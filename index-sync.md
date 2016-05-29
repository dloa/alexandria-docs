###Syncing the Library Index for Lite-Clients

The Florincoin blockchain stores, as a sub-set of it's total data, Alexandria's library index. It is composed of all transaction messages with protocol matching tx-comments. Each libraryd node generates its own local copy of the index by parsing the entire blockchain looking for appropriate tx-comments. The database file it creates is stored in `<libraryd-application-folder>/bin/sync89.db` as a sqlite database. Libraryd does all of its read and search functions against this file, not the blockchain itself.  

It is worth noting that as of May 27, 2016, the sync89.db file is 127MB, whereas the Florincoin blockchain is 923MB. So only about 15% of the blockchain data is applicable. The below is a proposed method to allow a form of lite client to sync only `/db/sync89.db` with other nodes to give them full read access to the library index, without having to sync the entire blockchain. To verify the authenticity of individual entries in the index, the client could then verify that they are, in fact, in the florincoin blocks that they claim to be, either by asking a web-hosted Librryd client to verify it, or by asking an ethereum node with direct access to the florincoin to verify it for a payment.  

####Historians

Alexandria has a class of users it calls `Historians`. These users create a registration message in the index to announce themselves, and then they proceed to store various history archive data-points in the index, for them, or anyone, to later use as they see fit. Some `Historians` will be storing an archive we call `blockchain-data` for florincoin, and some will be doing so for other blockchains, like Bitcoin and Ethereum. The `blockchain-data` archive contains the following information:
<pre><code>
{
  "alexandria-data":{
    "bdFLO-data-point":{
        "block": "florincoin_block",
        "historian":"historian-pub-address",        
        "url_of_node_or_pool": "historian_miner_url",
        "miningrigs_last10": "btc_per_sCryptMHs_per24h",
        "node_hashrate": "historian_miner_hashrate",
        "fbd_networkhashps": "florincoin_net_hashrate",
        "fmd_weighted_btc": "flo_market_avg_btc",
        "fmd_weighted_usd": "flo_market_avg_usd"
        },
      "signature":"historian-sig-of-data-point"
    }
}
</code></pre>

From this data, one can calculate an estimated cost-basis for that node to mine a given number of tokens. When this data is added to the index by including it in the tx-comment of a coinbase of newly mined coins, it means that the node which won that particular block looked up that data themselves and then exerted the necessary mining effort to win the block. This means that it is possible for any user to be able to actively calculate the cost being expended by various historian nodes to include the data they find into the blockchain compared to others and use that information to judge the relative trustworthiness to assign to each `historians` data-points, and this has a great deal of significance to the `tradebot` tool, but that is a subject for another paper. For the purposes of this paper, we'll keep our focus on another service that historian nodes provide, helping to sync the library index database for lite-client nodes.  

When a `historian` announces themselves, they provide the public address of the blockchain key they intend to use to sign all of their future data-points, to allow for tracking and payments for their efforts. Some will also provide their IPNS public address as well. This address can be used with IPFS to resolve to an IPFS address - the IPNS can be updated regularly to point to new IPFS addresses, so together they work as a means of decentralized name resolution to a data set being regularly kept up to date. Any `historian` nodes who wish to provide Alexandria index-related services to users of other blockchains will also register themselves with a message in those blockchains - in some cases there is a method built into the blockchain to add arbitrary data, and in other cases functions like `OpReturn` will be used to accomplish this.  

####Adding the Index database to IPFS

Those `historian` nodes who wish to provide Alexandria index-related services to users of other blockchains will then regularly perform the following function:  
<pre><code>
ipfs add -r [path-to-index-db]
result: [ipfs-hash-of-index-db]
ipfs name publish /ipfs/[ipfs-hash-of-index-db]
result: Published to [ipns-hash]: [ipfs-hash-of-index-db]
</code></pre>

The process of locating a recent Index db file would simply require knowing something about one or serveral `historian` nodes. If someone knows their historian-pub-address, they could search any of the blockchains which they have registered on to look up their IPNS address. If someone knows a `historian` nodes IPNS address, they can perform the following function to find their most recently added Index database:  
<pre><code>
ipfs name resolve /ipfs/[ipns-hash]
result: [ipfs-hash]
ipfs ls [ipfs-hash]
result: [list-of-ipfs-files]

Each Publisher IPNS address can be resolved and their Index database found, and by comparing multiple results, a user can find the most common one between them, which will in most cases represent the most up-to-date version of the index database.  

Lite-clients will thus be able to find a recent copy of the Index database using one of the following methods:  

1) Front end providers may chose to hard-code one or several Historian IPNS addresses into their client, most applicable if the provider runs its own `historian` pool. 
2) By searching the blockchain for `historian` registration messages, they can find one or several Historian IPNS addresses.  

####Verifying individual blocks for lite-clients  
As described above, there will be two methods for lite-clients to manually verify that an artifact or data-point in the Index is actually stored in the blockchain, by asking a web-hosted Libraryd node to verify it, or by asking an ethereum node with direct access to the florincoin to verify it for a payment.  

####Web-Hosted Verifiers
Web-hosted Libraryd nodes can optionally run an API endpoint which allows them to receive requests that include the tx-id of the artifact or data-point which the user is asking to verify. The endpoint will then return their findings from their own indexed copy of the blockchain as the API response to the user. Because the user does not send them their expected findings, the node has no way to know whether its response will match what the user has in their lite-client or not, which means their motivation to send maliciously altered data back will be reduced. Note that this verification method could be prone to DDoS attacks if the API endpoint is permissionless, so most nodes will probably require API key registration.  

Ethereum users can optionally verify these requests by syncing both the Ethereum and Florincoin blockchains and running a fork of the software BTCRelay which we'll be building. This provides a mechanism whereby multiple users can compete for the payments from users requesting verification by watching for requests, using FLORelay to look up the appropriate data to provide to the end user, and one of the users who submitted the most common/popular answer will receive the payment. Between this mechanism and other forms of gamified returns for providing blockchain data, we beleive enough financial incentive will be provided for there to continually be a good sized swarm of nodes running full nodes of each blockchain involved.  
