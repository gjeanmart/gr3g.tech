---
title: Multis integrates The Graph to offer an even stronger multisig wallet
date: 2020-07-01 12:00:00
---
At [Multis](https://multis.co), we're very proud of the redesign of our crypto-first business banking app. As part of this redesign, we're especially excited about our new integration with [The Graph](https://thegraph.com) to populate our frontend with real-time data from the Ethereum Blockchain.


### Multis provides a simple & smooth neobanking experience

Our wallet reconciles balances and transactions for hundreds of ERC20 tokens and is integrated with some of the most secured DeFi protocols such as [Compound](https://compound.finance) (for earning interest), [TokenSets](https://www.tokensets.com) (for investing ether in automated trading strategies), [Kyber](https://kyber.network) (token exchange) and many more.

One of our aspirations is to attract mainstream users by offering a simple and smooth neobanking experience for businesses dealing with crypto today and tomorrow. We're quite proud of our elegant user interface ☺️


### Streamlining & strengthening: two core needs

Multis is a dApp (Decentralized Application), meaning the core of the application lies on a client side (frontend) communicating in a trust-less manner with the Ethereum Blockchain and DeFi protocols. In order to enrich our wallet and provide the best crypto-banking experience, we chose to use a server-less database ([Firebase](https://firebase.google.com)) to store metadata about accounts and transactions and remain backend-less (NB: no private keys are stored in this database).

It can still be hard to keep track of Blockchain transactions, especially with dozens of smart-contracts (Multisig, ERC20 tokens, DeFi, etc.) to query in a not so friendly format (Remote Procedure Call or `rpc` format).

Reading data directly from a smart-contract is also very restrictive due to some core principles of Ethereum and the EVM. Filters, pagination, or sorted lists are rarely implemented in Solidity because Blockchain developers prefer to focus on security and gas optimisation. That's why we made the choice to use our internal database, which is very useful for storing metadata about accounts and transactions but is less than perfect when it comes to maintaining an accurate transaction history. Transactions can be submitted from outside or dropped and replaced, and users can sometimes close the browser before a transaction is mined. In the past we had some issues processing transactions, especially when network congestion was high. Reconciling a lost transaction was a pain point for us.

What's more, Ethereum and Blockchain represent a new powerful paradigm in terms of software architecture compared to traditional client/server applications. This new paradigm comes with a host of new concepts, terms, and libraries. New developers in the space usually need some time to get used to complex libraries like [web3js](https://github.com/ethereum/web3.js), [etherjs](https://github.com/ethers-io/ethers.js) or [web3j](https://github.com/web3j/web3j) in comparison to standard well documented webservice protocols like RESTful or GraphQL. This long and difficult learning curve is not essential for growing a business and could be used somewhere else.

We believe The Graph project can help us addressing those two points.


### What is The Graph?

[The Graph](https://thegraph.com) is a middleware solution and protocol for indexing and querying Blockchain data with GraphQL. It provides a hosted service (you can also self-host if you want) to index one or several smart contract data into the schema of your choice and query those data via a standard fully-featured GraphQL API.

Today, many projects get around the lack of functionalities offered by web3 libraries and smart-contracts using a centralised indexing service to consume Blockchain events in real time and store data in a database with a friendly format. This solution works well to improve developers and users experience but comes at a high price in development, cost, maintenance and trust.

The Graph provides a ready-to-use framework (called Subgraph) to index and map data from Ethereum to a chosen format and exposes a GraphQL API without running a single backend server or database.

This middleware data layer also addresses the lack of functionalities from smart contract calls, including filters, pagination and sorting available out-of-the-box.

Finally as mentioned, The Graph is currently available as a hosted service, projects can also decide to self-host a node. Soon, a decentralised network will allow anyone to run a node to contribute indexing and query processing to the network building a data marketplace where nodes earn fees for their services.


### The Graph & Multis: a better UI starts on the inside

This is why we decided to move forward with The Graph. We built a Subgraph to index and cache all the on-chain information available about our Multisig (wallet) and its transactions.

One of the major benefits is to replace a complex transaction watcher mechanism and shift the operations of building an accurate transaction history to The Graph.

It also means we shifted from a pure source of truth (Blockchain node) to The Graph but we trust the data exposed for the following reasons:

- Subgraph mappings only process data issued from the Blockchain (events, calls, transactions) and cannot be corrupted with external non-trusted information.
- The Graph node code is open-sourced and can be run by anyone (cf. decentralized network).

Our Subgraph enables a standard (GraphQL) and real-time (websocket push) access to the Multisig data improving both users and developers experience.

It is important for us to remain server-less and backend-less with a simple architecture and code base so we spend less time maintaining a complex infrastructure and more time focusing on our product and business growth.


### Conclusion

Ethereum is a powerful but young technology. Developers can find it hard to build decentralized applications due to the difference of paradigm, lack of tools or learning content. However, as a community, Ethereum constantly succeeds to address pain points and evolve in the right direction attracting more developers in the space. The Graph is one of the tools making Ethereum more accessible and helping businesses like Multis build an even stronger product on top of Ethereum.

If you're interested in making the most of your company's crypto, open an account at [Multis](https://multis.co).
