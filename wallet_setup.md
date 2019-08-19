# Wallet setup

Currently theres only a text based wallet for PKT and in order to install this
you need to install the PKT daemon then the wallet, then btcctl for interacting
with the wallet.

## Install golang

First, you need to install the go programming language, how to do it is mostly
outside the scope of this document but you can learn more here.

[https://golang.org/doc/install](https://golang.org/doc/install)

## Install the components

Once you have golang fully installed and set up, you can use the following
commands to install pktd, pktwallet and btcctl.

```
go get -u github.com/pkt-cash/pktd
go get -u github.com/pkt-cash/pktwallet
go get -u github.com/pkt-cash/pktd/cmd/btcctl
```

## Launch pktd

Now, you can launch pktd, for the purposes of this document, we will be running
everything with `x` as the RPC username and password.

```
pktd -u x -P x
```

This should show some output such as the following:

```
2019-08-16 13:47:56.526 [INF] SYNC: Processed 843 blocks in the last 10.01s (843 transactions, height 843, 2019-08-16 05:56:50 +0000 UTC)
```

This tells you that it's properly syncing the chain. In another window, you can
check the status of your node.

```
btcctl -u x -P x getinfo
```

The block number should be over 3000.

## Setup pktwallet

First you'll need to create a wallet

```
pktwallet -u x -P x --create
```

Then once it is created, launch it

```
pktwallet -u x -P x
```

Now in another window, you can interact with the wallet.
First you might want to create for yourself an address:

```
btcctl -u x -P x --wallet getnewaddress
```

Or get your current balance:

```
btcctl -u x -P x --wallet getbalance
```

To send PKT to somebody, you need to first unlock your wallet.
In this example, we're keeping the wallet unlocked for only 60 seconds,
you can change the number at the end to your liking.

```
btcctl -u x -P x --wallet walletpassphrase <password you used when creating wallet> 60
```

Then send cjd a 10 pkt tip.

```
btcctl -u x -P x --wallet sendtoaddress pP6Vh6GiL4HsMfcPby5xHQTyBUApd7mewg 10
```

For an exhaustive list of all the RPC calls you can make, use:

```
btcctl -l
```

## Resources

* Matrix: [#pkt:matrix.org](https://riot.im/app/#/room/#pkt:m.trnsz.com)
* IRC: [#pkt@freenode.net](https://kiwiirc.com/nextclient/irc.freenode.net/pkt?nick=pktwow)
* [Suggest an edit to this page](https://github.com/pkt-cash/www.pkt.cash/edit/master/wallet_setup.md)
* [Main](https://pkt.cash/)