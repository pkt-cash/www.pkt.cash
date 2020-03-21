# Wallet setup

Currently theres only a text based wallet for PKT and in order to install this
you need to install the PKT daemon then the wallet, then btcctl for interacting
with the wallet.

## Install golang

First, you need to install the go programming language, how to do it is mostly
outside the scope of this document but you can learn more here.

[https://golang.org/doc/install](https://golang.org/doc/install)

## Install git

Next you will need to make sure you have git installed. The first thing to do
is check whether you have it installed already:

```
git version
```

If it prints something like `git version 2.21.1`, you're in luck and you can
continue. If it prints something more like `command not found: git` then you'll
need to install it.

Installation will depend on your system, for debian/ubuntu like systems you will
want `sudo apt install git` and for OSX with homebrew, you'll want `brew install git`.

## Install the components

Once you have golang and git fully installed and set up, you can use the following
commands to install pktd, pktwallet and btcctl.

```
git clone github.com/pkt-cash/pktd
cd pktd
./do
```

## Launch pktd

Now, you can launch pktd:

```
./pktd
```

This should show some output such as the following:

```
2019-08-16 13:47:56.526 [INF] SYNC: Processed 843 blocks in the last 10.01s (843 transactions, height 843, 2019-08-16 05:56:50 +0000 UTC)
```

This tells you that it's properly syncing the chain. In another window, you can
check the status of your node.

```
./btcctl getinfo
```

Check the [Block Explorer](https://newalpha-pkt-explorer.cjdns.fr/) to see the most recent block.

## Setup pktwallet

First you'll need to create a wallet

```
./wallet --create
```

Then once it is created, launch it

```
./pktwallet
```

Now in another window, you can interact with the wallet.
First you might want to create for yourself an address:

```
./btcctl --wallet getnewaddress
```

Or get your current balance:

```
./btcctl --wallet getbalance
```

To send PKT to somebody, you need to first unlock your wallet.
In this example, we're keeping the wallet unlocked for only 60 seconds,
you can change the number at the end to your liking.

```
./btcctl --wallet walletpassphrase <password you used when creating wallet> 60
```

Then send cjd a 10 pkt tip.

```
./btcctl --wallet sendtoaddress pP6Vh6GiL4HsMfcPby5xHQTyBUApd7mewg 10
```

For an exhaustive list of all the RPC calls you can make, use:

```
./btcctl -l
```

## Resources

* Telegram: https://t.me/pktproject
* Matrix: [#pkt:matrix.org](https://riot.im/app/#/room/#pkt:m.trnsz.com)
* IRC: [#pkt@freenode.net](https://kiwiirc.com/nextclient/irc.freenode.net/pkt?nick=pktwow)
* [Suggest an edit to this page](https://github.com/pkt-cash/www.pkt.cash/edit/master/wallet_setup.md)
* [Main](https://pkt.cash/)
