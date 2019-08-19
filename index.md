# PKT.cash
<small>*so cash*</small>

PKT is a fork of bitcoin with it's own genesis block, it's designed for mesh networking. It uses [PacketCrypt](https://github.com/cjdelisle/PacketCrypt) proof of work which requires internet bandwidth in order to mine and it has a *network steward* address which receives 20% of every coinbase.

## What is a network steward?
The network steward is an address which gets 20% of every new block-mine so that the developers can <s>have lamborghinis</s> finance the building of mesh network technology. Unlike a premine or founder's fee, the recipient of the network steward payout can be changed by a PoS vote.

## What can you do with it?
Not a whole lot at the moment, there's a [text based wallet](https://github.com/cjdelisle/pkt-wallet) but in order to use it, you need to run a [full node](https://github.com/cjdelisle/pktd).

If you're ready to try out the text-based wallet, check out [setting up a wallet](https://pkt.cash/wallet)

## So you wanna mine
The PKT chain uses the [PacketCrypt](https://github.com/cjdelisle/PacketCrypt) work algorith.
PacketCrypt has 2 distinct stages, first an *announcement* stage wherein a miner creates a small
(1KB) message which proves that they did some work, the second stage is the ordinary block mining
stage where a block miner gets a discount on the work they need to do if they can prove that they
have lots of announcements in memory at the time of mining. Importantly, announcements can contain
*content* which, due to it's value to block miners, will be spread far and wide creating a 
decentralized broadcast medium for small messages.

To learn more about mining and get started, check out [mining](https://pkt.cash/mining)

## FAQ

* Can I use it to buy DDoS
  * No
* Is this real?
  * \> puts on morpheus sunglasses
  <br/>
  How do you define "real" ?

## Resources

* Matrix: [#pkt:matrix.org](https://riot.im/app/#/room/#pkt:m.trnsz.com)
* IRC: [#pkt@freenode.net](https://kiwiirc.com/nextclient/irc.freenode.net/pkt?nick=pktwow)
* [Suggest an edit to this page](https://github.com/pkt-cash/www.pkt.cash/edit/master/index.md)
* [Wallet setup](https://pkt.cash/wallet_setup)
* [How to mine](https://pkt.cash/how_to_mine)