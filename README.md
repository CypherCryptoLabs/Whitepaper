# Cypher
# Table of contents

- [Introduction](#introduction)
- [How does Cypher work](#how-does-cypher-work)
  - [What is a Blockchain](#what-is-a-blockchain)
  - [Consensus Algorithm](#consensus-algorithm)
    - [P.o.R](#por)
    - [Voting slot](#voting-slot)
    - [Selecting Validators](#selecting-validators)
    - [Choosing a forger](#choosing-a-forger)
    - [Forging a Block](#forging-a-block)
  - [Privacy and Security](#privacy-and-security)
  - [Future plans](#future-plans)

## Introduction
For years big companies like Google, Facebook, Snapchat, Twitter, etc, have been providing Live-Messengers, while the data produced by its users has been collected and analyzed and advertised upon, and in the worst case, data has been shared with other Companies or upon request shared with Government Agencies. All this data has been sitting in the United States of America, even if the end-user was and never will physically be in the U.S.A.

No User on said platforms was able to control the flow of data, and most Users do not know what data is collected and analyzed. Hundreds of Journalists have been spied upon, and even imprisoned because of private communication on these platforms. Even more Journalists have been banned from these Platforms for doing their research. 

Power has been abused by Governments, Companies and employees. Leaked Messages have destroyed thousands of lives, sometimes it even costed lives, which is why Cypher is aiming to stop all of this.

Cypher is a decentralized, free, open-source and censorship-free Live-Messenger. The infrastructure is based on Blockchain Technology, which encourages people to lend the Cypher Network Bandwidth in exchange for Cypher (Crypto Currency).

Cyphers end-goal is to replace current Messengers, the vision of the end-product is similar to Snapchat and WhatsApp, a platform for everyone, talking to friends and family, just like on traditional Messengers, with an open space for Content Creators to show their Content to Cyphers Users.

This Document explains how Cypher is working, if you want to read more technical details on how the official Cypher Node works, please refer to the Technical Documentation provided in the [official GitHub Repository](https://github.com/CypherCryptoLabs/cypher).

## How does Cypher work
Cypher is a relatively simple Protocol. Cypher uses a simple Blockchain, similar to the original Bitcoin Blockchain, because Cypher is not intended to be used primarily as a Currency, it is intended as a reward System, which has the secondary purpose of a Currency. Smart Contracts and Layer 2 are currently not planned. 

### What is a Blockchain
A Blockchain is a Database, in which you can only perform 2 operations: Read and Append. You cannot delete any entries or modify them. A dataset in a Blockchain is called "Block". A Block in Cyphers Case only contains a few different types of information (Other Blockchains may include other Information, please read other Projects White-papers to understand how their Blockchain works):

- Timestamp at creation of the Block
- Previous Block Hash, to prove the previous Blocks integrity
- Payload, which contains all Transactions saved in the current Block
- Reward Amount and Address, to tell which Address is credited for the creation of the Block
- Signatures, to prove the Block has been approved by the Network
- Network Diff, which proves which Nodes were online during the creation of the Block

The Cypher Blockchain is synced across all Nodes in the Network, via the Proof of Reception Consensus Algorithm.

### Consensus Algorithm
Cypher uses a new Consensus, called "Proof of Reception". The classic Proof of Work, or P.o.W. for short, and Proof of Stake, P.o.S. for short, do not offer the functionality required by Cypher, although, Proof of Reception, P.o.R., is technically a P.o.W. Consensus. There are some key differences:

A classic P.o.W. as seen in Bitcoin is based on senselessly hashing data to find a hash that will be accepted by the network. This may be very secure, but its wasting a lot of energy, for nothing in return except Network security. Imagine this could be turned into something more useful. This is where P.o.R. comes into play.

P.o.R. does something similar, nodes need to find a good enough hash to be deemed the creator of a block. But the data that needs to be hashed, is not based on transactions, rather than messages send over the network.

#### P.o.R
A P.o.R. is a message combined with its metadata, signed by the recipient.

#### Voting slot
A voting slot is a 1 minute timeframe, during which Validators and the forger are selected, a block proposed and appended to the Blockchain if the Block is validated by at least n/2 + 1 nodes, where n represents the number of Nodes in the network with an upper limit of 128.

#### Selecting Validators
In the first stage, Validators are selected for the current voting slot. This works by hashing the latest blocks hash concatenated with current voting slots Unix timestamp. The voting slots timestamp is the timestamp of the beginning of a minute, which means it can evenly be divided by 60 seconds (60000 milliseconds).

This hash is called the Voting slot seed. This seed is very important for the rest of the voting slot.

First of all, all Nodes blockchain Addresses are thrown into a pool with the seed, and sorted by their numerical value. Then the seeds 2 neighbors are chosen as validators. Hash the seed, and repeat until there is 128 Nodes selected as validators, or there are no nodes left in the pool.

#### Choosing a forger
Choosing a forger can go 2 ways, depending on P.o.R.s being present or not.

If there are no P.o.Rs present, the Node who's numerical value of the Blockchain address is closest to the numerical value of the voting slots original seed, will become forger and can proceed to propose a block.

If there is one or more P.o.R.s present, all P.o.R.s will be collected in a pool, and the P.o.R.s numerical value of its hash, closest to the numerical value of the seed, will be deemed the winner. The winner P.o.R.s owner, the node that send it into the pool, will be the forger and can propose a block.

#### Forging a Block
After being chosen as Forger, a Node has to build a Block, containing transactions. The P.o.R. doesn't appear in the Block (this will very likely change though, when NetworkDiff is enabled).

The proposed Block will then be fetched by all Validators, if they approve of the Block, they will share their signature, if they receive more than n/2 + 1 number of signatures, they will start sharing the block in the network, and the whole cycle can restart.

### Privacy and Security
Cypher will be as secure and private as possible, for this reason, a User will be able to create a new Identity (Crypto Wallet) for each communication partner, so Messages can not be cross-linked by Nodes with the Blockchain-Address. Using a Network like Tor, the communication with Nodes will be completely anonymous, and close to impossible to trace.

Senders of a message will have to prove to the Network, that the Receiver is actually willing to be contacted, for this, the Sender needs to include a copy of their public Key signed by the Receivers. This way, contacting random Addresses is not possible, and preventing spam and abuse.

### Future plans
Cypher Crypto Labs is currently considering moving all of Cyphers Network to Tor. This would improve the Nodes anonymity, as well ass the Users. There are certain issues that need to be solved before that step will be taken however.
