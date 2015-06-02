##Alexandria Installation Instructions  

####1) Install IPFS
####note, this must be done to play content in Alexandria  
visit [http://ipfs.io/docs/install](http://ipfs.io/docs/install) and download a current prebuilt package of IPFS for Mac OS X  
Unzip the downloaded archive   
in a terminal window `cd` into your recently unzipped `ipfs` folder  
Now enter `mv ipfs /usr/local/bin/` to move the ipfs binary to where the system can execute it   
Now init the repo by trying `ipfs init`   
<pre><code>initializing ipfs node at /Users/jbenet/.go-ipfs
generating 4096-bit RSA keypair...done
peer identity: Qmcpo2iLBikrdf1d6QU6vXuNb6P7hwrbNPW9kLAH8eG67z
to get started, enter:

  ipfs cat /ipfs/QmPXME1oRtoT627YKaDPDQ3PwA8tdP9rWuAAweLzqSwAWT/readme </code></pre>   

Note the hash there may differ. If it does, use the one you got.   
Now try:
`ipfs cat /ipfs/QmPXME1oRtoT627YKaDPDQ3PwA8tdP9rWuAAweLzqSwAWT/readme`

And you should get something like this:
<pre><code>Hello and Welcome to IPFS!

██╗██████╗ ███████╗███████╗
██║██╔══██╗██╔════╝██╔════╝
██║██████╔╝█████╗  ███████╗
██║██╔═══╝ ██╔══╝  ╚════██║
██║██║     ██║     ███████║
╚═╝╚═╝     ╚═╝     ╚══════╝

If you're seeing this, you have successfully installed
IPFS and are now interfacing with the ipfs merkledag!</code></pre>
  
do `ipfs version` and it will return it's version number if correctly installed.  
do `ipfs daemon` to launch the IPFS daemon - necessary step to stream media in Alexandria.   

####2) Download Alexandria-nightly-20150528-69e346b-OSX.zip
It can be found [here](https://blocktech.slack.com/files/devon/F0534V9LQ/alexandria-nightly-20150528-69e346b-osx.zip)  
Unzip the downloaded archive and save the folder `Alexandria-nightly-20150528-69e346b-OSX` to a directory of your choosing.

####3) Download Florincoin wallet
####note, you can skip steps 3-5 if you just wish to browse the library, but they must be done in order to send tips and publish content in Alexandria  
Visit [florincoin.org](http://florincoin.org/) to download the current OSX build.  There is a blockchain bootstrap available to download if you'd like to speed up the initial sync.  
Open the wallet and let it fully sync before moving on to the next step. This may take a few hours (or a few days if your network is slow)   

####4) Enable RPC-access to your Florincoin-QT wallet with a florincoin.conf file    
Once your Florincoin-QT wallet has fully synced, quit it and navigate in the Finder to `~/Library/Application Support/Florincoin/`  
  
Create a new config file called `florincoin.conf` that includes the following code block.  
<pre><code>rpcuser=username
rpcpassword=password
rpcallowip=127.0.0.1
rpcallowip=192.168.*.*
rpcport=18322
server=1
daemon=1
txindex=1</code></pre>

Remember, it is **extremely important** that you change the username and password to something secure. Store this username and password somewhere secure but retrievable, as you will need it to access wallet functions within Alexandria. Save `florincoin.conf` and relaunch the Florincoin-QT wallet.   
**note:** the Alexandria library is indexed in the Florincoin blockchain, so if you are interested in browsing it in an entirely peer-to-peer manner, you must be running a synced Florincoin-QT wallet.

####5) Run the Alexandria library daemon
In terminal, do `export F_USER=username`, then do `export F_TOKEN=password`.  Remember to change the username and password to what you used in `florincoin.conf`.  
Then in terminal, `cd` into `Alexandria-nightly-20150528-69e346b-OSX`., then do `./libraryd` to launch Alexandria's library daemon. (note, this must be done to send tips and publish content in Alexandria)

####6) Enter the Decentralized Library of Alexandria 
Open `Alexandria.app` and enjoy the library.
