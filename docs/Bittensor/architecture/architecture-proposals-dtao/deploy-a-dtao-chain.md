---
title: Deploy a test Chain rao or local (Mac)
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
# Deploy the Subtensor

The Bittensor subtensor code can be found on GitHub: <https://github.com/opentensor/subtensor/>

Clone this repository locally, and switch to the dynamic branch:

```shell
git clone git@github.com:opentensor/subtensor.git
cd subtensor
git fetch origin rao
git checkout rao
```

Now we'll get the Subtensor up and running..  For installation you need rosetta.  We'll also use Homebrew to install OpenSSL. (these instructions are from the GitHub Readme - so if you are in a different OS, check that out and work through the steps).

```shell
softwareupdate --install-rosetta

# Install Homebrew if necessary https://brew.sh/
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
# Make sure Homebrew is up-to-date, install openssl
brew update
brew install openssl
```

Now we need to install Rust.  Again there's a link on the GitHub repo for those of you on different OS.

```shell
# Install
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
# Configure
source ~/.cargo/env

#rust configuration
rustup default stable
rustup update
rustup update nightly
rustup target add wasm32-unknown-unknown --toolchain nightly
```

<br />

## Config changes

1. Update the `scripts/localnet.sh` on line 34.  In testing, raonet does not work with fastblocks. (this may change before launch).  We want to have the pow-faucet to distribute tao to our wallets.

```
  : "${FEATURES:=" pow-faucet raonet runtime-benchmarks"}"
```

2. Increase the faucet amount (if desired).  Add a few more zeros to this value to ensure that you have enough test tao.`https://github.com/opentensor/subtensor/blob/58c1f51cc9f0716545fbf99c10c8d761d19dd472/pallets/subtensor/src/subnets/registration.rs#L397`

```
let balance_to_add: u64 = 1_000_000_000_000;
```

# build

OK - everything is installed for the subtensor, so we can build and run it:

```shell
cargo build
sh scripts/localnet.sh
```

Your subtensor is now running.

> 📘 Calling the subtensor
> 
> When working with your local chain, add the 
> 
> `--subtensor.network local` or `--subtensor.network ws://127.0.0.1:9946` 
> 
> parameters to your btcli commands.  They can be used interchanably for the subtensor running on your computer.

# Install Bittensor

The Bittensor Github repo can be found in the same organization on Github: <https://github.com/opentensor/bittensor>

We're going to install it, and again use the dynamic branch:

```shell
git clone git@github.com:opentensor/bittensor.git
cd bittensor
git fetch origin rao
git checkout rao
python3 -m pip install -e .
cd ..
python3 -m pip install -e bittensor/
```

Any time there is an update to the subtensor or Bittensor - you'll need to pull from Github and rebuild and install the dependencies again.

You now have a running Bittensor-Rao subtensor, and are ready to start creating!