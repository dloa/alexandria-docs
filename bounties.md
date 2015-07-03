###Development Bounties
This is meant to be an exhaustive list of every peice of functionality planned for Alexandria 1.0 and the supplemental mechanisms that support the Alexandria eco-system. Some of these functions will be coded by Alexandria's staff devs and some can simply be forked from a developers existing code - if you are interested in working on anything in this list, please get in touch with the Alexandria team to discuss it in more detail before getting started.

####Alexandria Browser:
1. File browser in publishing UI, including drag and drop files functionality & IPFS "add" functionality
2. Better music playing interface (playlists, repeat, shuffle)
3. Artifact authorization-checker API - [details](https://github.com/dloa/alexandria-browser/issues/13)
4. "Pin this" button on artifact details UI (tells Librarian Module: Distributor to pin the file)
5. On/Off switch to auto-pin any artifacts downloaded during a browsing session function
6. Integrate [History Records visualizer](https://github.com/dloa/history_records_visualizer) into Alexandria UI/app
7. Upgrade [History Records visualizer](https://github.com/dloa/history_records_visualizer) to scrape datapoints from blockchain explorer & work w/ all History Records datasets (instead of just BTC Average and Flo-market-data as it does currently)
8. Inline comments on artifacts - [details](https://github.com/dloa/alexandria-browser/issues/10)
9. Fix download button on artifact details UI - [details](https://github.com/dloa/alexandria-browser/issues/6)
10. Fix embedding on artifact details for [PDFs](https://github.com/dloa/alexandria-browser/issues/5) & ebooks
11. Connect "buy more" button in Alexandria browser wallet to ShapeShift API
12. p2p messaging between users in-app (once this functionality has been forked into Florincoin wallet client)
13. Fork functionality from ProTip/WeTipCoins to locally track the content a user enjoys each week and auto-pay their "streaming subscription" to it's publishers
14. Browsing/purchase/tips history UI
15. Fix VLC plugin for Windows and Linux
16. Publisher's Artifacts UI (with deactivate button)
17. Finish social media historian (tweet archives)
18. Native app for Android (through gateways, or local librarian modules if possible)
19. Native app for iOS (through gateways)
20. "Couch interface" (and 32-bit build) for [BitSeed](http://www.bitseed.org)

####Alexandria Librarian:
1. Librarian (daemon loader/manager) tool-bar applet for Mac OSX, Windows, Linux 64-bit, Android (if possible), and Linux 32-bit (for [BitSeed](http://www.bitseed.org))
2. Fix Librarian Module: Historian so that it works with APIs that include `&` and `?` characters in their URIs - [details](https://github.com/dloa/librarian-module_historian/issues/1)
3. Upgrade Librarian Module: Historian to be able to capture web page archives on a periodic basis (to get plugged into the Internet Archive's Wayback Machine)
4. Subscribe to publisher (auto pin)
5. Librarian Module: Distributor

####Council of Librarians management app (or perhaps feature within Alexandria Browser app)
1. Blockchain voting process (including Living Articles of Organization document)
2. Multi-tiered chat platform (with comment links & permission-based chat-room access)
3. Decentralized ID system w/ reputation management and optional pseudonymity)
4. Blockchain: 100% premine, 1MM tokens, sidechain of Florincoin or 0% PoS
5. 

####Serverside Software
1. Florincoin web wallet (zero knowledge) based on Blockchain.info/LiteVault
2. Florincoin tipping bot for social media [Slack version can be found here](https://github.com/blocktech/slack_tipbot)

####Florincoin Wallet client
1. Fork in p2p messaging functionality [like Jumbucks wallets](http://getjumbucks.com/#wallets)
2. Upgrade to Bitcoin Core v0.10
3. Auto/scheduler keys backup feature
