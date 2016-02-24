###The Council of Librarians

####Problem:  
The Decentralized Library of Alexandria is designed to avoid all central points of failure. The application itself is able to do this by relying on decentralized technology, but there still exists a central point of failure in the entity responsible for its future development.

####Proposed Solution:  
An open source, encrypted peer-to-peer communication mechanism and a blockchain token that together allow users all around the world to participate in the management and future development of Alexandria in a decentralized, collaborative manner.   

####Summary Overview
A group of ~10 individuals is elected by all holders of the token to serve as the day-to-day managers of the development and marketing efforts for Alexandria. They communicate with each other via a P2P chat room in which only they can participate, but anyone in the world can observe. Normal day to day decision-making power is granted to the Chief Librarian, elected by all holders of the token. If the Chief Librarian or the Council of Librarians deem that a topic should be voted on by all token-holders, a vote will be held.

A second chat room shall also be made available for public discussion - users can pin things said by the management group into the public chat room so that they can comment and discuss decisions made by the management group. If a member of the public feels that a decision made by the management team should be challenged, they can propose a vote on the topic. If enough token holders second the vote, the vote is held by all holders of the token. Votes are made by sending tokens to oneself with their vote included in the transaction as a tx-comment. A “Living Articles of Organization” document will be drafted which contains all of the rules for voting, a description of how day to day decisions are handled, the maximum amounts that financial decisions must be below in order to be made without a vote and the minimum quorum needs for decisions of various types; ie, the decision to award a development bounty to a developer who submits some code may only require a 15% quorum of token holders, but the decision to change the priority of feature development may require a 50% quorum of token holders. Each article of the constitution, and all sections and sub-sections in it can be amended by vote.

The target number of members on the Council of Librarians is determined by popular vote, and from it is extracted a minimum number of tokens that a user must either personally own or have proxied to them by other users (more info on this in the Elections process section below) to be on the Council. For example, to have 10 users on the Council of Librarians, a minimum amount of 9% of the total tokens must be controlled by each user.



####Voting Process
When it has been decided that a vote will be held, the token-holder who requested the vote will publish the question to be voted upon by sending a transaction to themselves with a tx-comment in the following format:

    { "alexandria-proposal" : { "alexandria-vote-name": "[name for topic to be voted on]", 
    "question": "[question to be decided]", "responses": "[possible response1],[possible response2]", 
    "quorum": "[# of token-votes req’d to meet quorum]", "polls-open":
    "[timestamp when votes will begin to be counted]", "polls-close": 
    "[deadline for votes to be cast]" } }

Token-holders then submit their votes by sending their tokens to themselves with a tx-comment in the following format:

    { "alexandria-ballot" : { "alexandria-proposal" : "[txid of the TX containing the alexandria-proposal 
    to be voted on]", "vote": "[chosen response]" } }

####Elections Process
Elections for the Council of Librarians works by users holding some amount of tokens who wish to chose a “representative” or proxy their voting rights to another user sending a tx-comment to themselves in one of the following formats:

    { "alexandria-election" : { "[representative]": "[address of chosen candidate]" } }

Doing this announces the users wish to proxy their day to day decision making ability to another user, but they retain the right to vote for themselves whenever votes are held.

    { "alexandria-election" : { "[vote-proxy]": "[address of chosen candidate]" } }

Doing this announces the users wish to proxy their voting power to the chosen person.

Of particular note, this mechanism should avoid the problems often encountered in “representative democracies” by making it an extremely simple process to un-elect members from the Council if they are making choices that do not reflect the wishes of their constituents (the user base). All they must do is send another message in the same format and either enter their own address or another candidates address.

####Living Articles of Organization
A living AoO will be drafted which contains all of the rules for voting, a description of how day to day decisions are handled, the the maximum amounts that financial decisions must be below in order to be made without a vote and the minimum quorum needs for decisions of various types. Each article of the constitution, and all sections and sub-sections in it can be amended by vote.


####Blockchain Properties
TBD coins, all issued at genesis block.   
Considering a mix of NXT assets, XCP assets & Bitshares assets to ensure long term redundancy (if POS turns out to simply be unscalable (or too vulnerable to attack at scale) and NXT goes to 0, BTX and BTS are unaffected, if BTC goes to 0, so does NXT's POW, but NXT & POS are are unaffected, and so on)   
Voting tokens should either be free or have a cost payable in another token only. If a user must exhaust their ownership in order to share their voice, that's no good.  
Blockchain voting: X% share of tokens = X% of vote 
