###Known issues in current ALEXANDRIA build  

**v.0.4.2 alpha 2015-06-19**  
* Before attempting to use a Pay-What-You-Want Wall, users must log into their wallet through the user menu or by attempting to send a tip  
* Get balance after wallet actions in Mac build sometimes crashes Alexandria  
* VLC plugin not fully implemented in WINDOWS and LINUX  
* "Back" button is sometimes unreliable on first click  
* PDF embed not yet working  
* Download link (magnet icon) does not work  
* No settings UI  
* Media loading status indicator not yet implemented  
* Partial search on Publisher for Name does not return correct results  
    
###Alpha Version Changes  
**v.0.4.2 alpha 2015-06-19**  
* Linux-64 Florincoin-QT and Florincoind wallet released - Linux users can now publish!
* "Movies" artifact type re-added
* PDF type provides a download button
* "New Florincoin Address" button works

**v.0.4.2 alpha 2015-06-09**  
* API defaults set to gateway with switch to local  
  
**2015-06-04**  
* Things view now includes an embed of the thing's poster image (ipfs hash of the image should be included in the Poster Frame Filename field of the submission)  
* Recipes view now includes an embed of the recipe  
* Bug squashed: using the custom field when sending a tip sent the wrong amount  
* Bug squashed: sending Florincoin from the wallet view sent the wrong amount  

**v.0.4.1 alpha 2015-05-28**  
* Users can now publish media! (requires an up to date Florincoin-QT wallet and user must be running Alexandria protocol binary (currently Mac only)  
* Media files are now handled by the IPFS DHT instead of the bittorrent mainline DHT, so all users must be running the IPFS daemon to stream embedded video and audio files  
* No more memory leak!  
* Users can now trade Bitcoin for Florincoin directly in their Alexandria wallet!  
* Removed labels from FLO address dropdowns  

**v.0.4 alpha 2015-04-13**   
* "Pay-What-You-Want wall"  
* Bitcoin-QT wallet auth + tip sending  
  
**2015-04-12**
* Bug fixes  
* Alert modals for Publisher + Artifact submission  
  
**2015-04-10**  
* Corrected address account labels  
* Add Media UX/UI tightening  
  
**2015-04-09**  
* Publisher Address select options on Add Media  
* Bitcoin address on Add Publisher + Add Media  
* Wallet login prompt on Add Media  

**2015-03-27**  
* Wallet USD/FLO inputs  
* Updated Alexandria logos  
* USD amount input checks and other bug fixes  

**2015-03-26**  
* Send FLO amount round to 10e8  
* Fixed tip custom input error checking and parsing as USD value  
* Bug fixes  

**2015-03-25**  
* Send FLO confirmation and input check  
* Tip with Florincoin-QT wallet  
* Publisher QR code and view styles  

**2015-03-24**  
* Wallet Create Address and Send FLO  
* Initial Bitcoin-QT Wallet integration  
* New Publisher form Florincoin-QT wallet integration  

**2015-03-22**  
* Node module 'bitcoin' added for JSON-RPC with FLO wallet  
* Wallet login. Pulls FLO balance (calculates USD) and addresses.  
* Wallet address QR code generation  

**2015-03-20**  
* Added VLC web plugin and player  

**2015-03-19**  
* Added module heading to search results  
* Added media deactivation interface and message signing/post functions  
* Moved Publisher FLO address and Torrent hash input to first Add Media tab and removed extraneous tabs  
* Added BTC and FLO address to About page for development support  

**2015-03-18**    
* Go To Location with URL or plain location/view data (txId, address, view title, etc)  
      * Full Url routes to local app location or current web host  
* Cleaned extraneous bugs in Windows build  
* Cleaned CSS  

**2015-03-17**  
* Embed for Book  
* Initial wallet UI build (prep for Florincoind integration)  

**2015-03-16**  
* Rewrote router function  
* Search and breadcrumb function build-out and bug fixes  
* Simple "Back" navigation button  
* Go To Location modal feature built and operational with Share paths  
* Fixed Windows header element malfunctions  
* Windows streamer support  

**2015-03-15**  
* Fixed bugs in previous build  
* Added media genres select options per media type  
* Icon design tweaks (still not quite right)  
* Changed front view to Browse Media view  
