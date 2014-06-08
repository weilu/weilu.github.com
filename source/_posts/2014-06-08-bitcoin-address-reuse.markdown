---
layout: post
title: "Bitcoin Address Reuse"
date: 2014-06-08 14:28
comments: true
categories: [bitcoin, address]
---

Bank account number is often used as an analogy to Bitcoin address when one is first introduced to Bitcoin. Then you heard that it is bad to use the same Bitcoin address for all your transactions. I was asked by 3 different people something along the lines of 

> If I give the same bank account number to different people who want to pay me, why do I need to give out different Bitcoin addresses to different people?

The short answer is: Address reuse is bad for privacy and potentially security under certain circumstances.

## Privacy

__Background:__ All Bitcoin transactions are public. Given an address, anyone can look up all transactions ever sent to and from this address. This is where the bank account number analogy breaks down.

__Scenario:__ My salary is paid in Bitcoin (reality). I use a single Bitcoin address for everything (fictional). You and I are friends (fictional, obviously).

__The story:__ Say we had a good time hanging out in a bar. Your significant other called -- it's time to head home. I paid the bill because you didn't have any cash. Later you want to pay me back. I give you my one and only Bitcoin address to receive payment. You send some coins to it. You want to check if the transaction is confirmed. You looked it up on blockchain.info. While you are at it, you click on the address, noticing that every month on the first day I receive the same amount of bitcoins. And the amount isn't trivial. Bam! It doesn't take a genius to deduce that it's my salary.


## Security

__Background:__ Every time you send some coins, a transaction is created and signed with your private key that corresponds to your one and only Bitcoin address. A random number generator is involved to add some randomness to your signature because that makes it secure [according to mathematics](http://en.wikipedia.org/wiki/Elliptic_Curve_DSA#Signature_generation_algorithm).

__Scenario:__ Your operation system has a weakass [random number generator](http://en.wikipedia.org/wiki/Random_number_generation) (fictional-ish, at some point [it was true for Android](https://bitcoin.org/en/alert/2013-08-11-android)). You use a single Bitcoin address for everything (fictional, I hope).

![xkcd random number](/images/post/2014-06-08-random.png "RFC 1149.5 specifies 4 as the standard IEEE-vetted random number.")

^^ Your random number generator

__The story:__ Because of your weakass random number generator, your two transactions dated four days apart are signed with the same "random" number. Bam! Some smartpants figures out your private key by staring at your two transactions for long enough. You lost all your bitcoins.

There you have it, why reusing Bitcoin address is bad. Until next time,

> Vires in Numeris
