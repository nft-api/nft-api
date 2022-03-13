# `nft api`

> NFT API that returns resolved metadata and has all information about all NFT collections, users, transactions. Cross-Chain NFT API.

NFT API is a central part of any NFT dapp. Whether you build an NFT game, wallet, marketplace, analytics site, dashboard or something else based on NFTs you need to have a reliable NFT API that can help you get things such as: 
1) **NFT Metadata**
2) **NFT Ownership data**
3) **NFT Transfer data**
4) **NFT Prices**

See full [table of contents](https://github.com/nft-api/nft-api/blob/main/README.md#-table-of-contents).

If these features are required in your dapp - keep reading!

### `Chains supported`
The NFT API supports the following chains: 
1) Ethereum (ETH)
2) Binance Smart Chain (BSC) 
3) Polygon (MATIC)
4) Avalanche (AVAX) 
5) Fantom (FTM)
6) Testnets are fully supported.

This API is widely used in the web3 industry and is powering many prominent web3 projects.

![unnamed](https://user-images.githubusercontent.com/11097108/146640298-12da8642-8580-4906-a350-826f64970916.gif)

# ⭐️ `Star us`

If this NFT API helps you - please star this project, every star makes us very happy!

# 🚀 `Quick Start`

1) Sign up at [Moralis](https://moralis.io?utm_source=GitHub&utm_medium=NFT+API&utm_campaign=Moralis+Web3+Docs)
2) See example requests below
3) Read full docs: https://docs.moralis.io/moralis-server/web3-sdk

You can either call the API endpoints using REST HTTP requests or using the Moralis SDK. 
Both methods are demonstrated below for each endpoint. 

# 🤝 `Need help?`

If you need help with using the NFT API or have other questions - don't hesitate to write in our community forum and we will check asap. [Forum link](https://forum.moralis.io/). We are answering questions 24/7

# 🧭 Table of contents

