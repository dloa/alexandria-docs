### What is Alexandria, what is the Open Index Protocol and how are they related?  
The short answer:  
Alexandria is an application built for the Open Index Protocol, both of which our core team invented.  
The Open Index Protocol (OIP) is a blockchain media publishing & retrieval protocol
OIP uses a proof of work blockchain, [Florincoin](florincoin.org), to store & protect the data used for the index itself and it was designed so that transport protocols are interoperable, so that each application can support whichever ones it sees fit. by transport protocols, we specifically mean value transport protocols (ie, the payments function), and file transport protocols (ie, how files are stored and distributed). as such, it initially only allowed Florincoin tokens to used for payment, but in 2015 we added support for BTC and adopted the practice of having publishers dilineate their prices in fiat-terms. likewise, we initially used the bittorrent protocol for file transport, but in 2016 switched to IPFS, and plan to use the Filecoin DApp (essentially a decentralized market for paid storage and distribution) as *a* means of paying for media files to be stored/retrieved, but we aren’t expecting filecoin to be released for as long as a year, so the protocol has other means of ensuring all files published are persistent and retreivable.

### Ok, how does the Open Index Protocol work?
Watch this video...  
[![OIP Animation](https://gateway.ipfs.io/ipfs/Qmcv5uGL2wckxLsLyfW4PoiRoLuECe6ihTsNHGt67aQB4D/previewimage.png)](https://alexandria.io/browser/player/82135e)  

#### Now you should have the general idea:  
• **Publishers** start things out by sending their media files to the IPFS network, determining their distribution preferences, meta data and other details, and then sending all of this raw data, signed, to the Florincoin blockchain as a (or a series of) transaction message(s).  
• **Miners** confirm the validity of the transactions themselves and store the entire history of transactions in the blockchain.  
• **Open Index Protocol Full Nodes** confirm the validity of publish messages.  
• **End Users** ask for media files, and when necessary, exchange Bitcoin (or other cryptocurrencies) in exchange  

End users can chose to either be a full node themselves, by syncing the blockchain and running IPFS locally, or they can use a node hosted on the web. Since it runs more than just a plain relay node, but has a user interface which can facilitate sales of published content, we call this kind of node a [**Retailer**](https://api.alexandria.io/alexandria/v2/retailer/get/all). [Alexandria](https://alexandria.io/browser/) is the first retailer node, a streaming music focused platform called [Token-FM](https://token.fm/) is the second, and many more will come.  

### What is the stack for a retailer node?  
1. web server software of your choice
2. florincoin wallet daemon (or GUI) [project site](http://florincoin.org/) | [github](https://github.com/florincoin/florincoin)
3. open index protocol daemon [github](https://github.com/dloa/libraryd) (private repo, contact devon for access)
4. ipfs daemon [project site](https://ipfs.io/) | [github](https://github.com/ipfs)
5. pinbot [github](https://github.com/oipwg/pinbototron)
6. optional: bitcoin (and other coins) wallet daemon (or GUI) [github](https://github.com/bitcoin)
7. optional: p2p tradebot (to facilitate bitcoin <-> florincoin exchanges) [api](https://api.alexandria.io/docs/#tradebot) | [github](https://github.com/oipwg/oip-tradebot) (this is **not** the p2p version, this only trades between the retailer and end users currently)
8. MISSING! a javascript app/library that standardizes/normalizes the ~30 most commonly needed functions for a media front end
9. an interface for all of it

#### Here's a few interfaces:
Alexandria browser (react) [Hosted](https://alexandria.io/browser/) | [GitHub](https://github.com/dloa/browser-react)  
OIP lilBrowser (quasar) [GitHub](https://github.com/bitspill/lilbrowser)  
Alexandria Publisher (web) [Hosted](https://alexandria.io/publisher/) | [GitHub](https://github.com/dloa/publisher-web)  


### Who does the mining?
Anyone who wants to earn some money may have an incentive to mine a proof of work blockchain, which was part of Satoshi's brilliance - by that I mean that many of them don't know the nature of the contents of the blockchain they are mining, it just happened to have a good token price to mining difficulty per block reward ratio, which meant it received their hashes. However, for any Open Index Protocol users who specifically wish to mine the florincoin blockchain can use a tool we've built called Autominer to rent miners for them and then facilitate the exchange of their won tokens with other users who are need of some (like, for example, publishers who need to pay their publishing fees in Florincoin tokens).

#### Autominer on GitHub
[API](https://github.com/oipwg/autominer-api) | [Interface](https://github.com/oipwg/autominer-frontend) | [Electron App](https://github.com/oipwg/autominer-app)

The best part is that whenever an Autominer user wins a block, the current market data relating to Florincoin is written in their block reward transaction comment, archiving a snapshot of the current sCrypto rental market costs, the market exchange value of Florincoin on the exchanges where its traded, and the average value of BTC in USD. In exchange for providing this invaluable historical data, the Open Index Protocol facilitates the automatic trading of any Flo mined with this data at its cost plus a protocol calculated margin - sometimes (like when the price is spiking and mining hasn't yet caught up) it will allow quite high margins, in most conditions it will allow a reasonable margin of 20-30%, sometimes (like when the hash rate is very high and the price dips) it will only allow very low margins, and sometimes it will allow no margin at all, but it will always ensure the user gets their cost covered.  
This allows our Autominer app to be told to only mine when conditions are such that the user will receive a particular margin or higher (what end users will most likely do), or decide to mine at any margin (what companies who rely on the data in the index will most likely do).  

### What about "mining" files?
Yep, that's part of the plan too, but not yet implemented. For the time being, OIP uses a requirement that all Retailer nodes run the pinbot software which balances the storage needs of all of the files in the shared media layer across all retailers. When it comes online, we intend to use [Filecoin](http://filecoin.io/) to let Publishers pay for higher performance levels for their files, as the protocol will only ensure safe retreivability of all published files and cannot necessarily, on its own, ensure a good playback experience. However, since most retailers generally like for their users to have an enjoyable experience on their platform, we expect that simple commercial interests will ensure that all published files have enough pinners (IPFS for seeds) to provide an enjoyable experience to end users.  

#### API Docs?
Some of these may be out of date, so please ask if one isn't behaving as expected.   
[Hosted](https://api.alexandria.io/docs/) | [GitHub](https://github.com/dloa/slate)  

Missing end points:  
• Historian summary, for tradebot transactions (post endpoint, see [postman collection](https://github.com/dloa/alexandria-docs/blob/master/OIP.postman_collection.json.zip?raw=true))  
• searchTXcomment (post endpoint, see [postman collection](https://github.com/dloa/alexandria-docs/blob/master/OIP.postman_collection.json.zip?raw=true))  
• index summary [endpoint](https://api.alexandria.io/alexandria/v2/info)  
• calculate publish fee (post endpoint, see [postman collection](https://github.com/dloa/alexandria-docs/blob/master/OIP.postman_collection.json.zip?raw=true))  
• get all retailers [endpoint](https://api.alexandria.io/alexandria/v2/retailer/get/all)  
• get all promoters [endpoint](https://api.alexandria.io/alexandria/v2/promoter/get/all)  
• get all autominers [endpoint](https://api.alexandria.io/alexandria/v2/autominer/get/all)  
• get all autominer pools [endpoint](https://api.alexandria.io/alexandria/v2/autominerpool/get/all)

#### Dev Roadmap?
[Trello Board](https://trello.com/b/2178eVZH/next-release-v080) (Ask for an invite if you can't see this)

#### Dev Chat?
[Slack](dloaslack.bitspill.net) we're closing this down very soon, but its where everyone is currently  
[Rocketchat](https://chat.alexandria.io/channel/general)
