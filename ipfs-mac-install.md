##IPFS Installation Instructions for Mac  

####1) Download IPFS
visit [http://ipfs.io/docs/install](http://ipfs.io/docs/install) and download a current prebuilt package of IPFS for Mac OS X  
Unzip the downloaded archive   

####2) Install it into your bin path
In a new terminal window `cd` into your recently unzipped `ipfs` folder  
Now input `mv ipfs /usr/local/bin/ipfs` to move the ipfs binary to where the system can execute it   

<pre><code>
computer:~$ user cd ~/Downloads/ipfs/ 
computer:ipfs user$ ls
dist	ipfs
computer:ipfs user$ mv ipfs /usr/local/bin/ipfs
computer:ipfs user$ ls
dist
</code></pre>

And then try `ipfs version` and it will return it's version number if correctly installed  

<pre><code>
computer:ipfs user$ ipfs version
ipfs version 0.3.4
</code></pre>   
Now init the repo by entering `ipfs init`   
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
  
####3) Launch the daemon  
Enter `ipfs daemon` to launch the IPFS daemon - *note*: this is a necessary step to stream media in Alexandria.   
