---
title: A Best Practices Guide for Safely Installing Software
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
As a User, installing software in a safe and verifiable manner isn’t always simple. This guide will provide you with a few pointers to install software without putting yourself at risk, or becoming susceptible to supply chain attacks.

## Use the source repository

It's important to install software in a safe and reliable manner. This reduces the chance of installing a malicious imitation, instead of a genuine product. Avoid pulling or installing software from third party platforms like [PyPI](https://pypi.org/) or [Docker Hub](https://hub.docker.com/), as the builds hosted on these platforms are not guaranteed to be derived from the same source code you will find on GitHub. Instead, rely on installing or building projects directly from the repo as this guarantees the build on your machine is built from source and hasn't been intercepted by a bad actor who may have published a malicious build.

## Verify signatures

If the developers are signing commits, check to see that the releases are signed. This is typically achieved by signing an [annotated tag](https://git-scm.com/book/en/v2/Git-Basics-Tagging). You can easily and visually check this in GitHub by looking for the verification on the commit. If the author has uploaded their GPG keys to GitHub, you can fetch them at `https://github.com/<username>.gpg`.

If you’ve cloned the repo, and have the authors public keys installed, you can check and verify a tag’s signature with `tag -v <tag>`.

<Image align="center" src="https://files.readme.io/a343466-octocat.png" />

## Installing packages

When installing packages from GitHub, either clone down and checkout a tagged version, or point the project's language's toolchain directly at the repo and install from there.

<br />

> 🚧
>
> Never, *ever* install a project or dependency without specifying a version. One of the easiest and most commonly performed attacks, is to push a patched version and hope users blindly auto update.
>
> Only upgrade when instructed to by the project developers or when they announce a new version, via official/verified channels, and only to the version they have announced.
>
> To checkout and switch branches in one command, use:

```bash
git checkout <url> -b <tag>
```

### Installing via a toolchain

While this example is for a Python project, it applies to most programming languages and their toolchains.

If a user wishes to install `bittensor` at `v7.3.0`, you can install it directly from GitHub using the following command:

```bash
$ pip install --upgrade git+https://github.com/opentensor/bittensor.git@v7.3.0
$ btcli --help
usage: btcli <command> <command args>

bittensor cli v7.3.0
```

This avoids relying on an external dependency like PyPI to install the project (where malicious code is most likely to reside), but pip will still resolve it's *dependencies* from PyPI. This is the responsibility of the developers to check that any project dependencies have not been compromised ([see below](https://www.notion.so/A-Best-Practices-Guide-for-Safely-Installing-Software-38766d1f178f4ef89490cb999d61ba16?pvs=21)).

### Installing via Docker

If you don't have the necessary toolchain for a given project, but you do have [Docker](https://docker.com/) installed and can locate a `Dockerfile` in the root of the project. You can build the project directly by pointing Docker at the repo. This avoids having to pull a container image from Docker Hub, which may be compromised.

```bash
docker build \
	https://github.com/opentensor/bittensor.git#v7.3.0 \
	-t opentensor/bittensor:v7.3.0
```

# What Developers can do to help

While it's not possible to produce *truly* reproducible builds in Python (it was never a requirement of pip, nor is Python built to do it), you can get close by relying on lock files to avoid supply chain attacks. If you notice the projects you are using don’t do some of the following things, request them via GitHub Issues.

## Manage project dependencies properly

To guarantee software is resistant to supply chain attacks, correctly manage and verify the project’s dependencies. If you are still relying on `pip` and `setuptools` you’re probably doing it wrong!

Consider an alternative like [Poetry](https://python-poetry.org/), to manage and build your projects.

Poetry will generate lock files (via `poetry lock`) or a pinned and hashed `requirements.txt` (via `poetry export`) that will lock down all of your project dependencies and any transient dependencies. Users can depend on the hashed `requirements.txt` to install the project’s dependencies without relying on Poetry.

This will stop any supply chain attacks that swap out packages for malicious variants, by guaranteeing the user is pulling and installing the exact modules, and verifying the contents haven't been modified.

If the project isn’t a library, commit the lock files with the repo so that those either making changes, or just installing, will get exactly the same versions of packages. When bumping the version of a given dependency, verify the new version is legitimate and uncompromised. We suggest bumping, checking, and committing one dependency at a time.

## Make deployment easy

If you provide a Docker container, make sure it’s entirely self sufficient. Invoking `docker build .` should work without any special environmental setup, this lets users remotely point to your repo with `docker build https://github.com/org/project.git#tag` and build directly from the repo.

If you want to provide other alternative images that are lighter, or are specialised for unique environments, append a suffix and let the user choose with `docker build -f Dockerfile.foo`. 

If publishing to Docker hub, make sure there isn’t a `latest` tag; Docker defaults to `latest` if no tag is requested. This can lead to supply chain attacks in the event of a compromised Docker hub account.

## Check for vulnerabilities

Use tools like [safety](https://pypi.org/project/safety/) and enable the [bandit](https://docs.astral.sh/ruff/rules/#flake8-bandit-s) linting rules inside of `ruff` to check that your packages don’t have known vulnerabilities and that you’re not introducing any yourself.

Automate these tools to run when commits are pushed to GitHub.

## Authenticate everything

Use 2 Factor Authentication to protect developer accounts, especially those with the ability to merge pull requests and publish new releases.

[Limit permissions](https://en.wikipedia.org/wiki/Principle_of_least_privilege) and access to repos to only what is necessary. This minimizes potential damage if an account is compromised. 

For enhanced verification generate a GPG key, or use a [HSM](https://www.yubico.com/us/product/yubikey-5-series/yubikey-5-nfc/). Upload your GPG keys to places like [GitHub](https://docs.github.com/en/authentication/managing-commit-signature-verification/adding-a-gpg-key-to-your-github-account) and [Keybase](https://keybase.io), and announce their availability over your official channels.

Sign commits and annotated tags to allow both GitHub  and your more security concerned users that you really did publish those commits.

If you release build artifacts, hash, sign, and provide the signatures alongside them too.

## Release Process

Ensure developers adhere to a formal branching scheme.

Proposed releases should be placed in a branch and a pull request set up to merge back into the `main/master` branch.

Set up the repo to only allow a quorum of specific developers to merge the PR.

Any small changes or hotfixes can then live in the release branch. Once approved, merge the branch into `main/master` and have whoever is responsible for releases, generate a commit with any version numbers inside the project bumped appropriately, the change log regenerated, and an annotated/signed tag.

Github will pick this up and generate a release which you can then see on the project’s releases page. 

Once the release is finalised, you may then deploy the release to any suitable environments by either merging `main/master` into a environmental branch, or force moving a lightweight tag that represents the environment. Your CI should spot the change and start the release process.

For libraries, once the merge is complete and the version ratified, use your CI to automatically use the project’s toolchain to build an artifact(s) and publish them to the appropriate repos.
