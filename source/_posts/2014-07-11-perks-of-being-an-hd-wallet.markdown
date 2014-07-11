---
layout: post
title: "Perks of Being an HD Wallet"
date: 2014-07-11 08:27
comments: true
categories: [bitcoin, wallet, HD wallet, hierarchical deterministic wallet, bip32]
---

The technical crowd in Bitcoin land has been excited about hierarchical deterministic(HD) wallet since the day it came out. But what benefits exactly does it bring to regular end users?

tl;dr much more simplified backup + better privacy

To understand why that is the case, we need to start with how non-HD wallet works.

## The non-HD way

The primary job of a wallet is to manage your keys. To spend any funds, the wallet needs to find private keys(s) that correspond to the spendable funds. To receive any funds, the wallet needs to tell you what is the address that corresponds to a private key that it's aware of. Previously, we've already established that [it is bad to use a single address for all your transactions](/blog/2014/06/08/bitcoin-address-reuse/). But why do wallets still do it? A single address is the default setting for most wallets because it has its perks. For wallets, from a technical point of view, a single address is easy to manage. A user backs up his/her one and only private key and be done with it for good. For users new to Bitcoin, the bank account analogy stands, so less confusion for users. Privacy seems like a reasonable price to pay.

Some wallets allow users to create more addresses. I guess the rationale is that those who care to create more addresses are power users who more or less know some inter workings of Bitcoin. So they shall be given the freedom to manage their own addresses/keys. But here's the catch, in case you don't already know, every time you create a new address, you need to back up your wallet. Why? The point of a backup is to save another copy of all your private keys that correspond to addresses that you have unspent funds or can potentially receive funds at in the future. So in case that you lose the device that has your wallet which holds all the private keys, you can still access your funds on another device by importing the backup keys. In case one forgets to carry out a backup in time, he/she risks losing funds that are sent to the addresses whose corresponding private keys are not among the backed up keys.

In short, in the non-HD land, as a user, if you want to avoid address reuse and ensure the safety of your funds at the same time, you'd have to go through the inconvenience of carrying out backups whenever you creates a new address. Is there a way we can avoid this privacy/fund security/convenience trade-off? And even better, can we have wallets abstract away the key/address management from users altogether?

## HD wallets come to the rescue

The technical specs of hierachical deterministic wallets are defined by [BIP32](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki). The gist of BIP32 is that it defines how a tree of private keys can be derived from a single master key in a deterministic manner. "Hierarchical" refers to the tree-like structure. "Deterministic" means that so long as one follows the specs, a given master key is guaranteed to always produces the exact same tree regardless of how many times one carries out the derivation. HD wallets have many potential applications. Here, I'm only going to focus on how it solves the above-mentioned problems with the non-HD wallets.

![xkcd tree](/images/post/2014-07-11-tree.png "Not only is that terrible in general, but you just KNOW Billy's going to open the root present first, and then everyone will have to wait while the heap is rebuilt.")

^^ A tree-like structure

With BIP32, the line between the user responsibilities and wallet responsibilities is clear -- user keeps the master key safe; and it's the only backup he/she will ever need. While the wallet generates keys in the tree when necessary, for example, whenever an address is used for receiving funds, the wallet generates the next address in line to be used for the next transaction. The user always gives out the current address wallet displays for optimal privacy, while the wallet needs to watch all the addresses it has ever generated for the purpose of receiving funds. In case a user loses his/her device that has the wallet, they can enter their master key in an HD wallet on another device. The wallet goes ahead and derive the tree of private keys, scans each key for funds. And there we go, a wallet recovered.

Enough said, embrace HD wallet, for simpler backup and better privacy :)

