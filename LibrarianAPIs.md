####1. Register a new Publisher Address
After user fills out fields on form and hits submit,  
a) **Florincoind** checks if users wallet has enough tokens;  
b) if False, first complete stage 4, and then continue on to stage 1d  
c) if True, continue on to stage 1d  
d) Create a signature by sending a *POST* api request to your local **Libraryd** *sign* endpoint ([http://localhost:41289/alexandria/v1/sign](http://localhost:41289/alexandria/v1/sign)) with this data:  
{"address":"*$florincoin_address*","text":"*$publishername*-*$florincoin_address*-*$unixtimestamp*000"}  
e) Store response as *$publishersignature*  
f) Announce your new Publisher by sending a *POST* api request to your local **Libraryd** *send* endpoint ([http://localhost:41289/alexandria/v1/send](http://localhost:41289/alexandria/v1/send)) with this data:  
{"alexandria-publisher":{"name":"*$publishername*","address":"*$florincoin_address*","timestamp":*$unixtimestamp*000,"bitmessage":"*$bitmessage_address*","emailmd5":"*$md5hashofemailaddress*"},"signature":"*$publishersignature*"}
g) A new transaction will be added to the next Florincoin block mined with the Publisher announcement in it's tx-message.  
h) A new publisher should appear in the results to *GET* api requests to your local **Libraryd** *publisher/all* endpoint ([http://localhost:41289/alexandria/v1/publisher/get/all](http://localhost:41289/alexandria/v1/publisher/get/all)) or to DLOA's web mirror of this endpoint ([http://libraryd.alexandria.media/alexandria/v1/publisher/get/all](http://libraryd.alexandria.media/alexandria/v1/publisher/get/all))

####2. Publish a new Artifact
After user adds their chosen files, fills out fields on form and hits submit,  
a) **Florincoind** checks if users wallet has enough tokens;  
b) If False, first complete stage 4, and then continue on to stage 2d  
c) If True, continue on to stage 2d  
d) **Librarian** local webserver uploads users chosen files to a new local folder,  
e) Add folder to the IPFS DHT by sending a *GET* api request to your local **Librarian** *ipfs/add/-r* endpoint ([http://localhost:8079/api/ipfs/add/$folderpath/-r](http://localhost:8079/api/ipfs/add/$folderpath/-r)) (Note, [Proper URL encoding](http://meyerweb.com/eric/tools/dencoder/) of the folderpath must be adhered to)  
f) The response will be a list of files added to IPFS and their hashes, store the last response, for the folder itself, as *$ipfsFolderHash*  
g) The files should now be found in the IPFS DHT, which can be confirmed by using a web browser to visit the URL [http://localhost:8080/ipfs/$ipfsFolderHash](http://localhost:8080/ipfs/$ipfsFolderHash) or any IPFS web gateway, such as DLOA's at [http://ipfs.alexandria.media/ipfs/$ipfsFolderHash](http://ipfs.alexandria.media/ipfs/$ipfsFolderHash).  
h) Create a signature by sending a *POST* api request to your local **Libraryd** *sign* endpoint ([http://localhost:41289/alexandria/v1/sign](http://localhost:41289/alexandria/v1/sign)) with this data:  
{"address":"*$florincoin_address*","text":"*$ipfsFolderHash*-*$florincoin_address*-*$unixtimestamp*000"}  
i) Store response as *$artifactsignature*  
j) Publishj your new Artifact by sending a *POST* api request to your local **Libraryd** *send* endpoint ([http://localhost:41289/alexandria/v1/send](http://localhost:41289/alexandria/v1/send)) with the data from the forms & ipfs files formatted according to this schema:[Alexandria media schema](https://docs.google.com/spreadsheets/d/1C3KNzQ-ec8Ma1ln5_Z-8609SkOM9TWoxmRprRU3Qe1M/edit#gid=0)  
k) A few new transactions will be added to the next Florincoin block mined with the Artifact announcement spread between their tx-messages.  
l) A new artifact should appear in the results to *GET* api requests to your local **Libraryd** *publisher/all* endpoint ([http://localhost:41289/alexandria/v1/media/get/all](http://localhost:41289/alexandria/v1/media/get/all)) or to DLOA's web mirror of this endpoint ([http://libraryd.alexandria.media/alexandria/v1/media/get/all](http://libraryd.alexandria.media/alexandria/v1/media/get/all))

####3. PinBotWizard

####4. TradeBot

####5. MineBot  

####6. HashReport

####7. Get data for a single artifact only
a) Send a *POST* api request to your local **Libraryd** *search* endpoint ([http://localhost:41289/alexandria/v1/search](http://localhost:41289/alexandria/v1/search)) or DLOA's web mirror of this endpoint [libraryd.alexandria.media/alexandria/v1/search](libraryd.alexandria.media/alexandria/v1/search) with this data:  
```{
  "protocol":"media",
  "search-on":"txid",
  "search-for":"$txidOfSpecificArtifact"
}```  

####8. Interact directly with the FLO blockchain over the web  
[http://flovault.dloa.io/wallet/](http://flovault.dloa.io/wallet/)  
Create Wallet: Send POST api to [http://flovault.dloa.io/wallet/create](http://flovault.dloa.io/wallet/create) Unknown schema to send password    
Login to Wallet: Send POST api to [http://flovault.dloa.io/wallet/readaccount](http://flovault.dloa.io/wallet/readaccount) Unknown schema to send identifier and password  
Get Wallet Balance: [http://flovault.dloa.io/wallet/getbalances/*$floaddress*](http://flovault.dloa.io/wallet/getbalances/*$floaddress*)  
Get Wallet Transactions: [http://flovault.dloa.io/wallet/addresstxs/*$floaddress*](http://flovault.dloa.io/wallet/addresstxs/*$floaddress*)  


