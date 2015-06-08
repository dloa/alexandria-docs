##Alexandria Installation Instructions  

####1) Download Alexandria-daily-20150608-282cc6a-OSX.zip
If you are in the alpha testers Slack chatroom, it can be downloaded by clicking [here](https://blocktech.slack.com/files/devon/F0608DCG7/alexandria-alpha-20150604-osx.zip)  
If you are not in the chatroom but were given another link, use it instead. If you think you're in the chatroom,  but this link doesn't work, you aren't yet in the room; either accept the invite if one is still pending, or ask the Alexandria team for a new invite.   
Unzip the downloaded archive and save the folder `Alexandria-Alpha-20150604-OSX` to a directory of your choosing.

####That's it, that's all you have to do to browse and view content on the library. If you want to do so in an entirely p2p manner, or if you want to publish or send tips with comments, please continue on.   


####2) Install IPFS
####note, this must be done to play content in Alexandria  
visit [http://ipfs.io/docs/install](http://ipfs.io/docs/install) and download a current prebuilt package of IPFS for Mac OS X  
Unzip the downloaded archive   
in a terminal window `cd` into your recently unzipped `ipfs` folder  
Now input `mv ipfs /usr/local/bin/ipfs` to move the ipfs binary to where the system can execute it   
And then try `ipfs version` and it will return it's version number if correctly installed  

<pre><code>
computer:~$ user cd ~/Downloads/ipfs/ 
computer:ipfs user$ ls
dist	ipfs
computer:ipfs user$ mv ipfs /usr/local/bin/ipfs
computer:ipfs user$ ls
dist
computer:ipfs user$ ipfs version
ipfs version 0.3.4
</code></pre>   
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
  
do `ipfs daemon` to launch the IPFS daemon - necessary step to stream media in Alexandria.   

####3) Download Florincoin wallet
####note, you can skip steps 3-5 if you just wish to browse the library, but they must be done in order to send tips and publish content in Alexandria  
Visit [florincoin.org](http://florincoin.org/) to download the current OSX build.  

####4) Enable RPC-access to your Florincoin-QT wallet with a florincoin.conf file    
Navigate in the Finder to `~/Library/Application Support/Florincoin/`  
  
Create a new config file called `florincoin.conf` that includes the following code block (Or use the provided sample file). Please note, if you create this file with textedit, it may attempt to hide a .txt extension on the file, which will cause it to fail.  
<pre><code>
rpcuser=username
rpcpassword=password
rpcallowip=127.0.0.1
rpcallowip=192.168.*.*
rpcport=18322
server=1
daemon=1
txindex=1</code></pre>

Remember, it is **extremely important** that you change the username and password to something secure. Store this username and password somewhere secure but retrievable, as you will need it to access wallet functions within Alexandria. Save `florincoin.conf` and relaunch the Florincoin-QT wallet and **let it fully sync**. This may take a few hours (or a few days if your network is slow)   
**note:** the Alexandria library is indexed in the Florincoin blockchain, so if you are interested in browsing it in an entirely peer-to-peer manner, you must be running a synced Florincoin-QT wallet.

####5) Download and Run the Alexandria library daemon
Using IPFS, download the Alexandria library daemon by going to the following URL in your web browser: [http://localhost:8080/ipfs/QmYggCwuqqmGScfkYV6PaDhYK9hKdjdGrf13ewp1vU1MJC](http://localhost:8080/ipfs/QmYggCwuqqmGScfkYV6PaDhYK9hKdjdGrf13ewp1vU1MJC)   
A file called `QmYggCwuqqmGScfkYV6PaDhYK9hKdjdGrf13ewp1vU1MJC.zip` will be downloaded - unzip it to extract the folder `Alexandria_Library_Daemon`.
In a new terminal window, enter `export F_USER=username`, and then `export F_TOKEN=password`.  Remember to change the username and password to what you used in `florincoin.conf`.  
In the same terminal window, `cd` into the `Alexandria_Library_Daemon` folder, and enter `./libraryd` to launch Alexandria's library daemon. (note, this must be done to send tips and publish content in Alexandria)

<pre> <code>
$ export F_USER=[myusername]
$ export F_TOKEN=[mysuperpassword]
$ ./libraryd
           _                          _      _
     /\   | |                        | |    (_)
    /  \  | | _____  ____ _ _ __   __| |_ __ _  __ _
   / /\ \ | |/ _ \ \/ / _` | '_ \ / _` | '__| |/ _` |
  / ____ \| |  __/>  < (_| | | | | (_| | |  | | (_| |
 /_/    \_\_|\___/_/\_\__,_|_| |_|\__,_|_|  |_|\__,_|

 Blocktech                                       v0.1

Error opening configuration file.
Error decoding JSON from config file.
opening database ./db/sync89.db?cache=shared&mode=wrc... done opening DB!
creating tables and triggers if they don't exist...  done!
2015/06/02 10:38:58 Listening on port 41289

LOADED PROTOCOL: alexandria-media

current block chain height (rpc): 1214348
current max(block) from database: 1211818

syncing 2530 blocks between 1211819 and 1214348
first, checking past 256 blocks for reorg... 
> no reorg found!


sync at 0.00%
sync at 3.20%
sync at 7.15%
sync at 11.11%
sync at 15.06%
sync at 19.01%
sync at 22.96% </code></pre>

####6) Enter the Decentralized Library of Alexandria 
Open `Alexandria.app` and enjoy the library.

**Remember, in the current build, you must be running the `Florincoin-QT` wallet and `libraryd` to browse the Library index in a p2p manner, and you must be running `IPFS daemon` to stream or download content in the Library.**
