###Known issues in current ALEXANDRIA build  

**v.0.4.1 alpha (20150528)**  
* **MAJOR BUG:** When a user clicks Tip on a media detail page, they are given 4 options for amount, 3 suggested amounts and a custom field. Tips sent using one of the 3 suggest amounts work properly, but custom amount field is not being calculated into accurate crypto amounts at this time (resulting in significantly more FLO than the requested USD amount), so please avoid this function until this is resolved  
* **MAJOR BUG:**  Users can send each other Florincoin from within the wallet view, but USD-FLO amounts are being inaccurately calculated, so please avoid this feature until this is resolved  
* Before attempting to use a Pay-What-You-Want Wall, users must log into their wallet through the user menu or by attempting to send a tip  
* Magnet button on media detail pages (for Downloading media) does not work with IPFS files  
* Get balance after wallet actions in Mac build sometimes crashes Alexandria  
* VLC plugin not fully implemented in WINDOWS and LINUX  
* "Back" button is sometimes unreliable on first click  
* PDF embed not yet working  
* No linux Florincoin-QT wallet exists  
* No settings UI  
* Media loading status and seed count indicators not yet implemented  
* Partial search on Publisher for Name does not return correct results  
    
###Alpha Version Changes  
**v.0.4.1 alpha (20150528)**  
* Users can now publish media! (requires an up to date Florincoin-QT wallet and user must be running Alexandria protocol binary (currently Mac only)  
* Media files are now handled by the IPFS DHT instead of the bittorrent mainline DHT, so all users must be running the IPFS daemon to stream embedded video and audio files  
* No more memory leak!  
* Users can now trade Bitcoin for Florincoin directly in their Alexandria wallet!  
* Removed labels from FLO address dropdowns  

**v.0.4 alpha (20150413)**   
* "Pay-What-You-Want wall"  
* Bitcoin-QT wallet auth + tip sending  
  
**(20150412)**
* Bug fixes  
* Alert modals for Publisher + Artifact submission  
  
**(20150410)**  
* Corrected address account labels  
* Add Media UX/UI tightening  
  
**(20150409)**  
* Publisher Address select options on Add Media  
* Bitcoin address on Add Publisher + Add Media  
* Wallet login prompt on Add Media  

**(20150327)**  
* Wallet USD/FLO inputs  
* Updated Alexandria logos  
* USD amount input checks and other bug fixes  

**(20150326)**  
* Send FLO amount round to 10e8  
* Fixed tip custom input error checking and parsing as USD value  
* Bug fixes  

**(20150325)**  
* Send FLO confirmation and input check  
* Tip with Florincoin-QT wallet  
* Publisher QR code and view styles  

**(20150324)**  
* Wallet Create Address and Send FLO  
* Initial Bitcoin-QT Wallet integration  
* New Publisher form Florincoin-QT wallet integration  

**(20150322)**  
* Node module 'bitcoin' added for JSON-RPC with FLO wallet  
* Wallet login. Pulls FLO balance (calculates USD) and addresses.  
* Wallet address QR code generation  

**(20150320)**  
* Added VLC web plugin and player  

**(20150319)**  
* Added module heading to search results  
* Added media deactivation interface and message signing/post functions  
* Moved Publisher FLO address and Torrent hash input to first Add Media tab and removed extraneous tabs  
* Added BTC and FLO address to About page for development support  

**(20150318)**    
* Go To Location with URL or plain location/view data (txId, address, view title, etc)  
      * Full Url routes to local app location or current web host  
* Cleaned extraneous bugs in Windows build  
* Cleaned CSS  

**(20150317)**  
* Embed for Book  
* Initial wallet UI build (prep for Florincoind integration)  

**(20150316)**  
* Rewrote router function  
* Search and breadcrumb function build-out and bug fixes  
* Simple "Back" navigation button  
* Go To Location modal feature built and operational with Share paths  
* Fixed Windows header element malfunctions  
* Windows streamer support  

**(20150315)**  
* Fixed bugs in previous build  
* Added media genres select options per media type  
* Icon design tweaks (still not quite right)  
* Changed front view to Browse Media view  
