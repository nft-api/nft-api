# Quick Start to Moralis NFT API

1. [Get an API key](https://docs.moralis.io/reference/getting-the-api-key?utm_source=GitHub&utm_medium=NFT+API&utm_campaign=Moralis+Web3+Docs)
2. Explore the [documentation guides](https://docs.moralis.io/web3-data-api/evm/nft-api)
3. Explore the [full list of endpoints](https://github.com/nft-api/nft-api/blob/main/README.md#-list-of-nft-api-endpoints)
4. Explore [API reference](https://docs.moralis.io/web3-data-api/evm/reference#nft-api)

## Boost Your dApp with the Moralis NFT API

> NFT API that returns resolved metadata and has all information about all NFT collections, users, transactions, and Cross-Chain NFT API.

The Moralis NFT API is your ultimate ally for creating a top-tier NFT dApp. Whether you are venturing into the world of NFT gaming, building a secure NFT wallet, launching a bustling NFT marketplace, crafting insightful NFT analytics tools, developing a dazzling NFT dashboard, or exploring any NFT-based endeavor, you need the robust Moralis NFT API in your toolkit!

![unnamed](https://user-images.githubusercontent.com/11097108/146640298-12da8642-8580-4906-a350-826f64970916.gif)

## Explore the Power of the NFT API

In the NFT ecosystem, data reigns supreme, and the Moralis NFT API is your gateway to success. Unlock a world of features to take your dApp to the next level:

1. **NFT Metadata**: Access stunning NFT metadata effortlessly to showcase your digital art, collectibles, and assets.

2. **NFT Ownership Data**: Dive into ownership records to personalize the NFT experience and engage your users.

3. **NFT Transfer Data**: Seamlessly track NFT transfers and transactions, ensuring a smooth user journey.

4. **NFT Price Insights**: Stay ahead of the curve with real-time NFT price data and market trends, providing users with valuable financial information.

If these powerful features are essential for your dApp's success (and they definitely are!), read on to embark on a remarkable NFT journey with Moralis!

## List of NFT API Endpoints

The following table contains a list of all NFT API endpoints:

| No. | Method      | Description                                     | URL                                                                       | API Reference                                                                                             |
|-----|--------------------------|--------------------------------------------------------------|---------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
| 1   | `getMultipleNFTs`        | Get multiple NFTs | [https://deep-index.moralis.io/api/v2.2/nft/getMultipleNFTs](https://deep-index.moralis.io/api/v2.2/nft/getMultipleNFTs) | [Documentation for getMultipleNFTs](https://docs.moralis.io/web3-data-api/evm/reference/get-multiple-nfts?tokens=[]&normalizeMetadata=false&media_items=true&chain=eth) |
| 2   | `getWalletNFTs`           | Get NFTs by wallet | [https://deep-index.moralis.io/api/v2.2/:address/nft](https://deep-index.moralis.io/api/v2.2/:address/nft)                     | [Documentation for getWalletNFTs](https://docs.moralis.io/web3-data-api/evm/reference/get-wallet-nfts?address=0x1f9090aaE28b8a3dCeaDf281B0F12828e676c326&chain=eth&format=decimal&token_addresses=[]&media_items=false)   |
| 3   | `getContractNFTs`         | Get NFTs by contract | [https://deep-index.moralis.io/api/v2.2/nft/:address](https://deep-index.moralis.io/api/v2.2/nft/:address)                   | [Documentation for getContractNFTs](https://docs.moralis.io/web3-data-api/evm/reference/get-contract-nfts?address=0xb47e3cd837dDF8e4c57F05d70Ab865de6e193BBB&chain=eth&format=decimal) |
| 4   | `reSyncMetadata`           | Resync the metadata for an NFT | [https://deep-index.moralis.io/api/v2.2/nft/:address/:token_id/metadata/resync](https://deep-index.moralis.io/api/v2.2/nft/:address/:token_id/metadata/resync) | [Documentation for reSyncMetadata](https://docs.moralis.io/web3-data-api/evm/reference/resync-metadata?address=0xb47e3cd837dDF8e4c57F05d70Ab865de6e193BBB&token_id=1&chain=eth&flag=uri&mode=async)   |
| 5   | `getNFTMetadata`           | Get NFT data | [https://deep-index.moralis.io/api/v2.2/nft/:address/:token_id](https://deep-index.moralis.io/api/v2.2/nft/:address/:token_id) | [Documentation for getNFTMetadata](https://docs.moralis.io/web3-data-api/evm/reference/get-nft-metadata?address=0xb47e3cd837dDF8e4c57F05d70Ab865de6e193BBB&token_id=1&chain=eth&format=decimal&normalizeMetadata=true&media_items=false)   |
| 6   | `getWalletNFTTransfers`    | Get NFT transfers by wallet | [https://deep-index.moralis.io/api/v2.2/:address/nft/transfers](https://deep-index.moralis.io/api/v2.2/:address/nft/transfers) | [Documentation for getWalletNFTTransfers](https://docs.moralis.io/web3-data-api/evm/reference/get-wallet-nft-transfers?address=0x1f9090aaE28b8a3dCeaDf281B0F12828e676c326&chain=eth&format=decimal) |
| 7   | `getNFTContractTransfers`  | Get NFT transfers by contract | [https://deep-index.moralis.io/api/v2.2/nft/:address/transfers](https://deep-index.moralis.io/api/v2.2/nft/:address/transfers) | [Documentation for getNFTContractTransfers](https://docs.moralis.io/web3-data-api/evm/reference/get-nft-contract-transfers?address=0xb47e3cd837dDF8e4c57F05d70Ab865de6e193BBB&chain=eth&format=decimal) |
| 8   | `getNFTTransfersFromToBlock` | Get transfers of NFTs from a block number to a block number | [https://deep-index.moralis.io/api/v2.2/nft/transfers](https://deep-index.moralis.io/api/v2.2/nft/transfers) | [Documentation for getNFTTransfersFromToBlock](https://docs.moralis.io/web3-data-api/evm/reference/get-nft-transfers-from-to-block?chain=eth&format=decimal)   |
| 9   | `getNFTTransfersByBlock`   | Get transfers of NFTs given a block number or block hash  | [https://deep-index.moralis.io/api/v2.2/block/:block_number_or_hash/nft/transfers](https://deep-index.moralis.io/api/v2.2/block/:block_number_or_hash/nft/transfers) | [Documentation for getNFTTransfersByBlock](https://docs.moralis.io/web3-data-api/evm/reference/get-nft-transfers-by-block?block_number_or_hash=15846571&chain=eth)   |
| 10  | `getNFTTransfers`          | Get transfers of an NFT given a contract address and token ID | [https://deep-index.moralis.io/api/v2.2/nft/:address/:token_id/transfers](https://deep-index.moralis.io/api/v2.2/nft/:address/:token_id/transfers) | [Documentation for getNFTTransfers](https://docs.moralis.io/web3-data-api/evm/reference/get-nft-transfers?address=0xb47e3cd837dDF8e4c57F05d70Ab865de6e193BBB&token_id=1&chain=eth&format=decimal)   |
| 11  | `getWalletNFTCollections`  | Get NFT collections owned by a given wallet address        | [https://deep-index.moralis.io/api/v2.2/:address/nft/collections](https://deep-index.moralis.io/api/v2.2/:address/nft/collections) | [Documentation for getWalletNFTCollections](https://docs.moralis.io/web3-data-api/evm/reference/get-wallet-nft-collections?address=0x1f9090aaE28b8a3dCeaDf281B0F12828e676c326&chain=eth)   |
| 12  | `getNFTContractMetadata`   | Get the collection/contract level metadata for a given contract | [https://deep-index.moralis.io/api/v2.2/nft/:address/metadata](https://deep-index.moralis.io/api/v2.2/nft/:address/metadata) | [Documentation for getNFTContractMetadata](https://docs.moralis.io/web3-data-api/evm/reference/get-nft-contract-metadata?address=0xb47e3cd837dDF8e4c57F05d70Ab865de6e193BBB&chain=eth)   |
| 13  | `syncNFTContract`          | Initiates a sync of a previously non-synced contract     | [https://deep-index.moralis.io/api/v2.2/nft/:address/sync](https://deep-index.moralis.io/api/v2.2/nft/:address/sync)       | [Documentation for syncNFTContract](https://docs.moralis.io/web3-data-api/evm/reference/sync-nft-contract?address=0x60E4d786628Fea6478F785A6d7e704777c86a7c6&chain=eth) |
| 14  | `getNFTOwners`            | Get owners of NFTs for a given contract                   | [https://deep-index.moralis.io/api/v2.2/nft/:address/owners](https://deep-index.moralis.io/api/v2.2/nft/:address/owners) | [Documentation for getNFTOwners](https://docs.moralis.io/web3-data-api/evm/reference/get-nft-owners?address=0xb47e3cd837dDF8e4c57F05d70Ab865de6e193BBB&chain=eth&format=decimal) |
| 15  | `getNFTTokenIdOwners`      | Get owners of a specific NFT given the contract address and token ID. | [https://deep-index.moralis.io/api/v2.2/nft/:address/:token_id/owners](https://deep-index.moralis.io/api/v2.2/nft/:address/:token_id/owners) | [Documentation for getNFTTokenIdOwners](https://docs.moralis.io/web3-data-api/evm/reference/get-nft-token-id-owners?address=0xb47e3cd837dDF8e4c57F05d70Ab865de6e193BBB&token_id=1&chain=eth&format=decimal)   |
| 16  | `getNFTTrades`             | Get trades of NFTs for a given contract and marketplace   | [https://deep-index.moralis.io/api/v2.2/nft/:address/trades](https://deep-index.moralis.io/api/v2.2/nft/:address/trades) | [Documentation for getNFTTrades](https://docs.moralis.io/web3-data-api/evm/reference/get-nft-trades?address=0xb47e3cd837dDF8e4c57F05d70Ab865de6e193BBB&chain=eth&marketplace=opensea)   |
| 17  | `getNFTLowestPrice`        | Get the lowest executed price for an NFT contract for the last x days | [https://deep-index.moralis.io/api/v2.2/nft/:address/lowestprice](https://deep-index.moralis.io/api/v2.2/nft/:address/lowestprice) | [Documentation for getNFTLowestPrice](https://docs.moralis.io/web3-data-api/evm/reference/get-nft-lowest-price?address=0xBC4CA0EdA7647A8aB7C2061c2E118A18a936f13D&chain=eth&marketplace=opensea)   |
| 18  | `getNFTCollectionStats`     | Get the stats for a NFT collection address              | [https://deep-index.moralis.io/api/v2.2/nft/:address/stats](https://deep-index.moralis.io/api/v2.2/nft/:address/stats) | [Documentation for getNFTCollectionStats](https://docs.moralis.io/web3-data-api/evm/reference/get-nft-collection-stats?chain=eth)   |
| 19  | `getNFTTokenStats`          | Get the stats for a NFT token                       | [https://deep-index.moralis.io/api/v2.2/nft/:address/:token_id/stats](https://deep-index.moralis.io/api/v2.2/nft/:address/:token_id/stats) | [Documentation for getNFTTokenStats](https://docs.moralis.io/web3-data-api/evm/reference/get-nft-token-stats?address=0xbc4ca0eda7647a8ab7c2061c2e118a18a936f13d&token_id=1&chain=eth)   |

## List of Supported Chains

Please check the article [Supported Chains Overview](https://docs.moralis.io/supported-chains).

## ⭐️ Star us

If this NFT API helps you - please star this project, every star makes us very happy!

Moralis [NFT API](https://moralis.io/api/nft/) is the ultimate tool for building an NFT application. Looking to build an NFT project such as an NFT marketplace, a portfolio site, NFT-based authentication or an NFT auction site? If so, Moralis NFT API is the tool for you.

It’s never been so easy to fetch NFT metadata, NFT owners, NFT transfers, NFT collection metadata, and much more. This NFT API isn’t just blazing fast - it also features support for a long list of EVM chains, such as Ethereum, BNB Chain, Polygon, Arbitrum, Avalanche, Palm Network, and many more!

# 🤝 Need help?

If you need help with using the NFT API or have other questions - don't hesitate to write in our community forum and we will check asap. [Forum link](https://forum.moralis.io/). We are answering questions 24/7
