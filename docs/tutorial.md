# Usage tutorial of data store pallet

this tutorial explains how a user can spin up one of our Substrate nodes and send test transactions, which will show how the new functionality works.

## Introduction

Data store pallet realizes the features of recording and management of stored data. It implements functions related to meta-data such as _store_, _retrieve_, _replace_, _delete_ and _edit_, _query_. This is a regular-spec Pallet, and any Substrate Node can easily import it and get the above features. Generally speaking, if you want to get a complete data storage service, in addition to integrating this module, you also need to use the **Custom-built Storage Sidecar**, which is under development. 

# ![Figure 1: Typical example process](https://raw.githubusercontent.com/CESSProject/W3F-illustration/main/substrate-builder-program/10.svg)

As shown in Figure 1 above, the **data store pallet** is responsible for managing the meta information of the stored data, while the source data will be stored on CESS via the **Custom-built Storage Sidecar**.

Now let's see how the data store pallet works.

## Demonstration of function Interface

### store
Upload meta-info of stored file on chain.

1. Call _store_ function to record meta-info of file on chain with inputing 1) fileId, 2) fileName, 3) fileSize, 4) keywords.
# ![Figure 2](https://raw.githubusercontent.com/CESSProject/W3F-illustration/main/data-store-pallet/docs/data-store-01.png)

2. Check if the above info on-chain.
# ![Figure 3](https://raw.githubusercontent.com/CESSProject/W3F-illustration/main/data-store-pallet/docs/data-store-02.png)

### retrieve
Check if the caller has permission to get the specified file.

1. Call _retrieve_ function to get meta-info of target file. Only the data owner has access to it.
# ![Figure 4](https://raw.githubusercontent.com/CESSProject/W3F-illustration/main/data-store-pallet/docs/data-store-03.png)

2. It gets successful when I call as the data owner.
# ![Figure 5](https://raw.githubusercontent.com/CESSProject/W3F-illustration/main/data-store-pallet/docs/data-store-04.png)

### edit
Support to modify meta-info of the owner's specified file.

1. Call _edit_ function to modify meta-info of the owner's specified file with inputing 1) fileId, 2) newFileName, 3) newKeywords.
# ![Figure 6](https://raw.githubusercontent.com/CESSProject/W3F-illustration/main/data-store-pallet/docs/data-store-05.png)

2. See if the updated info on-chain.
# ![Figure 7](https://raw.githubusercontent.com/CESSProject/W3F-illustration/main/data-store-pallet/docs/data-store-06.png)

### replace
Upload and replace old meta-info with new's of stored file on chain.

1. Call _replace_ function to replace meta-info of the owner's specified file with inputing 1) oldFileId, 2) newFileId, 3) fileName, 4) fileSize, 5) keywords.
# ![Figure 8](https://raw.githubusercontent.com/CESSProject/W3F-illustration/main/data-store-pallet/docs/data-store-07.png)

2. Check if the replacement is successful.
# ![Figure 9](https://raw.githubusercontent.com/CESSProject/W3F-illustration/main/data-store-pallet/docs/data-store-08.png)

### query
Query the meta-info of file by fileId and owner.
# ![Figure 10](https://raw.githubusercontent.com/CESSProject/W3F-illustration/main/data-store-pallet/docs/data-store-11.png)

### delete
Delete the meta-info of the specified file, and the caller must be the owner of the file.

1. Call _delete_ function to delete the targeted file by fileId.
# ![Figure 11](https://raw.githubusercontent.com/CESSProject/W3F-illustration/main/data-store-pallet/docs/data-store-09.png)

2. Removed all meta information.
# ![Figure 12](https://raw.githubusercontent.com/CESSProject/W3F-illustration/main/data-store-pallet/docs/data-store-10.png)

