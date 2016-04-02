##Florincoin-QT Installation Instructions for Mac  

####1) Download Florincoin wallet
Visit [florincoin.org](http://florincoin.org/) to download the current OSX build. Mount the disk image and copy `Florincoin-QT` into your Applications folder. Open it so that it creates the necessary folders for the next step, wait about a minute, and then quit and move on to step 2.  

####2) Enable RPC-access to your Florincoin-QT wallet with a florincoin.conf file    
In the Finder, pull down the `Go` menu and chose `Go to Folder...` and paste this path `~/Library/Application Support/Florincoin/`  
  
Create a new config file called `florincoin.conf` that includes the following code block (Or download [this sample file](http://gateway.ipfs.io/ipfs/QmUFdbi4CTXAyqGi1ouKYcwFL2dTSqVPE4TzXUDcQMjPCo/)).   
<pre><code>
rpcuser=username
rpcpassword=password
rpcallowip=127.0.0.1
rpcallowip=192.168.0.0/16
addnode=54.209.141.153
rpcport=18322
server=1
daemon=1
txindex=1</code></pre>

Remember, it is **extremely important** that you change the username and password to something secure. Store this username and password somewhere secure but retrievable, as you will need it to access wallet functions within Alexandria. Save `florincoin.conf` - Please note, if you create this file with textedit, it may attempt to hide a .txt extension on the file, which will cause it to fail. Assuming the file has the proper name on it, relaunch the Florincoin-QT wallet and **let it fully sync**. This may take a few hours (or a few days if your network is slow)   

###Optional: bootstrap with IPFS
Downloading the full Florincoin blockchain takes a while. If you have IPFS install
ed, you can speed this process up dramatically. To do this:

a.) Navigate to your florincoin directory
b.) Make sure your IPFS daemon is running, and run the following command:
$ ipfs name resolve QmfYRn7eAHz9DtzCz8oVYjC6Y7geUSYBkz6iG3CVdb56W9
ipfs will output a hash.
c.) copy hash, and paste into the command:
$ ipfs get [copied hash]
4.) feel free to delete bootstrap.dat.old after the blockchain sync has finished.


####3) Send a comment!  
Open your `Alexandria.app` browser, select `Wallet` from the user menu, and enter the username and password you used in your `florincoin.conf` file. You Alexandria browser now has access to your wallet, so you can send and receive Flo, you can use `trade-bot` to exchange BTC for FLO, and you can include comments with any tips you send to publishers!
