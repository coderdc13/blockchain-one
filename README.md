# Blockchain One Homework

## Introduction

This readme is designed to help the user to compose the blockchain and join the network. In addition, this readme provides lists of items, directions, and indications of completion. This readme also aims to describe the successful construction of the Proof of Authority (PoA) blockchain.


(Nota Bene: Vast Majority of Text (99.999999%) from Instructors GS, AN, and KS and from Tutor, Ms. LT)



## General Start

### Material

The user needs specific programs.

-Git Bash

-MyCrypto Application

-Go Ethereum

-Microsoft Windows

-Anaconda (Optional)

### What to Do with Material

The user must have Git Bash terminal (https://gitforwindows.org/). In addition, the user must have the MyCrypto application downloaded (https://download.mycrypto.com/). The user must have a version of Go Ethereum; the student author has the version labeled “Geth & Tools 1.9.23” (https://geth.ethereum.org/downloads/). It would help to have access to Microsoft Windows Explorer in order to view the structure of files and folders. The user could benefit from access to the Anaconda interface, leveraging the name of the anaconda network (possible name: “zbank_blockchain”).

At least two action items help the process. One is to have the MyCrypto application open. Another action item is to have two (2) Git Bash terminals open with the ability to open either the puppeth or geth program (i.e., have two (2) terminals open at the Ethereum directory).

### Check

The icons for each of these programs appears with the successful download and loading.

 

## Data Specific for Network

### Node 1 Information (Directly Below)

Public Address of the Key:   0x14E77e8dE86498E0fB5Ad53Bc0A1Bb2627C898a0

Path of the Secret Key File: node1\keystore\UTC--2020-11-02T14-54-47.164341500Z--14e77e8de86498e0fb5ad53bc0a1bb2627c898a0

Password: Player13

Port: 30303

### Node 2 Information (Directly Below)

Public Address of the Key:   0x465A15B479527Bf991c4f5a651eAb94caD150020

Path of the Secret Key File: node2\keystore\UTC--2020-11-02T14-56-25.696957100Z--465a15b479527bf991c4f5a651eab94cad150020

Password: Player31

Port: 30304 

Enode from Node 1 (Directly Below):

enode://86a7596ac42d38a47044843db9800f3c7837ecc1b842353b18921bc5dc53975cf8c20ea918d37eca1d68d5ee9142b09242403013c0a1de9182f9573383834158@127.0.0.1:30303

### General Clique Data

Chain ID: 450

Blocktime: 15

Network Name: trial_five

 

## What to Do with Data Specific for Network

(Nota Bene: Text below lifted almost exclusively from POA-Blockchain-guide.md)

The Proof of Authority (PoA) algorithm is typically used for private blockchain networks as it requires pre-approval of, or voting in of, the account addresses that can approve transactions (seal blocks).

Unlike for Proof of Stake (PoS), it is important to start new accounts in the geth program (./geth) before running the puppeth program (./puppeth).

The user has the option to set the virtual environment to the zbank_blockchain with the specific command (provided below).

conda activate zbank_blockchain

Otherwise, it is possible to have the two (2) Git Bash terminals, with each open on the Ethereum network (as described above).

The user must accounts for two nodes for the network with a separate datadir for each using geth.

In order to activate the first node, the user has to enter a specific command (listed directly below).

./geth init trial_five.json --datadir node1

In order to activate the second node, the user has to enter a specific command (listed directly below).

./geth init trial_five.json --datadir node2

The user would do well to create a file with the passwords (Player13 for node1 and Player31 for node2) and to save this file in the same directory as the node files. In addition, the user would do well to enter each password at the correct time. At least one time would be after entering the command to start mining.

 

 

The user would most likely mine most efficiently with starting mining on node1 in one Git Bash terminal and with continuing mining on node2 in another Git Bash terminal.

The user may start mining on node1 with a specific command (given below).

./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock

With the “SEALER_ONE_ADDRESS” as the address of the first public address of the key for the first node, the command changes.

./geth --datadir node1 --unlock "0x14E77e8dE86498E0fB5Ad53Bc0A1Bb2627C898a0" --mine --rpc --allow-insecure-unlock

For node2, which may be entered in a different Git Bash terminal as described above, the command is somewhat different (given below).

./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock

With “SEALER_TWO_ADDRESS” being the second public address for the second node and with the “SEALER_ONE_ENODE_ADDRESS” as the address of the enode address for the first node, the command changes.

./geth --datadir node2 --unlock "0x465A15B479527Bf991c4f5a651eAb94caD150020" --mine --port 30304 --bootnodes "enode://86a7596ac42d38a47044843db9800f3c7837ecc1b842353b18921bc5dc53975cf8c20ea918d37eca1d68d5ee9142b09242403013c0a1de9182f9573383834158@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock

After entering these last two commands, the user should enter the unique passwords, even when not prompted (Player13 for node1 and for node2, Player31).

### Explanation of Flags

The commands and options for the ./geth and ./puppeth programs are at https://geth.ethereum.org/docs/interface/command-line-options. 

The --allow-insecure-unlock flag provides the opportunity to unlock. The site at https://geth.ethereum.org/docs/interface/command-line-options states that this command provides for "insecure account unlocking when account-related RPCs are exposed."


The --bootnode flag allows for peer-to-peer networking. The site at https://geth.ethereum.org/docs/interface/command-line-options states that this command provides for communication with "comma separated enode URLs."


The --mine flag commmands the node to mine. The site at https://geth.ethereum.org/docs/interface/command-line-options states that this command provides for communication with "comma separated enode URLs."


The --minerthreads flag instructs the program how much effort to devote to the blockchain mining process. This command may be deprecated. The --miner.threads value (according to https://geth.ethereum.org/docs/interface/command-line-options) gives the "number of CPU threads to use for mining."


The --password flag allows use of the password file. The website https://geth.ethereum.org/docs/interface/command-line-options states that this command allows for the "password file to use for non-interactive password input."


The --rpc flag allows the node to participate in the network. The website https://geth.ethereum.org/docs/interface/command-line-options states that this command provides for use of "the HTTP-RPC server" and that this command is being deprecated.


 

With both nodes working, the blockchain can be added to MyCrypto for testing.

### Check

One can tell that the nodes are working by verifying transactions with the MyCrypto application.

 

## MyCrypto

The MyCrypto application is being leveraged to verify the functionality of the blockchain. This verification occurs through tracking a transaction. This verification requires a set of steps.

The user should log into the MyCrypto application and then create a custom node. The node name, to reiterate, is trial_five. The network is custom. The currency is ETH. The Chain ID is 450. The URL is http://127.0.0.1:8545.


Access to the initial node occurs through the selection of logging in through the Keystore File. Upon choosing the Keystore File access option, the user is then taken to a screen in which the user may enter the keystore file from the node1 directory along with the password. In this case the keystore file identification is node1\keystore\UTC--2020-11-02T14-54-47.164341500Z--14e77e8de86498e0fb5ad53bc0a1bb2627c898a0. The password for node1 is Player13.

Upon gaining access to the account of the first node through the keystore file process, the user finds a large account full of practice Ethereum. The user may leverage this practice Ethereum and send some of the currency to the node2 address (0x465A15B479527Bf991c4f5a651eAb94caD150020). Sometimes, simply pasting the address is not good enough; the user may have to erase and retype the initial 0x in the address. Validation of the ./puppeth and ./geth work occurs with a successful transaction.


 

(Nota Bene: Text above lifted almost exclusively from POA-Blockchain-guide.md)



## Review of Blockchain Establishment




![text](/Screenshots/Screenshot%20(1710).png)






Directly above shows the use of the addresses for the two nodes sealing and pre-funding. Please note also that the default time is 15 seconds and that the block is 450.




![text](/Screenshots/Screenshot%20(1711).png)





Directly above shows the export of the genesis configurations.




![text](/Screenshots/Screenshot%20(1713).png)





Directly above shows the initialization of the nodes.




![text](/Screenshots/Screenshot%20(1715).png)



Directly above shows the use of the key file to open the node account.



### Transfer of 3.9 ETH






![text](/Screenshots/Screenshot%20(1717).png)





Directly above shows the transfer of 3.9 ETH from node1 to node2.




![text](/Screenshots/Screenshot%20(1718).png)




![text](/Screenshots/Screenshot%20(1719).png)





![text](/Screenshots/Screenshot%20(1720).png)






![text](/Screenshots/Screenshot%20(1722).png)






![text](/Screenshots/Screenshot%20(1723).png)







Directly above shows the process of the 3.9 ETH transfer. This transaction was signed with the hash of 0xf86d8084ee6b280082520894465a15b479527bf991c4f5a651eab94cad15002088361f955640060000808203a8a08d15551dacadef7e5cd0ca98cb2f9382521aaa7e15f98a16690844afa252107aa0294567edfd2509d0446ba1b0fd3553d3e29b7961b0fb3d56e1e4a9a02102e53d. Also, the JavaScript object/Python dictionary was 

{ "value": "0x361f955640060000", "data": "0x", "to": "0x465a15b479527bf991c4f5a651eab94cad150020", "nonce": "0x0", "gasPrice": "0xee6b2800", "gasLimit": "0x5208", "chainId": 450}   


This transaction was in the pending stage for over twenty (20) minutes.



### Transfer of 14 ETH




![text](/Screenshots/Screenshot%20(1725).png)






Directly above shows the attempt to transfer 14 ETH from node1 to node2.






![text](/Screenshots/Screenshot%20(1727).png)



Directly above shows the details of the transfer of 14 ETH from node1 to node2. The signature hash is 
0xf86e01850df847580082520894465a15b479527bf991c4f5a651eab94cad15002088c249fdd327780000808203a8a028446781e4001e2fa5adf7bb0226a57968fc5c96368a5c05bd4006e3f7411c86a01d8bf731647bc7cbecb4f52aeec51f2067e0c50fd19abc4170cf72109ecea26b. Also, the JavaScript object/Python dictionary is 


{ "value": "0xc249fdd327780000", "data": "0x", "to": "0x465a15b479527bf991c4f5a651eab94cad150020", "nonce": "0x1", "gasPrice": "0xdf8475800", "gasLimit": "0x5208", "chainId": 450}  

The value for the nonce is noteworthy.



### Definitions


wei/gwei - One (1) unit of Ethereum (ether, or ETH) is 1.0 ^ 10^18 wei (https://academy.binance.com/en/glossary/wei).

nonce - One may substitute this word with the phrase "number used once." The nonce is a number that is used to enhance security.

gas - This term describes "the cost necessary to perform a transaction on the network" (https://www.investopedia.com/terms/g/gas-ethereum.asp#:~:text=On%20the%20ethereum%20blockchain%2C%20gas,fractions%20of%20ether%20called%20gwei).







## Success

Upon facing an extended period of pending transactions, both the node1 and node2 operations were stopped and restarted.




![text](/Screenshots/Screenshot%20(1730).png)




Directly above shows that the 3.9 ETH transfer succeeded.




![text](/Screenshots/Screenshot%20(1729).png)




Directly above shows that the 14 ETH transfer succeeded.


## Update on NOV 06 2020--Successful Preservation of Blockchain and Successful Additional Transactions

The Instructor Corps very generously granted an extension on this assignment. As a result, the student author (Franklin Bueno) retested the blockchain with additional transaction. To his great pleasure and satisfaction, the student author found that his blockchain and private network (trial_five) are maintaining integrity and the ability to hold transactions. In particular, the student author managed to document the transactions and results for at least four (4) transactions for NOV 06 2020 to the node of the second address: 41 ETH at 1421 EST, 29 ETH at 1426 EST, 23 ETH at 1433 EST, 61 ETH at 1441 EST. These transactions are catalogued as the four (4) top transactions in the graphic (directly below).





![text](/Screenshots/Screenshot%20(1826).png)






There are specific transaction (TX) hash values for each of the transactions: 0xedf6c36dcad82dd4ee071f11281c0269bbcbfc8373e1b69681aa87eb97bdeb38 for the 41 ETH transaction at 1421 EST, 0x20b1544104a19736f310856630359b66760645444740277e4a1541d891404420 for the 29 ETH transaction at 1426 EST, 0x7a337d62edcd4e7e5deab52186d3a9af0b713d71b2d5aa151747b645ef73b82c for the 23 ETH transaction at 1433 EST, 0x4813d408e133fd297bcae4c1445035d2f8b6e4146fc3dfd430f592165b4149b2 for the 61 ETH transaction at 1441 EST.
 
The data for the 41 ETH transaction at 1421 EST is provided (directly below).




![text](/Screenshots/Screenshot%20(1828).png)




The data for the 29 ETH transaction at 1426 EST is provided (directly below).




![text](/Screenshots/Screenshot%20(1829).png)




The data for the 23 ETH transaction at 1433 EST is provided (directly below).





![text](/Screenshots/Screenshot%20(1830).png)





The data for the 61 ETH transaction at 1441 EST is provided (directly below).




![text](/Screenshots/Screenshot%20(1831).png)




The screenshots for the geth updates at node one for the all of the NOV 06 2020 transactions are provided (directly below).




![text](/Screenshots/Screenshot%20(1768).png)


![text](/Screenshots/Screenshot%20(1769).png)


![text](/Screenshots/Screenshot%20(1770).png)


![text](/Screenshots/Screenshot%20(1771).png)


![text](/Screenshots/Screenshot%20(1772).png)


![text](/Screenshots/Screenshot%20(1773).png)



![text](/Screenshots/Screenshot%20(1774).png)



![text](/Screenshots/Screenshot%20(1775).png)



![text](/Screenshots/Screenshot%20(1776).png)



![text](/Screenshots/Screenshot%20(1777).png)



![text](/Screenshots/Screenshot%20(1778).png)



![text](/Screenshots/Screenshot%20(1779).png)



![text](/Screenshots/Screenshot%20(1780).png)




![text](/Screenshots/Screenshot%20(1781).png)



![text](/Screenshots/Screenshot%20(1782).png)



![text](/Screenshots/Screenshot%20(1783).png)




![text](/Screenshots/Screenshot%20(1784).png)



![text](/Screenshots/Screenshot%20(1785).png)



![text](/Screenshots/Screenshot%20(1786).png)




![text](/Screenshots/Screenshot%20(1787).png)



![text](/Screenshots/Screenshot%20(1788).png)




![text](/Screenshots/Screenshot%20(1789).png)




![text](/Screenshots/Screenshot%20(1790).png)



![text](/Screenshots/Screenshot%20(1791).png)



![text](/Screenshots/Screenshot%20(1792).png)



![text](/Screenshots/Screenshot%20(1793).png)



![text](/Screenshots/Screenshot%20(1794).png)



![text](/Screenshots/Screenshot%20(1795).png)




![text](/Screenshots/Screenshot%20(1796).png)




![text](/Screenshots/Screenshot%20(1797).png)





One can note that the interval captured in the screenshots above is from about 1409 EST to about 1453 EST.

Directly below is the record of geth updates for node two.




![text](/Screenshots/Screenshot%20(1799).png)




![text](/Screenshots/Screenshot%20(1800).png)




![text](/Screenshots/Screenshot%20(1801).png)




![text](/Screenshots/Screenshot%20(1802).png)





![text](/Screenshots/Screenshot%20(1803).png)






![text](/Screenshots/Screenshot%20(1804).png)






![text](/Screenshots/Screenshot%20(1805).png)






![text](/Screenshots/Screenshot%20(1806).png)





![text](/Screenshots/Screenshot%20(1807).png)





![text](/Screenshots/Screenshot%20(1808).png)






![text](/Screenshots/Screenshot%20(1809).png)






![text](/Screenshots/Screenshot%20(1810).png)





![text](/Screenshots/Screenshot%20(1811).png)




![text](/Screenshots/Screenshot%20(1812).png)




![text](/Screenshots/Screenshot%20(1813).png)



![text](/Screenshots/Screenshot%20(1814).png)



![text](/Screenshots/Screenshot%20(1815).png)




![text](/Screenshots/Screenshot%20(1816).png)




![text](/Screenshots/Screenshot%20(1817).png)




![text](/Screenshots/Screenshot%20(1818).png)



![text](/Screenshots/Screenshot%20(1819).png)



![text](/Screenshots/Screenshot%20(1820).png)


One may note that the interval for the screenshots above is for the time between 1419 EST to about 1459 EST, with the first transaction occuring 1421 EST on NOV 06 2020.





