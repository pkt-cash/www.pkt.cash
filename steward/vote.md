# Network Steward Vote

We believe it is a universal fact that any *unaccountable* authority, no
matter how benevolent, will eventually fall victim to corruption, inefficiency
or simple failure to innovate.

Because of this, we built in to the PKT blockchain solution in case that the
network steward is ever not fulfilling it's role.

Every holder of PKT is able to cast a *vote* to impeach the network steward
and allow a new one to take it's place. Impeachment is not an insignificant
event, it requires at least 50% of the total PKT in existance to explicitly
vote for it in order for it to take occur. However, if it does occur, what
follows is an automatic vote count and the network steward changes.

### How voting works

A vote consists one two parts, *VoteFor* and *VoteAgainst*, VoteAgainst is a
vote for impeachment while VoteFor is a vote for who should become network
steward in the event of an impeachment.

A network steward is represented as a
[transaction output script](https://en.bitcoin.it/wiki/Transactions#Output)
rather than a script encoded key. An easy way to get the script for a given
address is to pay some money to it and then explore the raw transaction and
copy the output.

Exploring a coinbase transaction we can see the output being paid to the
network steward `pkt1q6hqsqhqdgqfd8t3xwgceulu7k9d9w5t2amath0qxyfjlvl3s3u4sjza2g2`
and the script for this output is `0020d5c1005c0d4012d3ae2672319e7f9eb15a57516aeefabbbc062265f67e308f2b`

```
$ btcctl -u x -P x getrawtransaction 505d2750577a3d3c739c2a650ec0e03a7ddb1f81080c820ab1a317575020745b 1
{
  "hex": "01000000010000000000000000000000000000000000000000000000000000000000000000ffffffff10022913000b2f503253482f706b74642fffffffff03cac2a6ee0000000
01976a9147d9df4279212fd7def4c47abf2d5f3a6c6eaf4ae88ac362f5f3b00000000220020d5c1005c0d4012d3ae2672319e7f9eb15a57516aeefabbbc062265f67e308f2b000000000000
0000326a3009f91102ffff7f20c70542e4ca2363ce0149e845305f25564e7ce81e33411ad570df0f56f387462021cd01000000000000000000",
  "txid": "505d2750577a3d3c739c2a650ec0e03a7ddb1f81080c820ab1a317575020745b",
  "hash": "505d2750577a3d3c739c2a650ec0e03a7ddb1f81080c820ab1a317575020745b",
  "size": 203,
  "vsize": 203,
  "version": 1,
  "locktime": 0,
  "vin": [
    {
      "coinbase": "022913000b2f503253482f706b74642f",
      "sequence": 4294967295
    }
  ],
  "vout": [
    {
      "value": 40.0390625,
      "n": 0,
      "scriptPubKey": {
        "asm": "OP_DUP OP_HASH160 7d9df4279212fd7def4c47abf2d5f3a6c6eaf4ae OP_EQUALVERIFY OP_CHECKSIG",
        "hex": "76a9147d9df4279212fd7def4c47abf2d5f3a6c6eaf4ae88ac",
        "reqSigs": 1,
        "type": "pubkeyhash",
        "addresses": [
          "pGzmtW4Q2v4AWHcX8TYGqG5c1Eh5Ykg6fX"
        ]
      }
    },
    {
      "value": 9.9609375,
      "n": 1,
      "scriptPubKey": {
        "asm": "0 d5c1005c0d4012d3ae2672319e7f9eb15a57516aeefabbbc062265f67e308f2b",
        "hex": "0020d5c1005c0d4012d3ae2672319e7f9eb15a57516aeefabbbc062265f67e308f2b",
        "reqSigs": 1,
        "type": "witness_v0_scripthash",
        "addresses": [
          "pkt1q6hqsqhqdgqfd8t3xwgceulu7k9d9w5t2amath0qxyfjlvl3s3u4sjza2g2"
        ]
      }
    },
    {
      "value": 0,
      "n": 2,
      "scriptPubKey": {
        "asm": "OP_RETURN 09f91102ffff7f20c70542e4ca2363ce0149e845305f25564e7ce81e33411ad570df0f56f387462021cd010000000000",
        "hex": "6a3009f91102ffff7f20c70542e4ca2363ce0149e845305f25564e7ce81e33411ad570df0f56f387462021cd010000000000",
        "type": "nulldata"
      }
    }
  ],
  "blockhash": "c77d9026867de1455e573eb47bd3322548fd537b29ed9296a004a00f43d1da18",
  "confirmations": 3,
  "time": 1566221646,
  "blocktime": 1566221646
}
```

If we double-check by querying pktd to find out what is the network steward, we will
see that it shows the *script* that was paid to.

```
$ btcctl -u x -P x getnetworksteward
{
  "script": "0020d5c1005c0d4012d3ae2672319e7f9eb15a57516aeefabbbc062265f67e308f2b",
  "votesagainst": 0,
  "totalpossible": 21985819476623360
}
```

So if we wanted, for instance, to change the network steward to
`pGzmtW4Q2v4AWHcX8TYGqG5c1Eh5Ykg6fX`, we would want to vote for the corrisponding
script `76a9147d9df4279212fd7def4c47abf2d5f3a6c6eaf4ae88ac`, and of course we
probably want to vote *against* the current network steward as well.

## How to vote

Voting is done by configuring your wallet to vote, whenever you spend money, your
wallet will include a vote in every future payment of PKT which is made. If you
want to speed up the voting process, you can configure your wallet to vote and then
transfer all of your PKT to another wallet, in order to be sure it will all be voting.

To configure your wallet to vote for `pGzmtW4Q2v4AWHcX8TYGqG5c1Eh5Ykg6fX` and against
`pkt1q6hqsqhqdgqfd8t3xwgceulu7k9d9w5t2amath0qxyfjlvl3s3u4sjza2g2`, you would use the
following workflow:

```
$ btcctl -u x -P x --wallet getnetworkstewardvote
{}
$ btcctl -u x -P x --wallet setnetworkstewardvote default 76a9147d9df4279212fd7def4c47abf2d5f3a6c6eaf4ae88ac 0020d5c1005c0d4012d3ae2672319e7f
9eb15a57516aeefabbbc062265f67e308f2b
{}
$ btcctl -u x -P x --wallet getnetworkstewardvote
{
  "votefor": "76a9147d9df4279212fd7def4c47abf2d5f3a6c6eaf4ae88ac",
  "voteagainst": "0020d5c1005c0d4012d3ae2672319e7f9eb15a57516aeefabbbc062265f67e308f2b"
}
```

## Resources

* Matrix: [#pkt:matrix.org](https://riot.im/app/#/room/#pkt:m.trnsz.com)
* IRC: [#pkt@freenode.net](https://kiwiirc.com/nextclient/irc.freenode.net/pkt?nick=pktwow)
* [Suggest an edit to this page](https://github.com/pkt-cash/www.pkt.cash/edit/master/steward/vote.md)
* [Steward](https://pkt.cash/steward)
* [Main](https://pkt.cash/)