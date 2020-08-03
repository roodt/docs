---
id: technical_faq
title: Technical FAQ
sidebar_label: Technical FAQ
---

Welcome to the Frequently Asked Questions. To contribute, use the `Edit` button on the right.

This Technical FAQ is dedicated to technical questions about the technical architecture of the project.  It is not intended to cover specific development questions. For those, please see the [developer FAQ](/roles/developer/faq)  For more specific question areas, please see the appropriate section in the sidebar menu.

## Technical FAQ


## Comparisons to Other Technologies

### How does NEAR's design compare to ETH 2.0?
*Last updated: 20200803*

Note that Ethereum 2.0 is just a proposal at the moment, so it may change.  Overall, Eth 2 is essentially designed to be nuclear-war-proof.

We optimized for liveness with BFT assumptions so we say a block is final within 2-3 seconds

On NEAR, all calls are asynchronous and shards are homogeneous so it’s easy for contracts to operate across shards.  We ensure messages get routed properly between the blocks.

On Eth2.0 that’s not really designed but generally you’ll have an account on every shard, you’ll have to decide where you want to deploy your contract and you’ll be very aware of which shard you’re on and have to program around it.


#### What tradeoffs did this design require you to make?
*Last Updated: 20200625*

The main thing that is different with NEAR is that a number of block producers that maintain consensus can’t be too big. So right now we’re going after 100.  The top consensus will be operated by 100, then another set that’s 100 * # shards, then building up layers.

Vs Eth2 which is planning to have millions (or at least tens of thousands).  If you need consensus fast, you need fewer nodes to come up with consensus.

Also, asynchronous systems don’t have transactions as much so composability isn’t quite as strong. You have to keep in mind that you’re in an asynchronous environment (so there are async callbacks floating around).  You have all the tools to manage callbacks, so not too bad for a programmer used to that.



### How does NEAR's design compare to Polkadot?
*Last updated: 20200103*

The main difference is that in Polkadot every application needs to have its own blockchain (which is pretty hard to launch) and there are only 32 slots (up to 100 later). Whereas in NEAR it's straightforward to launch an app (you can try it on testnet now - https://near.dev/) and there is no limit on how many apps. Additionally, there are a bunch of consensus, security, staking, economics, smart contracting differences on top of it but they won't fit here.

The other major difference is our focus on user and developer experience - we are really trying to make it easy for non-crypto ppl to build stuff. We measure ourselves based on how easy it is to start using apps on NEAR by folks who never owned crypto for example.


## Asynchronous System Questions

### How does Atomicity work on NEAR?
*Last Updated: 20200625*

Atomicity is more complex in an asynchronous system.  We’re still figuring it out a bit since you have to see how the system is actually used before designing this appropriately.

NEAR is expected to bundle things into a Safe, which is sort of like that, but it hasn’t been implemented that since first there needs to be proven demand for it.


## Bridge Questions

TODO