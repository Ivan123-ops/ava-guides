# How to deploy a ERC-20 token on Avalanche with OpenZeppelin
Published on 3 August 2021

***YouTube guide available! (Click on the image below)***

[![Youtube guide](http://img.youtube.com/vi/OCyOyqDDXOA/0.jpg)](https://www.youtube.com/watch?v=OCyOyqDDXOA)

This guide will help you to create a ERC-20 token on Avalanche Network. The main idea is to deploy Solidity smart contract on Avalanche blockchain. 
So now, let’s walk through the steps.

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

## 3. Creating ERC-20 token with Remix
Now it’s time to create our ERC-20 token! Visit [Remix](https://remix.ethereum.org/), click “SOLIDITY” and “New file”. 
After that, navigate to the Workspaces section (files under the logo) and see a blank file, which you should rename. 
In this case we name it avaerc.

![Remix](https://miro.medium.com/max/700/1*cZzVYKPcEWdq8tg47OcaYA.png)
![Remix](https://miro.medium.com/max/700/1*xxo_itydp95p7-hMjDgRRg.png)

We will use a ERC-20 OpenZeppelin contract, so there is no need no write anything on our own, we can just write
```
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/presets/ERC20PresetMinterPauser.sol";
```

After this, go to the Solidity compiler section and press “Compile”. Press the “Compile avaerc.sol” and return to the file directory.

Next, go to files section and find ERC20PresetMinterPauser.sol in presets.

![Remix](https://miro.medium.com/max/700/1*iX9KuUxmGps2e-2gQz3vag.png)

After this, go to the Solidity compiler section and press “Compile”. Mind the compiler version, this should be higher than your source file is. For example, in our file, it’s written pragma solidity 0.8.0 and compiler is 0.8.4, so it’s ok. If you didn’t change anything in the file, you should be OK.

![Remix](https://miro.medium.com/max/700/1*4mUpwlIf6yC8XshA_Pa4bA.png)

This contract includes the following abilities:

* the ability for holders to burn (destroy) their tokens
* a minter role that allows for token minting (creation)
* a minter role that allows to stop all token transfers

This contract is already ready for deployment so we don’t need to change anything and can move on to “Deploy and run transactions” section which is right under Compiler icon.

## 4. Deployment
In this section, choose Injected Web3 environment and connect your Metamask account with C-AVAX funds we requested from the faucet. In the “CONTRACT” field, select ***ERC20PresetMinterPauser.sol*** as it’s the main contract.
Right before deployment, click the button next to “Deploy” sign and fill in the requisites:

NAME — name of the token (AVAERC)

SYMBOL — (AVAE)

![Remix](https://miro.medium.com/max/700/1*s1Qt7n89oU2pG9WFf60qLw.png)

In the lower sections, click debug and find transaction hash, copy it.

![Remix](https://miro.medium.com/max/700/1*aF7e3QF1YZkkIBg-jMj6iw.png)

Then, navigate to the [explorer](https://cchain.explorer.avax-test.network/) and inset you txhash. 
You will see the wallet address (0x6F0935E3F3a53a659f6bAf938F387c626d784F84) 
and our ERC-20 contract address — 0x7ADc290F0098a8A7641e76238E86AfA5AA646e70.

![Remix](https://miro.medium.com/max/700/1*KsBpIdKww9ion2_it-6BiA.png)

We have deployed our contract but now let’s mint some ERC-20 tokens!

## 5. Minting tokens

Return to the Deploy and run transactions section and click under “Deployed contracts”. Here you can see some functions of the contract. You can refer to OpenZeppelin documention in order to find out more about smartcontract functions. We will focus on one that allows minting.

![Remix](https://miro.medium.com/max/700/1*0IRvvh3Wg5scDoIqHLpS7A.png)

Open the mint tab and enter address you want to mint tokens to and the amount in WEI (for example, if we want to mint 1000000 tokens, we should enter “1000000000000000000000000”, you can also use https://etherchain.org/tools/unitConverter to convert. Press “Transact” and confirm in Metamask.

In the DEBUG section, we can see txHash — and we can find this txHash on the explorer. We can see that token minting succeeded and out token contract address is 0x7ADc290F0098a8A7641e76238E86AfA5AA646e70. You can click on the contract and look through it’s details.

![Remix](https://miro.medium.com/max/700/1*ktYnhW157hZ9VoCKZvdqCA.png)

## 6. Adding NFT token to Metamask

Open your Metamask Assets and click “Add token”. Insert the contract address we previously found out (in our case — 0x7ADc290F0098a8A7641e76238E86AfA5AA646e70), token symbol — AVAE and since NFT is non-fungible — leave decimals at 0.

![Remix](https://miro.medium.com/max/300/1*gqFfO16SCbE1NbxZ3aLIbg.png)

## 7. Conclusion

We have succesfully minted ERC-20 tokens on Avalanche Network with OpenZeppelin! Now you can move on to Mainnet and create "real" tokens. You can also follow OpenZeppelin documentation to find out more functions of it's smartcontract https://docs.openzeppelin.com/contracts/4.x/erc20