- [`nft-api`](#nft-api)
- [🧭 Table of contents](#-table-of-contents)
- [🖼 NFT API Endpoints](#nft-api-endpoints)
  - [`SearchNFTs`](#searchnfts)
  - [`GetNFTs`](#getnfts)
  - [`GetNFTsForContract`](#getnftsforcontract)
  - [`GetNFTTransfers`](#getnfttransfers)
  - [`GetNFTTransfersByBlock`](#GetNFTTransfersByBlock)
  - [`GetAllTokenIds`](#getalltokenids)
  - [`GetContractNFTTransfers`](#getcontractnfttransfers)
  - [`GetNFTLowestPrice`](#getnftlowestprice)
  - [`GetNFTMetadata`](#getnftmetadata)
  - [`GetNFTOwners`](#getnftowners)
  - [`GetNFTTrades`](#getnfttrades)
  - [`GetNftTransfersFromToBlock`](#getnfttransfersfromtoblock)
  - [`GetTokenAdressTransfers`](#gettokenaddrestransfers)
  - [`GetTokenAllowance`](#gettokenallowance)
  - [`GetTokenIdMetadata`](#gettokenidmetadata)
  - [`GetTokenIdOwners`](#gettokenidowners)
  - [`GetWalletTokenIdTransfers`](#getwallettokenidtransfers)
- [Helpful Tools](#helpful-tools)

# 🖼 NFT API Endpoints

### `SearchNFTs`

NFT API gets the NFT data based on a metadata search.

**Options**:

- `q` _(required)_: The search string parameter
- `filter` _(required)_: What fields the search should match on. To look into the entire metadata set the value to global. To have a better response time you can look into a specific field like name. Available values : name; description; attributes; global; name,description; name,attributes; description,attributes; name,description,attributes
- `chain` _(optional)_: The blockchain to get data from. Valid values are listed on the intro page in the [`Supported Blockchains`](#supported-blockchains). Default value Eth.
- `format` _(optional)_: The format of the token id. Available values : decimal, hex. Default value : decimal.
- `offset` _(optional)_: offset.
- `limit` _(optional)_: limit.

#### Moralis SDK

```js
const options = { q: "Pancake", chain: "bsc", filter: "name" };
const NFTs = await Moralis.Web3API.token.searchNFTs(options);
```

#### REST

```bash
GET /nft/search
```

#### CURL

```bash
curl -X 'GET' \
  'https://deep-index.moralis.io/api/v2/nft/search?chain=eth&format=decimal&q={q}&filter=name' \
  -H 'accept: application/json' \
  -H 'X-API-Key: YOUR_API_KEY'
```

**Example return**

```json
[
  {
    "token_id": "124436",
    "token_address": "0x3afa102b264b5f79ce80fed29e0724f922ba57c7",
    "token_uri": "https://ipfs.moralis.io:2053/ipfs/QmVAD8v4s2SXF8FgjePqMdQ2GV5hE2isZnzxcrA36XcSDA/metadata.json",
    "metadata": "{\"name\":\"Pancake\",\"description\":\"The dessert series 1\",\"image\":\"ipfs://QmNQFXCZ6LGzvpMW9Q5PWbCrEnLknQrPwr2r8pbQAgzQ9A/4863BD6B-6C92-4B96-BF80-8020B2F7C3A5.jpeg\"}",
    "contract_type": "ERC721",
    "token_hash": "d03fe436e972bf9215d7bb8c64c4c556",
    "synced_at": null,
    "created_at": "2021-09-19T10:36:16.610Z"
  }
]
```

### `GetNFTs`

NFT API gets all NFTs from the current user or address. Supports both ERC721 and ERC1155. Returns an object with the number of NFT objects and the array of NFT objects.

**Options**:

- `address` _(required)_: A user address (i.e. 0x1a2b3x...).
- `chain` _(optional)_: The blockchain to get data from. Valid values are listed on the intro page in the [`Supported Blockchains`](#supported-blockchains). Default value Eth.
- `format` _(optional)_: The format of the token id. Available values : decimal, hex. Default value : decimal.
- `offset` _(optional)_: offset.
- `limit` _(optional)_: limit.

#### Moralis SDK

```js
onst options = { chain: 'matic', address: '0x...' };
const polygonNFTs = await Moralis.Web3API.account.getNFTs(options);
```

#### REST

```bash
GET /{address}/nft
```

#### CURL

```bash
curl -X 'GET' \
  'https://deep-index.moralis.io/api/v2/0xaddress/nft?chain=eth&format=decimal' \
  -H 'accept: application/json' \
  -H 'X-API-Key: YOUR_API_KEY'
```

**Example return**

```json
[
  {
    "token_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
    "token_id": "15",
    "contract_type": "ERC721",
    "owner_of": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
    "block_number": "88256",
    "block_number_minted": "88256",
    "token_uri": "string",
    "metadata": "string",
    "synced_at": "string",
    "amount": "1",
    "name": "CryptoKitties",
    "symbol": "RARI"
  }
]
```

### `GetNFTsForContract`

NFT API gets an object with the NFT count for the specified contract and an NFT array belonging to the given address for the specified contract.

**Options**:

- `address` _(required)_: The owner of a given token (i.e. 0x1a2b3x...).
- `token_address` _(required)_: Address of the contract.
- `chain` _(optional)_: The blockchain to get data from. Valid values are listed on the intro page in the [`Supported Blockchains`](#supported-blockchains). Default value Eth.
- `format` _(optional)_: The format of the token id. Available values : decimal, hex. Default value : decimal.
- `offset` _(optional)_: offset.
- `limit` _(optional)_: limit.

#### Moralis SDK

```js
const options = { chain: "matic", address: "0x...", token_address: "0x..." };
const polygonNFTs = await Moralis.Web3API.account.getNFTsForContract(options);
```

#### REST

```bash
GET /{address}/nft/{token_address}
```

#### CURL

```bash
curl -X 'GET' \
  'https://deep-index.moralis.io/api/v2/{address}/nft/{token_address}?chain=eth&format=decimal' \
  -H 'accept: application/json' \
  -H 'X-API-Key: YOUR_API_KEY'
```

**Example return**

```json
{
  "status": "SYNCING",
  "total": 2000,
  "page": 2,
  "page_size": 100,
  "result": [
    {
      "token_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "token_id": "15",
      "contract_type": "ERC721",
      "owner_of": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "block_number": "88256",
      "block_number_minted": "88256",
      "token_uri": "string",
      "metadata": "string",
      "synced_at": "string",
      "amount": "1",
      "name": "CryptoKitties",
      "symbol": "RARI"
    }
  ]
}
```

### `GetNFTTransfers`

NFT API gets the NFT transfers. Returns an object with the number of NFT transfers and the array of NFT transfers.

**Options**:

- `address` _(required)_: A user address (i.e. 0x1a2b3x...).
- `chain` _(optional)_: The blockchain to get data from. Valid values are listed on the intro page in the [`Supported Blockchains`](#supported-blockchains). Default value Eth.
- `format` _(optional)_: The format of the token id. Available values : decimal, hex. Default value : decimal.
- `offset` _(optional)_: offset.
- `limit` _(optional)_: limit.
- `direction` _(optional)_: The transfer direction. Available values : both, to, from . Default value : both.
- `order` _(optional)_: The field(s) to order on and if it should be ordered in ascending or descending order.

#### Moralis SDK

```js
const options = { chain: "bsc", address: "0x...", limit: "10" };
const transfersNFT = await Moralis.Web3API.account.getNFTTransfers(options);
```

#### REST

```bash
GET /{address}/nft/transfers
```

#### CURL

```bash
curl -X 'GET' \
  'https://deep-index.moralis.io/api/v2/nft/{address}/transfers?chain=eth&format=decimal' \
  -H 'accept: application/json' \
  -H 'X-API-Key: YOUR_API_KEY'
```

**Example return**

```json
{
  "total": 2000,
  "page": 2,
  "page_size": 100,
  "result": [
    {
      "token_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "token_id": "15",
      "from_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "to_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "value": "1000000000000000",
      "amount": "1",
      "contract_type": "ERC721",
      "block_number": "88256",
      "block_timestamp": "2021-06-04T16:00:15",
      "block_hash": "string",
      "transaction_hash": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "transaction_type": "string",
      "transaction_index": "string",
      "log_index": 0,
      "operator": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e"
    }
  ],
  "block_exists": true
}
```

### `GetNFTTransfersByBlock`

NFT API gets NFT transfers by block number or block hash

**Options**:

- `block_number_or_hash` _(required)_: The block hash or block number.
- `chain` _(optional)_: The blockchain to get data from. Valid values are listed on the intro page in the [`Supported Blockchains`](#supported-blockchains). Default value Eth.
- `format` _(optional)_: The format of the token id. Available values : decimal, hex. Default value : decimal.
- `offset` _(optional)_: offset.
- `limit` _(optional)_: limit.

#### Moralis SDK

```js
const options = { chain: "bsc", block_number_or_hash: "11284830" };
const NFTTransfers = await Moralis.Web3API.native.getNFTTransfersByBlock(options);
```

#### REST

```bash
GET /block/{block_number_or_hash}/nft/transfers
```

#### CURL

```bash
curl -X 'GET' \
  'https://deep-index.moralis.io/api/v2/block/{block_number_or_hash}/nft/transfers?chain=eth&limit=500' \
  -H 'accept: application/json' \
  -H 'X-API-Key: YOUR_API_KEY'
```

**Example return**

```json
{
  "total": 2000,
  "page": 2,
  "page_size": 100,
  "result": [
    {
      "token_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "token_id": "15",
      "from_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "to_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "value": "1000000000000000",
      "amount": "1",
      "contract_type": "ERC721",
      "block_number": "88256",
      "block_timestamp": "2021-06-04T16:00:15",
      "block_hash": "string",
      "transaction_hash": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "transaction_type": "string",
      "transaction_index": "string",
      "log_index": 0,
      "operator": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e"
    }
  ],
  "block_exists": true
}
```

### `GetAllTokenIds`

NFT API gets an object with a number of NFTs and an array with NFT metadata(where available) for a given token contract address.

**Options**:

- `address` _(required)_: The address of the token contract.
- `chain` _(optional)_: The blockchain to get data from. Valid values are listed on the intro page in the [`Supported Blockchains`](#supported-blockchains). Default value Eth.
- `format` _(optional)_: The format of the token id. Available values : decimal, hex. Default value : decimal.
- `offset` _(optional)_: offset.
- `limit` _(optional)_: limit.

#### Moralis SDK

```js
const options = { address: "0xd...07", chain: "bsc" };
const NFTs = await Moralis.Web3API.token.getAllTokenIds(options);
```

#### REST

```bash
GET /nft/{address}
```

#### CURL

```bash
curl -X 'GET' \
  'https://deep-index.moralis.io/api/v2/nft/{address}?chain=eth&format=decimal' \
  -H 'accept: application/json' \
  -H 'X-API-Key: YOUR_API_KEY'
```

**Example return**

```json
{
  "total": 2000,
  "page": 2,
  "page_size": 100,
  "result": [
    {
      "token_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "token_id": "15",
      "contract_type": "ERC721",
      "token_uri": "string",
      "metadata": "string",
      "synced_at": "string",
      "amount": "1",
      "name": "CryptoKitties",
      "symbol": "RARI"
    }
  ]
}
```

### `GetContractNFTTransfers`

NFT API gets an object with number of NFT transfers and an array with NFT transfers for a given token contract address.

**Options**:

- `address` _(required)_: The address of the token contract.
- `chain` _(optional)_: The blockchain to get data from. Valid values are listed on the intro page in the [`Supported Blockchains`](#supported-blockchains). Default value Eth.
- `format` _(optional)_: The format of the token id. Available values : decimal, hex. Default value : decimal.
- `offset` _(optional)_: offset.
- `limit` _(optional)_: limit.

#### Moralis SDK

```js
const options = { address: "0xd...07", chain: "bsc" };
const nftTransfers = await Moralis.Web3API.token.getContractNFTTransfers(options);
```

#### REST

```bash
GET ​/nft​/{address}​/transfers
```

#### CURL

```bash
curl -X 'GET' \
  'https://deep-index.moralis.io/api/v2/nft/{address}/transfers?chain=eth&format=decimal' \
  -H 'accept: application/json' \
  -H 'X-API-Key: YOUR_API_KEY'
```

**Example return**

```json
{
  "total": 2000,
  "page": 2,
  "page_size": 100,
  "result": [
    {
      "token_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "token_id": "15",
      "contract_type": "ERC721",
      "token_uri": "string",
      "metadata": "string",
      "synced_at": "string",
      "amount": "1",
      "name": "CryptoKitties",
      "symbol": "RARI"
    }
  ]
}
```

### `GetNFTLowestPrice`

NFT API gets an object with the lowest price found for a NFT token contract for the last x days (only trades paid in ETH)

**Options**:

- `address` _(required)_: The address of the token contract.
- `days` _(optional)_: The number of days to look back to find the lowest price If not provided 7 days will be the default.
- `marketplace` _(optional)_: Marketplace from where to get the trades (only opensea is supported at the moment).
- `chain` _(optional)_: The blockchain to get data from. Valid values are listed on the intro page in the [`Supported Blockchains`](#supported-blockchains). Default value Eth.

#### Moralis SDK

```js
const options = { address: "0xd...07", days: "3" };
const NFTLowestPrice = await Moralis.Web3API.token.getNFTLowestPrice(options);
```

#### REST

```bash
GET ​/nft​/{address}​/lowestprice
```

#### CURL

```bash
curl -X 'GET' \
  'https://deep-index.moralis.io/api/v2/nft/{address}​/lowestprice?chain=eth&marketplace=opensea' \
  -H 'accept: application/json' \
  -H 'X-API-Key: YOUR_API_KEY'
```

**Example return**

```json
{
  "transaction_hash": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
  "transaction_index": "string",
  "token_ids": ["15", "54"],
  "seller_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
  "buyer_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
  "marketplace_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
  "price": "1000000000000000",
  "block_timestamp": "2021-06-04T16:00:15",
  "block_number": "13680123",
  "block_hash": "0x4a7c916ca4a970358b9df90051008f729685ff05e9724a9dddba32630c37cb96"
}
```

### `GetNFTMetadata`

NFT API gets the contract level metadata (name, symbol, base token uri) for the given contract

**Options**:

- `address` _(required)_: The address of the token contract.
- `chain` _(optional)_: The blockchain to get data from. Valid values are listed on the intro page in the [`Supported Blockchains`](#supported-blockchains). Default value Eth.
- `format` _(optional)_: The format of the token id. Available values : decimal, hex. Default value : decimal.
- `offset` _(optional)_: offset.
- `limit` _(optional)_: limit.

#### Moralis SDK

```js
const options = { address: "0xd...07", chain: "bsc" };
const metaData = await Moralis.Web3API.token.getNFTMetadata(options);
```

#### REST

```bash
GET ​/nft​/{address}​/metadata
```

#### CURL

```bash
curl -X 'GET' \
  'https://deep-index.moralis.io/api/v2/nft/{address}/metadata?chain=eth' \
  -H 'accept: application/json' \
  -H 'X-API-Key: YOUR_API_KEY'
```

**Example return**

```json
{
  "token_address": "0x2d30ca6f024dbc1307ac8a1a44ca27de6f797ec22ef20627a1307243b0ab7d09",
  "name": "KryptoKitties",
  "abi": "string",
  "supports_token_uri": 0,
  "synced_at": "string",
  "symbol": "RARI",
  "contract_type": "ERC721"
}
```

### `GetNFTOwners`

NFT API gets an object with a number of NFT owners and an array with NFT metadata (name, symbol) for a given token contract address .

**Options**:

- `address` _(required)_: The address of the token contract.
- `chain` _(optional)_: The blockchain to get data from. Valid values are listed on the intro page in the [`Supported Blockchains`](#supported-blockchains). Default value Eth.
- `format` _(optional)_: The format of the token id. Available values : decimal, hex. Default value : decimal.
- `offset` _(optional)_: offset.
- `limit` _(optional)_: limit.

#### Moralis SDK

```js
const options = { address: "0xd...07", chain: "bsc" };
const nftOwners = await Moralis.Web3API.token.getNFTOwners(options);
```

#### REST

```bash
GET ​/nft​/{address}​/owners
```

#### CURL

```bash
curl -X 'GET' \
  'https://deep-index.moralis.io/api/v2/nft/{address}/owners?chain=eth&format=decimal' \
  -H 'accept: application/json' \
  -H 'X-API-Key: YOUR_API_KEY'
```

**Example return**

```json
{
  "status": "SYNCING",
  "total": 2000,
  "page": 2,
  "page_size": 100,
  "result": [
    {
      "token_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "token_id": "15",
      "contract_type": "ERC721",
      "owner_of": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "block_number": "88256",
      "block_number_minted": "88256",
      "token_uri": "string",
      "metadata": "string",
      "synced_at": "string",
      "amount": "1",
      "name": "CryptoKitties",
      "symbol": "RARI"
    }
  ]
}
```

### `GetNFTTrades`

NFT API gets

**Options**:

- `address` _(required)_: The address of the token contract.
- `marketplace` _(optional)_: Marketplace from where to get the trades (only opensea is supported at the moment).
- `from_date` _(optional)_: The date from where to get the trades(any format that is accepted by momentjs). Provide the param 'from_block' or 'from_date' If 'from_date' and 'from_block' are provided, 'from_block' will be used.
- `to_date` _(optional)_: Get the trades to this date (any format that is accepted by momentjs). Provide the param 'to_block' or 'to_date' If 'to_date' and 'to_block' are provided, 'to_block' will be used.
- `from_block` _(optional)_: The minimum block number from where to get the tradesProvide the param 'from_block' or 'from_date' If 'from_date' and 'from_block' are provided, 'from_block' will be used.
- `to_block` _(optional)_: The maximum block number from where to get the trades. Provide the param 'to_block' or 'to_date' If 'to_date' and 'to_block' are provided, 'to_block' will be used.
- `chain` _(optional)_: The blockchain to get data from. Valid values are listed on the intro page in the [`Supported Blockchains`](#supported-blockchains). Default value Eth.
- `format` _(optional)_: The format of the token id. Available values : decimal, hex. Default value : decimal.
- `offset` _(optional)_: offset.
- `limit` _(optional)_: limit.

#### Moralis SDK

```js
const options = { address: "0xd...07", limit: "10", chain: "bsc" };
const NFTTrades = await Moralis.Web3API.token.getNFTTrades(options);
```

#### REST

```bash
GET ​/nft​/{address}​/trades
```

#### CURL

```bash
curl -X 'GET' \
  'https://deep-index.moralis.io/api/v2/nft/{address}​/trades?chain=eth&marketplace=opensea' \
  -H 'accept: application/json' \
  -H 'X-API-Key: YOUR_API_KEY'
```

**Example return**

```json
{
  "total": 2000,
  "page": 2,
  "page_size": 100,
  "result": [
    {
      "transaction_hash": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "transaction_index": "string",
      "token_ids": ["15", "54"],
      "seller_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "buyer_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "marketplace_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "price": "1000000000000000",
      "block_timestamp": "2021-06-04T16:00:15",
      "block_number": "13680123",
      "block_hash": "0x4a7c916ca4a970358b9df90051008f729685ff05e9724a9dddba32630c37cb96"
    }
  ]
}
```

### `GetTokenIdMetadata`

NFT API gets data, including metadata (where available), for the given token id of the given contract address.

**Options**:

- `address` _(required)_: The address of the token contract.
- `token_id` _(required)_: The id of the token.
- `chain` _(optional)_: The blockchain to get data from. Valid values are listed on the intro page in the [`Supported Blockchains`](#supported-blockchains). Default value Eth.
- `format` _(optional)_: The format of the token id. Available values : decimal, hex. Default value : decimal.
- `offset` _(optional)_: offset.
- `limit` _(optional)_: limit.

#### Moralis SDK

```js
const options = { address: "0xd...07", token_id: "1", chain: "bsc" };
const tokenIdMetadata = await Moralis.Web3API.token.getTokenIdMetadata(options);
```

#### REST

```bash
GET ​/nft​/{address}​/{token_id}
```

#### CURL

```bash
curl -X 'GET' \
  'https://deep-index.moralis.io/api/v2/nft/{address}​/{token_id}?chain=eth&format=decimal' \
  -H 'accept: application/json' \
  -H 'X-API-Key: YOUR_API_KEY'
```

**Example return**

```json
{
  "token_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
  "token_id": "15",
  "contract_type": "ERC721",
  "token_uri": "string",
  "metadata": "string",
  "synced_at": "string",
  "amount": "1",
  "name": "CryptoKitties",
  "symbol": "RARI"
}
```

### `GetTokenIdOwners`

NFT API gets

**Options**:

- `address` _(required)_: The address of the token contract.
- `chain` _(optional)_: The blockchain to get data from. Valid values are listed on the intro page in the [`Supported Blockchains`](#supported-blockchains). Default value Eth.
- `format` _(optional)_: The format of the token id. Available values : decimal, hex. Default value : decimal.
- `offset` _(optional)_: offset.
- `limit` _(optional)_: limit.

#### Moralis SDK

```js
const options = { address: "0xd...07", token_id: "1", chain: "bsc" };
const tokenIdOwners = await Moralis.Web3API.token.getTokenIdOwners(options);
```

#### REST

```bash
GET ​/nft​/{address}​/{token_id}​/owners
```

#### CURL

```bash
curl -X 'GET' \
  'https://deep-index.moralis.io/api/v2/nft/{address}/{token_id}/owners?chain=eth&format=decimal' \
  -H 'accept: application/json' \
  -H 'X-API-Key: YOUR_API_KEY'
```

**Example return**

```json
{
  "status": "SYNCING",
  "total": 2000,
  "page": 2,
  "page_size": 100,
  "result": [
    {
      "token_address": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "token_id": "15",
      "contract_type": "ERC721",
      "owner_of": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "block_number": "88256",
      "block_number_minted": "88256",
      "token_uri": "string",
      "metadata": "string",
      "synced_at": "string",
      "amount": "1",
      "name": "CryptoKitties",
      "symbol": "RARI"
    }
  ]
}
```
