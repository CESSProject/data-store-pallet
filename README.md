# data-store-pallet

[![Substrate version](https://img.shields.io/badge/Substrate-3.0.0-blue?logo=Parity%20Substrate)](https://substrate.dev/) [![GitHub license](https://img.shields.io/badge/license-GPL3%2FApache2-blue)](#LICENSE)

**The data-store-pallet is one of the components of the data storage service designed and implemented by CESS LAB based on Substrate. See [CIP-1](https://github.com/CESSProject/CIPs/blob/main/CIP-1.md) for its design scheme, and it has been included in [W3F Grants Program-ces_data_store](https://github.com/w3f/Grants-Program/blob/master/applications/ces_data_store.md).**

## Getting Started


### Install Guide

Follow [Setup](https://github.com/CESSProject/cess/tree/main/docs/setup.md) to guide you install the Substrate development.

### Build Node

The `cargo run` command will perform an initial build. Use the following command to build the node without launching it:

```
# Fetch the code
git clone https://github.com/CESSProject/data-store-pallet.git
cd data-store-pallet

# Build the node (The first build will be long (~30min))
cargo build --release
```

## Run The Node

After the node has finished compiling, you can follow these steps below to run it. 

### Generate Keys

If you already have keys for Substrate using the [SS58 address encoding format](https://docs.substrate.io/v3/advanced/ss58/), please see the next section.

Begin by compiling and installing the utility ([instructions and more info here](https://substrate.dev/docs/en/knowledgebase/integrate/subkey)). 

Generate a mnemonic (Secret phrase) and see the `sr25519` key and address associated with it.

```
# subkey command
subkey generate --scheme sr25519
```

Now see the `ed25519` key and address associated with the same mnemonic (secret phrase).

```
# subkey command
subkey inspect --scheme ed25519 "SECRET PHRASE YOU JUST GENERATED"
```

We recommend that you record the above outputs and keep mnemonic in safe.

### Run Testnet

Launch node on the cess-testnet with:

```
# start
./target/release/cess-node --base-path /tmp/cess --chain cess-testnet
```

Then you can add an account with:

```
# create key file
vim secretKey.txt

# add secret phrase for the node in the file
YOUR ACCOUNT'S SECRET PHRASE
```

```
# add key to node
./target/release/cess-node key insert --base-path /tmp/cess --chain cess-testnet --scheme Sr25519  --key-type babe --suri /root/secretKey.txt

./target/release/cess-node key insert --base-path /tmp/cess --chain cess-testnet --scheme Ed25519  --key-type gran --suri /root/secretKey.txt
```

Now you can launch node again:

```
# start
./target/release/cess-node --base-path /tmp/cess --chain cess-testnet
```

### Run in Docker

Install [Docker](https://docs.docker.com/get-docker/) first, and run the following command to start a node on the cess-testnet:

```
docker pull cesslab/data-store-pallet:0.1.0
docker run -itd --name data-store --network=host cesslab/data-store-pallet:0.1.0 && docker logs -f data-store
```

## Run Tests


CESS has Rust unit tests, and can be run locally.

```
# Run all the Rust unit tests
cargo test --release
```

## Run Tests with Benchmarks


CESS has Rust unit tests with benckmarks also. Currently, testing this feature in docker is not supported. Please execute belows after clone this repo.

```
# Run unit tests with benchmarks
cargo test -p pallet-sminer --features runtime-benchmarks
cargo test -p pallet-segment-book --features runtime-benchmarks
cargo test -p pallet-file-bank --features runtime-benchmarks
```

## Module Documentation


* [Files Bank](https://github.com/CESSProject/cess/tree/main/c-pallets/file-bank)
* [Segment Book](https://github.com/CESSProject/cess/tree/main/c-pallets/segment-book)
* [Sminer](https://github.com/CESSProject/cess/tree/main/c-pallets/sminer)

## Contribute

Please follow the contributions guidelines as outlined in [`docs/CONTRIBUTING.adoc`](https://github.com/CESSProject/cess/tree/main/docs/CONTRIBUTING.adoc). In all communications and contributions, this project follows the [Contributor Covenant Code of Conduct](https://github.com/paritytech/substrate/blob/master/docs/CODE_OF_CONDUCT.md).
