##Library Daemon (libraryd) Installation Instructions for Linux 64-bit (Tested on Ubuntu 14.04)  

####1) Download the latest build of libraryd
It can be downloaded by clicking [here](https://slack-files.com/T0457K60S-F06U6UPNE-0a2f3319f3)  
Unzip it to extract the binary `libraryd`   

####2) Make sure your Florincoin wallet is fully synced and that you have enabled RPC-access to your wallet with a florincoin.conf file. If you have not done so, click [here](https://github.com/dloa/alexandria-docs/blob/master/florincoin-lin64-install.md) for instructions.

####3) Start the daemon
In a new terminal window, enter `export F_USER=username`, and then `export F_TOKEN=password`.  These fields must match the username and password that you used in `florincoin.conf`.  
In the same terminal window, `cd` into the directory that contains the `libraryd` binary, and enter `./libraryd` to start Alexandria's library daemon.

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

####4) Decentralize  
Once this has reached 100%, open your `Alexandria` browser and click the word `Gateway` to switch to `local` mode and you'll be browsing the library decentralized...ly.
