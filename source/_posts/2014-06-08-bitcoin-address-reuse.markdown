---
layout: post
title: "Bitcoin Address Reuse"
date: 2014-06-08 14:28
comments: true
categories: [bitcoin, address]
---

Why is it a bad practice? It's bad for privacy and potentially security under certain circumstances.

## Privacy

### Background

My salary is paid in Bitcoin (reality). I use a single Bitcoin address for everything (fictional). You and I are friends (fictional, obviously).

### The Story

Say we had a good time hanging out in a bar. Your significant other called -- it's time to grab the bill and head home. The bar doesn't accept Bitcoin nor credit cards. You don't have any cash. I paid for you. Later you want to pay me back. I give you my one and only Bitcoin address to receive payment. You send some coins to it. You want to check if the transaction is confirmed. You looked it up on blockchain.info. While you are at it, you click on the address, noticing that every month on the first day I receive the same amount of bitcoins. And the amount isn't trivial. Bam! It doesn't take a genius to guess that it's my salary. 

## Security

### Background

Your operation system has a weakass [random number generator](http://en.wikipedia.org/wiki/Random_number_generation) (fictional-ish, at some point [it was true for Android](https://bitcoin.org/en/alert/2013-08-11-android)). You use a single Bitcoin address for everything (fictional, I hope). 

Every time you send some coins, a transaction is created and signed with your private key that corresponds to your one and only Bitcoin address. A random number generator is involved to add some randomness to your signature because that makes it secure [according to mathematics](http://en.wikipedia.org/wiki/Elliptic_Curve_DSA#Signature_generation_algorithm).

### The Story

![xkcd random number](/images/post/2014-06-08-random.png "RFC 1149.5 specifies 4 as the standard IEEE-vetted random number.")

^^ Your random number generator

Because of your weakass random number generator, your two transactions dated four days apart are signed with the same "random" number. Bam! Some smartass figures out your private key by staring at your two transactions for long enough.
