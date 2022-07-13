# Cypher
# Table of contents

- [Cypher](#cypher)
  - [Introduction](#introduction)
    - [What is a Block-chain](#what-is-a-block-chain)
    - [How a Block gets accepted in the Block-chain](#how-a-block-gets-accepted-in-the-block-chain)
  - [Live-Messenger](#live-messenger)
    - [How a classic Live-Messenger works](#how-a-classic-live-messenger-works)
    - [How Cypher Live-Messenger works](#how-cypher-live-messenger-works)
    - [How do Nodes earn rewards](#how-do-nodes-earn-rewards)
  - [Conclusion](#conclusion)

## Introduction
For years big companies like Google, Facebook, Snapchat, Twitter, etc, have been providing Live-Messengers, while the data produced by its users has been collected and analyzed and advertised upon, and in the worst case, data has been shared with other Companies or upon request shared with Government Agencies. All this data has been sitting in the United States of America, China and some European Countries, even if the end-user was and never will physically be in the in the place the data is stored.

No User on said platforms was able to control the flow of data, and most Users do not know what data is collected and analyzed. Hundreds of Journalists have been spied upon, and even imprisoned because of private communication on these platforms. Even more Journalists have been banned from these Platforms for doing their research. 

Power has been abused by Governments, Companies and employees. Leaked Messages have destroyed thousands of lives, sometimes it even costed lives, which is why Cypher is aiming to stop all of this.

Cypher is a decentralized, free, open-source and censorship-free Live-Messenger. The infrastructure is based on Blockchain Technology, which encourages people to lend the Cypher Network Bandwidth in exchange for Cypher (Crypto Currency).

Cyphers end-goal is to replace current Messengers, the vision of the end-product is similar to Snapchat and WhatsApp, a platform for everyone, talking to friends and family, just like on traditional Messengers, with an open space for Content Creators to show their Content to Cyphers Users.

This Document explains how Cypher is working, if you want to read more technical details on how the official Cypher Node works, please refer to the Technical Documentation provided in the [official GitHub Repository](https://github.com/CypherCryptoLabs/cypher).

```
Tip: It is a good idea to read the Bitcoin White-paper before you continue reading this
document, as this document does not explain the mathematical principals behind a
Crypto-currency and Blockchain.

This document assumes that you have basic knowledge in Crypto-currencies and Block-chains. 
```

### What is a Block-chain
A Blockchain in simple terms is nothing but a Databse. The difference bewteen traditional Databases is that in a Blockchain, there are only 2 operations that can be performed on the Databse: Read and Append. To understand this better, we have to understand how a Blockchain is actually storing data.

In a traditional Database, each record of Data is refereed to as a "Row", Rows are stored in Tables. Each Column in a table can only store one specific data type, like Age, Name, Address, etc.

In a Block-chain, data is not stored in Rows, its stored in "Blocks". A Block contains information about the previous Block, its creation time and the creator of the Block, as well as the payload of the Block, in this case the payload only contains transactions. Blocks are chained together with a check-sum, providing proof that the previous Block is intact and valid, thus chaining each Block to its previous Block.

You can only read Blocks or append a new one to the chain, you cannot modify previous Blocks in any way, without breaking the checksum references. Even if the checksums would all be recalculated, an attacker would still need to somehow get the public Network to accept the modified copy of the Block chain.

### How a Block gets accepted in the Block-chain
The Cypher Block-chain uses a Consensus Algorithm called "Proof of Stake", or P.o.S. Most Block-chains today use "Proof of Work", which, in very simple terms, means that a very computationally expensive equation needs to be solved for a Block to be accepted by the Network, and added to the Block-chain.

In Cypher, every Minute a semi-random Node (you will learn in "[How do Nodes earn rewards](#how-do-nodes-earn-rewards)" why its only semi-random) gets selected by the Network, to propose a new Block. This is called "forging", and the selected Node is called "Forger". Up to 128 other Nodes get selected by the Network to vote in favor or against the proposed Block, these Nodes are called "Validators".

If more than 50% of Validators agree on a Block being valid, each Node will now append the Block to their local copy of the Block-chain, and the cycle repeats.

Nodes that voted falsely will be punished and 15 Cypher will be removed from their balance, thus encouraging Nodes to only accept Blocks that are actually valid.

## Live-Messenger
Now that you understand the basics of how the Cypher Blockchain works, it is time to explain how Cypher aims to build a decentralized Live-Messenger.

Currently, most Crypto Projects infrastructure is used for nothing but transactions, while making safe and anonymous transactions possible, the Nodes running Crypto Networks have no other real purpose.

Expensive Hardware is being wasted, sitting idle and not benefiting the non-crypto-enthusiasts. Cypher aims to create a large, global, and decentralized Network, that will be used as the Backbone of the Cypher Live-Messenger, with anyone being able to participate, and earn rewards.

Nodes are pushed towards being online for as much time as possible due to how Proof of Stake works, thereby guaranteeing high availability, and high quality of Service, which is something a Live-Messenger should obviously have. The global Nature of a decentralized Crypto Network also helps availability, Latency, and throughput for a Live-Messenger.

### How a classic Live-Messenger works
To explain how the Protocol works, imagine a scenario in which Alice and Bob want to communicate with each other, without building a highly available infrastructure.

In a classic Messenger, Alice and Bob both have to generate a Asymmetric cryptographic key-pair, which consists of a public Key and a private Key. Alice has to share her public Key with Bob, and vise versa. Platforms like Whatsapp or Telegram automate this process for the End-User. After the exchange of Keypairs, Alice can write a Message, and encrypt it with Bobs public Key, and sign it with her own private Key. This ensures that the Message was created by Alice, and can only be read by Bob. The Message is sent over the Messengers Infrastructure to Bobs Device, where the Signature that Alice created is verified, and then decrypted with Bobs private Key.

The issue is that for the normal User it is very difficult to verify if the Message was really only encrypted with Bobs public Key, or if there is a second copy that was encrypted with the Infrastructure-providers keys.

If later is true, that would mean that, in fact the conversation is End-To-End encrypted, but not secure, as all messages can still be read by a third-party.

The User has to trust the Provider that they do not have a Backdoor like this one implemented in their software. Even if that is not the case, with the Metadata that is automatically created when writing a message, you can still create Advertisements, and sell other Data.

### How Cypher Live-Messenger works
Cyphers general process of sending a Message is very similar, with a distinct difference:

The Infrastructure on which the Message is sent on is determined by Alice and Bob themselves. The Clients select multiple Nodes, which will be used to transmit their Messages, and these Nodes change every couple of hours, to make it more difficult for a Node to collect enough Metadata of its Users.

Since the Messenger Client is open-source, Users can verify themselves if it contains any Backdoors, collection of Metadata is not an issue since Nodes change enough times, and if the User really wanted, they could only use their own Node for communication, if they still dont trust the Network.

### How do Nodes earn rewards
Each time a Message is sent on the Network, the Users have to select 8 different Nodes, which can be used to receive a Message on. The Message needs to be sent to each of those Nodes, and the Receiver selects one of them to get the Message from.

When the Message is being accessed by the Receiver, a "Proof of Reception", or P.o.R. for short, needs to be signed by the Receiver, and sent back to the Node which they requested the Message from.

This P.o.R. is needed if the Receiver still wants to be able to receive further Messages by the Network, if too many Messages have not been answered with a P.o.R., any incomming Messages addressed to the Receiver will be blocked.

It should be noted that the Sender of a Message needs to perform a small Proof of Work, in order to make Spam expensive and not worth it.

When a Node receives a P.o.R., it is shared in the whole Network, with each P.o.R., the Node becomes more likely to be selected as the Forger for the netxt Block, thus having the chance of receiving a reward.

## Conclusion
Cypher is a simple protocol, that is able to solve many Privacy and Security related issues, while bringing Block-chain technology closer to the Masses, and creating an actual Use case, outside of Transactions, for it.

Cypher is still very early in Development, but hopefully advancing relatively quickly, and soon challenging the current Information Titans in the world.

