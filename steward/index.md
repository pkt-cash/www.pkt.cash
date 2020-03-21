# Network Steward

20% of every newly mined block goes to a network steward address.
This address can be changed by way of a PoS based vote. See the
[Network Steward Vote](https://pkt.cash/steward/vote) for more information
about the mechanics of the vote. The payments to the network steward address
have one special rule, they cannot be spent after 129600 blocks
(approximately 3 months) have elapsed, so if the network steward cannot decide
how to spend its treasury, the PKT will be burned rather than piling up.

The balance of this document will be about the network steward with the address
`pkt1q6hqsqhqdgqfd8t3xwgceulu7k9d9w5t2amath0qxyfjlvl3s3u4sjza2g2` which we will
henceforth refer to as The Network Steward.

## What is The Network Steward

The Network Steward is a multi-signature wallet which requires 3 out of 5
signatures in order to make a payment. The keys are held by:

* [cjd](https://github.com/cjdelisle) - cjdns original author
* [Arceliar](https://github.com/Arceliar) - Yggdrasil original author
* [benhylau](https://github.com/benhylau) - Contributor at Toronto Mesh
* [NeilAlexander](https://github.com/neilalexander) - Yggdrasil release manager
* [Backupbrain](https://github.com/backupbrain) - Creator of NetNinja VPN device

All of the participants have agreed not to enter into any relationships which
would affect their ability to act impartially on behalf of the PKT chain.

## Network Steward Charter

The objective of The Network Steward is to reduce barriers of entry to
network / VPN providers in the pursuit of increased individual autonomy
and privacy.

Key aspects of this objective include:

* Financing the development of open source networking software
* Lobbying for improved regulatory environment for small network operators
and more generally, for internet freedom, privacy, and decentralization
* Purchasing property such as proprietary software or radio frequency spectrum
rights in order to put these things in the commons

In order to achieve these goals, The Network Steward will occasionally meet to
review funding proposals and choose which ones to grant PKT to.

### How to make a funding proposal

Getting a proposal accepted is much like getting a pull request merged in a
project. You start by socializing what you want to do with the community
(try the [IRC](https://kiwiirc.com/nextclient/irc.freenode.net/pkt?nick=pktwow)
or [Matrix](https://riot.im/app/#/room/#pkt:m.trnsz.com) chats) and when you
have rough consensus, you move that conversation to a formal proposal.

To make a proposal, you must create a pull request to
[the ns-projects repository](https://github.com/pkt-cash/ns-projects) which
adds a new project markdown file as per the
[project template](https://github.com/pkt-cash/ns-projects/blob/master/projects/template.md)
and name it according to the naming convention defined in the repository readme.

Periodically The Network Steward will hold a meeting and decide on which
proposals should be funded. The minutes of these meetings are published in
the the ns-projects repository along with the projects and their status.

## Resources

* Telegram: https://t.me/pktproject
* Matrix: [#pkt:matrix.org](https://riot.im/app/#/room/#pkt:m.trnsz.com)
* IRC: [#pkt@freenode.net](https://kiwiirc.com/nextclient/irc.freenode.net/pkt?nick=pktwow)
* [Suggest an edit to this page](https://github.com/pkt-cash/www.pkt.cash/edit/master/steward/index.md)
* [Main](https://pkt.cash/)
  * **Steward** - you are here
    * [Vote](https://pkt.cash/steward/vote)
