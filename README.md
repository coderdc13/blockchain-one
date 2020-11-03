# Blockchain One Homework

## Introduction

This readme is designed to help the user to compose the blockchain and join the network. In addition, this readme provides lists of items, directions, and indications of completion. This readme also aims to describe the successful construction of the Proof of Authority (PoA) blockchain.

Pre-Work Arrangement and Structure

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

Port: 30304 (This number was not used in the initial establishment of the blockchain…)

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

./geth --datadir node2 --unlock "0x465A15B479527Bf991c4f5a651eAb94caD150020" --mine --port 30304 --bootnodes "enode://86a7596ac42d38a47044843db9800f3c7837ecc1b842353b18921bc5dc53975cf8c20ea918d37eca1d68d5ee9142b09242403013c0a1de9182f9573383834158@127.0.0.1:30303 --ipcdisable --allow-insecure-unlock

After entering these last two commands, the user should enter the unique passwords, even when not prompted (Player13 for node1 and for node2, Player31).

### Explanation of Flags

The commands and options for the ./geth and ./puppeth programs are at https://geth.ethereum.org/docs/interface/command-line-options. 

The --allow-insecure-unlock flag provides the opportunity to unlock.
The --bootnode flag allows for peer-to-peer networking.
The --mine flag commmands the node to mine.
The --minerthreads flag instructs the program how much effort to devote to the blockchain mining process.
The --password flag allows use of the password file.
The --rpc flag allows the node to participate in the network.


 

With both nodes working, the blockchain can be added to MyCrypto for testing.

### Check

One can tell that the nodes are working by verifying transactions with the MyCrypto application.

 

## MyCrypto

The MyCrypto application is being leveraged to verify the functionality of the blockchain. This verification occurs through tracking a transaction. This verification requires a set of steps.

The user should log into the MyCrypto application and then create a custom node. The node name, to reiterate, is trial_five. The network is custom. The currency is ETH. The Chain ID is 450. The URL is http://127.0.0.1:8545.


Access to the initial node occurs through the selection of logging in through the Keystore File. Upon choosing the Keystore File access option, the user is then taken to a screen in which the user may enter the keystore file from the node1 directory along with the password. In this case the keystore file identification is node1\keystore\UTC--2020-11-02T14-54-47.164341500Z--14e77e8de86498e0fb5ad53bc0a1bb2627c898a0. The password for node1 is Player13.

Upon gaining access to the account of the first node through the keystore file process, the user finds a large account full of practice Ethereum. The user may leverage this practice Ethereum and send some of the currency to the node2 address (0x465A15B479527Bf991c4f5a651eAb94caD150020). Sometimes, simply pasting the address is not good enough; the user may have to erase and retype the initial 0x in the address. Validation of the ./puppeth and ./geth work occurs with a successful transaction.


 

(Nota Bene: Text above lifted almost exclusively from POA-Blockchain-guide.md)




!(main/Screenshots/Screenshot%20(1710).png)
