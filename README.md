# RSK <-> ETH Token Bridge

Ethereum/RSK Bridge that allows to move ERC20 tokens from one chain to the other.

## Rationale
Cross chain events are very important in the future of crypto. Exchanging tokens between networks allows the token holders to use them in their favorite chain without beeing restricted to the contract owner network choice. Moreover this also allows layer 2 solutions to use the same tokens on different chains, this concept together with stable coins creates a great way of payment with low volatility across networks.

## Usage
See the ['interaction guide'](./docs/Interaction.md) for more information on how to use the bridge.

## Overview
We have a smart contract bridge on each network, the bridge on one chain will receive and lock the tokens, then it will emmit an event that will be served to the bridge on the other chain. There is a Federation in charge of sending the event from one contract to the other.
The bridge contracts are upgradeable as we want to move to a decentralized bridge in the future. Here is the first 
[POC of the trustless decentralized bridge](https://github.com/rsksmart/tokenbridge/releases/tag/decentralized-poc-v0.1)

## Developer

### Contracts
The smart contracts used by the bridge and the deploy instructions are on the bridge folder

### Federator 
The code used for the federator to cross the events created by the bridge from one chain to the other