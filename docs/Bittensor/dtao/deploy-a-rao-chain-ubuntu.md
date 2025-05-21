---
title: Deploy a Rao chain (Ubuntu)
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
In order to run a Bittensor-Rao chain, you must have the Subtensor code to run the chain, and Bittensor to interact with the chain.

# Install Subtensor

We'll install subtensor from Github, and then checkout the rao branch.

```
git clone git@github.com:opentensor/subtensor.git
cd subtensor
git checkout rao
git pull origin rao

```

## Setup the subtensor

### Install Rust

Using the \[Installationinstructions](<https://github.com/opentensor/subtensor/blob/main/docs/rust-setup.md>) for Ubuntu:

```
sudo apt update

sudo apt install -y git clang curl libssl-dev llvm libudev-dev
sudo apt install protobuf-compiler

curl --proto '=https' --tlsv1.2 -sSf <https://sh.rustup.rs> | sh

source ~/.cargo/env

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

<br />

```
cargo build
```

## Running ths subtensor

There are two scripts to run to start the subtensor:

```
bash  scripts/localnet.sh
#or
bash  scripts/raonet.sh
```

In practice - neither do exactly what you want to do.

- localnet: has a faucet - so you can add tao to your wallets, but it does not have the rao network
- localnet has fast-blocks turned on, but that seems to fail with raonet
- raonet has rao, but no faucet.

The fix is on line 28 & 34.

```
  : "${FEATURES:=" pow-faucet raonet runtime-benchmarks"}"
```

This has the faucet, the raonet, and no fastblocks.  Edit one or the other files (or create a new file).

# Install Bittensor

```
git clone git@github.com:opentensor/bittensor.git

#switch to rao branch
cd bittensor
git checkout rao
git pull origin rao

#create venv
sudo apt install python3.12-venv
python3 -m venv myenv
source myenv/bin/activate

#now install bittensor

python3 -m pip install -e bittensor/
pip install bittensor[torch]

```

test your bittensor install - we want to see (at least) version 7.4.0

```
btcli
/home/ubuntu/myenv/bin/btcli:4: DeprecationWarning: pkg_resources is deprecated as an API. See https://setuptools.pypa.io/en/latest/pkg_resources.html
  __import__('pkg_resources').require('bittensor==7.4.0rc1')
usage: btcli <command> <command args>

bittensor cli v7.4.0


```

You're now ready to create wallets and begin experimenting with Bittensor-Rao!