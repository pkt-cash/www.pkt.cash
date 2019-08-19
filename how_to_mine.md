# How to mine

In order to begin mining, you'll probably want to have your
[wallet](https://pkt.cash/wallet) setup. Once you have a wallet and an address
configured, you will need to setup PacketCrypt for mining.

## How PKT mining works

PKT chain uses a unique PoW algorithm known as
[PacketCrypt](https://github.com/cjdelisle/PacketCrypt). PacketCrypt is designed
such that efficient mining is achieved only if miners *communicated* between one
another, since this communication is potentially a lot of data, PacketCrypt is
thought to be *bandwidth hard*.

PKT mining consists of two distinct stages, the first stage is known as
*announcement mining*. Announcements are small 1KB proofs of some work having been
done. Any miner who can then prove that they had the announcement in memory at the
time they were mining is elligable for a discount on the amount of work which they
need to do to mine a block. Importantly, an announcement miner can optionally
attach some additional *content* to an announcement which, due to it's value to
block miners, is sure to be spread far and wide.

An announcement is essentially a broadcast message, sent out to anybody who cares
to listen.

The second stage is of course block mining, the type of mining which we're all
familiar with. In the PacketCrypt system, a block miner needs to download lots of
announcements in order to get the largest possible discount on the work that they
need to do.

## Setup PacketCrypt

If you're using Windows, please install Ubuntu from the app store, native
windows support is not here yet.

In order to use PacketCrypt, you will need a compiler, libcrypto, libsodium
and a recent version of nodejs. For nodejs we recommend using [nvm.sh](http://nvm.sh)
to install.

### Ubuntu

In order to build on Ubuntu, you will need to enable to universe repository
to be able to install `autoconf-archive`.

```
sudo add-apt-repository universe
sudo apt-get update
sudo apt install pkg-config libsodium-dev autoconf-archive git libssl-dev build-essential
```

Once the requirements are installed, get the source code and build it:

```
git clone https://github.com/cjdelisle/PacketCrypt
cd PacketCrypt
./autogen.sh
./configure
make
npm install
```

### Apline Linux

Make sure you have the
[community](https://wiki.alpinelinux.org/wiki/Enable_Community_Repository)
repository enabled.

```
sudo apk update
sudo apk add nodejs npm autoconf automake autoconf-archive build-base git libsodium-dev openssl-dev
```

Once the requirements are installed, get the source code and build it:

```
git clone https://github.com/cjdelisle/PacketCrypt
cd PacketCrypt
./autogen.sh
./configure
make
npm install
```

### Apple OSX

Make sure you have [homebrew](https://brew.sh) installed first.

```
brew install libsodium pkg-config autoconf-archive openssl
```

Once the requirements are installed, get the source code and build it:

```
git clone https://github.com/cjdelisle/PacketCrypt
cd PacketCrypt
./autogen.sh
export PKG_CONFIG_PATH="$PKG_CONFIG_PATH:`echo /usr/local/Cellar/libsodium/*/lib/pkgconfig`"
export PKG_CONFIG_PATH="$PKG_CONFIG_PATH:`echo /usr/local/Cellar/openssl/*/lib/pkgconfig/`"
./configure
make
npm install
```

## Mining

Once you've completed building PacketCrypt, you can begin mining. There are two
types of mining available and pools should typically make about 50% of their payment
to their announcement miners and 50% of their payment to their block miners.

Devices with low available memory and/or slow internet connection should prefer to
do announcement mining while devices with high speed internet and lots of available
memory may prefer block mining.

These examples have you mining in the [GridFinity](https://gridfinity.com) mining pool
and also **giving your coins to cjd**, make sure you update the `--paymentAddr`
appropriately unless you wish to make a donation.

Announcement mining:

```
node ./annmine.js --threads 2 --paymentAddr=pDSxcZunaUSUSxHrL6r8zpGJvoEropJ3Es http://pool.gridfinity.com/master
```

Block mining:

```
node ./blkmine.js --threads 2 --paymentAddr=pDSxcZunaUSUSxHrL6r8zpGJvoEropJ3Es http://pool.gridfinity.com/master
```

## Resources

* Matrix: [#pkt:matrix.org](https://riot.im/app/#/room/#pkt:m.trnsz.com)
* IRC: [#pkt@freenode.net](https://kiwiirc.com/nextclient/irc.freenode.net/pkt?nick=pktwow)
* [Suggest an edit to this page](https://github.com/pkt-cash/www.pkt.cash/edit/master/how_to_mine.md)
* [Main](https://pkt.cash/)