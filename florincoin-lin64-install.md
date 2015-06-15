##Florincoin Installation Instructions for Linux 64-bit (tested on Ubuntu 14.04)  

####1) Download Florincoin wallet
Click [here](https://slack-files.com/T0457K60S-F06B895SM-fba5b0403d) to download the rar package. Unzip and install Florincoin-QT and/or florincoind. Launch either of the wallets and let it sync for a few minutes - you want to make sure that the directoty `~/.florincoin/` has been created, but you do not need to let the wallet fully sync (in fact you shouldn't, as you'll need to do so at a later step and it will start over from the beginning at that time) before exiting it.   

####2) Enable RPC-access to your Florincoin-QT/florincoind wallet with a florincoin.conf file    
Navigate to `~/.florincoin/`  
  
Create a new config file called `florincoin.conf` that includes the following code block (or use the provided sample file). Please note, if you create this file with textedit, it may attempt to hide a .txt extension on the file, which will cause it to fail.  
<pre><code>
rpcuser=username
rpcpassword=password
rpcallowip=127.0.0.1
rpcallowip=192.168.*.*
rpcport=18322
server=1
daemon=1
txindex=1</code></pre>

Remember, it is **extremely important** that you change the username and password to something secure. Store this username and password somewhere secure but retrievable, as you will need it to access wallet functions within Alexandria. Save `florincoin.conf` and relaunch the Florincoin-QT (or florincoind) wallet and **let it fully sync**. This may take a few hours (or a few days if your network is slow)   

####3) Send a comment!  
Open your `Alexandria` browser, select `Wallet` from the user menu, and enter the username and password you used in your `florincoin.conf` file. You Alexandria browser now has access to your wallet, so you can send and receive Flo, you can use `trade-bot` to exchange BTC for FLO, and you can include comments with any tips you send to publishers!
