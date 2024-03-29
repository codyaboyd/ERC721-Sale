# FF721GILGAMESH Smart Contract

<p align="center">
<img src="https://github.com/codyaboyd/ERC721-Sale/assets/57097960/02d65555-08fc-40a4-8346-5af1eb7c7c34">
</p>

## Overview

The `FF721GILGAMESH` contract is an ERC721Enumerable token that includes several unique features tailored for creating a mintable, revealable NFT collection. It includes mechanisms for both regular minting with Ethereum and minting with a specified ERC20 token. This contract is designed for projects that require pre-reveal states for their NFTs and offer multiple minting options.

## Features

- **ERC721Enumerable**: Inherits from ERC721Enumerable for efficient tracking and enumeration of owned tokens.
- **Minting**: Allows public minting with either Ethereum or a specified ERC20 token.
- **Reveal Mechanism**: Supports a pre-reveal URI for all tokens before the official reveal.
- **Configurable Parameters**: Owners can set mint prices, supply caps, and other critical parameters.

## Contract Parameters

- `baseURI`: The base URI for all token metadata.
- `baseExtension`: The file extension to append to each token's URI.
- `cost`: The cost of minting each token with Ethereum.
- `tokenPrice`: The price for minting a token with the specified ERC20 token.
- `maxSupply`: The maximum supply of tokens that can be minted.
- `maxMintAmount`: The maximum number of tokens that can be minted in a single transaction.
- `paused`: A boolean to enable or disable minting functionality.
- `revealed`: Controls whether the token URIs are revealed or hidden.
- `notRevealedUri`: The URI used for all tokens before the reveal.
- `token`: The address of the ERC20 token used for minting.
- `devW`: The developer's wallet address for receiving ERC20 tokens from minting.

## Functions

### Minting

- **mint(uint256 _mintAmount)**: Mint tokens with Ethereum. Requires the contract not to be paused, the mint amount to be within limits, and sufficient payment.
- **mintWithToken(uint256 _mintAmount)**: Mint tokens with the specified ERC20 token. Transfers the token price from the caller to the developer's wallet.

### Token URI Management

- **tokenURI(uint256 tokenId)**: Returns the URI for a token's metadata. If the collection is not revealed, it returns the `notRevealedUri`.
- **reveal()**: Reveals the collection, enabling the true metadata URIs to be visible.

### Configuration

Owners can adjust critical parameters of the contract, including mint costs, supply cap, ERC20 token price, developer wallet, minting token, and base URI settings.

### Withdrawal

- **withdrawFTM(uint256 amount)**: Allows the owner to withdraw specified amounts of Ethereum from the contract.

## Usage

This contract is designed for NFT projects that require a flexible and feature-rich minting process. It accommodates both traditional Ethereum-based minting and alternative minting methods using ERC20 tokens, providing versatility in how participants can join the minting process.

## Deployment

To deploy this contract, specify the name and symbol of your NFT collection, along with the initial base URI and a not-revealed URI. After deployment, you can configure the contract's parameters to fit your project's needs before starting the minting process.

## Security Considerations

Ensure that all external calls, especially those involving token transfers, are secured against reentrancy attacks. Regularly audit and test contract functionalities, particularly those that modify critical state variables or handle funds.

## Conclusion

`FF721GILGAMESH` offers a comprehensive solution for NFT projects looking for a customizable and robust minting and reveal process. Its flexibility and range of features make it suitable for a wide variety of NFT applications.

## Inventory System

The `FF721GILGAMESH` contract introduces an advanced inventory system designed to enhance user interaction with NFTs. This system allows users to view and manage their NFT collections more efficiently, providing a seamless experience for both collectors and creators.

### Features

- **Paginated Viewing**: Users can browse their NFT collection page by page, making it easier to navigate large collections. This feature utilizes the `getPaginatedTokenData` function to display NFTs in manageable segments.
- **Enhanced Token Data**: Each NFT within the inventory system is associated with comprehensive data, including token ID and metadata URI. This rich information facilitates a deeper connection between the NFT and its holder.
- **Dynamic Page Calculation**: The `getTotalPages` function dynamically calculates the total number of pages based on the user's collection size and desired items per page. This ensures scalability and ease of access regardless of collection size.

### Implementation

- The inventory system is seamlessly integrated into the `FF721GILGAMESH` contract, leveraging ERC721Enumerable's capabilities for efficient tracking and enumeration of owned tokens.
- Structured data returned by the inventory system enhances the frontend application's ability to present NFTs in a user-friendly manner, including pre-reveal and post-reveal states.

### Usage

To utilize the inventory system:

1. **Viewing Collections**: Call `getPaginatedTokenData` with the owner's address and page number to retrieve a subset of their NFT collection.
2. **Calculating Pages**: Use `getTotalPages` to determine the total number of pages available for a given collection, aiding in navigation and UI design.

### Conclusion

The inventory system adds a layer of sophistication to the `FF721GILGAMESH` contract, making it an indispensable tool for projects that prioritize user experience and engagement with NFT collections. Its integration into the contract reflects a commitment to providing a comprehensive and accessible platform for NFT creators and collectors alike.

