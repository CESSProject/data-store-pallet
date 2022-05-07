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

### Run Example

Launch node on the dev-env with:

```
# start
./target/release/node-template --dev
```

### Run in Docker

Install [Docker](https://docs.docker.com/get-docker/) first, and run the following command to start a node:

```
docker pull cesslab/data-store-pallet:0.1.2
docker run -itd --name data-store --network=host cesslab/data-store-pallet:0.1.2 && docker logs -f data-store
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
# Build project with the benchmarks enabled
cargo build --release --features runtime-benchmarks

./target/release/node-template benchmark --chain dev --pallet pallet_data_store --extrinsic "*" --repeat 50 --output=./pallets/data-store/src/weights.rs
```

## Module Documentation


* [Data Store](https://github.com/CESSProject/data-store-pallet/tree/main/pallets/data-store)
