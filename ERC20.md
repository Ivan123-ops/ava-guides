# How to deploy a ERC-721 token on Avalanche with OpenZeppelin
Published on 3 August 2021

YouTube guide available! 

[![Youtube guide](http://img.youtube.com/vi/OCyOyqDDXOA/0.jpg)](https://www.youtube.com/watch?v=OCyOyqDDXOA)

This guide will help you to create a ERC-721 token which represents ownership of non-fingible tokens or NFTs.
In this case, every token is unique and and the same time can be transferred between individuals.

## 1. Setting up Metamask
First thing you need to do is to setup a custom RPC in your Metamask in order to connect to FUJI Testnet on Avalanche C-Chain. 
In case you want to operate on Mainnet, please, use the data for Mainnet.
Click on the network selection tool and choose Custom RPC.

![Metamask](https://miro.medium.com/max/800/1*OIe2uZT9orcED8ZWrFbGkw.png)

![Metamask](https://miro.medium.com/max/500/1*HKl96-x2e5GPfr1BRiRU4Q.png)

![Metamask](https://miro.medium.com/max/680/1*kFIA7ewIF8WAA0q_WNeX8A.png)

You should use following credentials depending on what network you want to interact with. 
In this guide we will be using FUJI Testnet.

Network Name: Avalanche C-Chain

New RPC URL:
https://api.avax-test.network/ext/bc/C/rpc for Fuji Testnet
https://api.avax.network/ext/bc/C/rpc for Mainnet

ChainID:
0xa869 for Fuji Testnet
0xa86a for Mainnet

Symbol: C-AVAX

Explorer:
https://cchain.explorer.avax-test.network for Fuji Testnet
https://cchain.explorer.avax.network for Mainnet

After selecting network you should see this page.

![Metamask](https://miro.medium.com/max/600/1*EAajjjBfKpqN2E52KfdSow.png)

Next step will be requesting C-AVAX tokens.

## 2. Acquiring faucet tokens
In order to operate on C-CHAIN, you will need to acquire C-AVAX tokens from the [faucet](https://faucet.avax-test.network/). 
Simple visit the link, provide your Ethereum address and click “REQUEST 10 AVAX”. 
Next, go to your Metamask and you will see updated balance. 
Tokens from this faucet are only for testing purposes and don’t represent any value.
