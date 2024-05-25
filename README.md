# Token List Bridge Utils

## Description
This package contains utility functions used for converting an L1 token list into a cross-chain tokenlist by adding cross-chain mapping information for Arbitrum, Optimism, and Polygon to a given L1 list.

ex:

      "name": "Uniswap",
      "address": "0x1f9840a85d5aF5bf1D1762F925BDADdC4201F984",
      "symbol": "UNI",
      "decimals": 18,
      "chainId": 1,
      "logoURI": "ipfs://QmXttGpZrECX5qCyXbBQiqgQNytVGeZW5Anewvh2jc4psg",
      "extensions": {
        "bridgeInfo": {
          "10": {
            "tokenAddress": "0x6fd9d7AD17242c41f7131d257212c54A0e816691"
          },
          "137": {
            "tokenAddress": "0xb33EaAd8d922B1083446DC23f610c2567fB5180f"
          },
          "42161": {
            "tokenAddress": "0xFa7F8980b0f1E64A2062791cc3b0871572f1F7f0"
          }
        }
      }}
Also adds a "root-level" token entry for each of the L2's that a token maps to.

ex. for Optimism:


    {
      "name": "Uniswap",
      "address": "0x6fd9d7AD17242c41f7131d257212c54A0e816691",
      "symbol": "UNI",
      "decimals": 18,
      "chainId": 10,
      "logoURI": "ipfs://QmXttGpZrECX5qCyXbBQiqgQNytVGeZW5Anewvh2jc4psg",
      "extensions": {
        "bridgeInfo": {
          "1": {
            "tokenAddress": "0x1f9840a85d5aF5bf1D1762F925BDADdC4201F984"
          }
        }
      }
    }


## Functions Overview

chainifyTokenList

 * Given a chain ID (Optimism, Polygon, or Arbitrum) and a TokenList, returns the TokenList with `extensions` filled.
 * @param chainId chainId to operate on
 * @param l1TokenListOrPathOrUrl either an L1 TokenList object or a path/url to a TokenList
 * @returns L1 TokenList with `extensions` filled for the given network


mergeTokenLists
 * Merges two token lists, resolving conflicts to primary list.
 * @param primary primary token list to resolve conflicts to
 * @param secondary secondary token list
 * @returns merged token list



## Usage (from external package):
### Install Package
`yarn add swifydex-token-list-bridge-utils`

or

`npm i swifydex-token-list-bridge-utils`


## Run Tests

`yarn install`

`yarn test`
