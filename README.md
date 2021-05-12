# Proof-of-Authority-Development-Chain


## Point of Authority

## 1. Creating a wallet in mycrypto

In order to create a Proof of Authority, we must first create a wallet using mycrypto.

Create a new wallet by using the nmemonic phrase.
After generating the wallet, there's things you need, in a separate file, copy/paste down the nmemonic phrase, your address, and private key(unencrypted). The address and private key can be found in the Wallet Info part of mycrypto.

## 2. Creating the Genesis block

Navigate to the file where you downloaded the blockchain tools.

use the ``` ./puppeth``` to open your Ethereum private network manager. Here you will create the Genesis block.

The screenshot below, shows step by step all the options I used to create genesis block applenet. The program does not like capital letters, so avoid using capital letters when naming it.
<img src ="Screenshots/Setting Genesis block for Proof of Authority.png" alt="genesis" width="500"/>

* Type ```2``` to pick the ```Configure new genesis```
* Use option ```1``` to ```Create new genesis from scratch```
* Type ```2``` for ```Clique - Proof- of- authority```
* In the question how many seconds should blocks take? ```15``` I have entered the default.
* In the next two questions about accounts seal and the pre-funded account, I have entered the address from the wallet.
* Should the precompile-addresses be pre-funded with 1 wei? Click ```Enter``` on this one and leave blank.
* Specify your chain/network ID if you want an explicit one. Here I entered ```315``` but remember to create a unique one every time you make a new block and write this number down.


<img src ="Screenshots/Creating the genesis specs.png" alt="genesis" width="500"/>



* Click ```2``` Manage existing genesis.
* Followed by a ```2``` Export genesis configurations.
* I then clicked ```enter``` as I wanted the folders to save the following specs into the defaut folder. You should have two folders and two errors, don't be alarmed. 
* Genesis block completed! Use ```Control C``` to get out of puppeth.


## Initializing Node 1 and Node 2:

To initialize Node 1 and Node 2 you need to execute the following commands in terminal.
```.geth init applenet.json --data node1``` 
Please note I am still in the folder where I have all the blockchain tools. Also, my genesis block is named applenet.json, if you put a different name, it goes here.

We use a similar command for Node 2 with some configurations.
```.geth init applenet.json --data node2``` 

You can see it in the screenshot below.

<img src ="Screenshots/Initializing node 1 and 2.png" alt="mint" width="500"/>


## Running Node 1

Now to the fun part, starting the blockchain.
You are going to need two terminals side by side, one for Node 1 and another one for Node 2.

For node 1 you must execute the following command.
```./geth --datadir node1 --unlock "0xb7e2b7caA9832E628D7c2f74eDF1028D3F329A81" --mine --miner.threads 1```

Please note, you must change the command to unlock your wallet, so modify my account with yours, starting at "Oxb7...".

After you run this step and the blockchain starts, you need to fetch the "self=enode://8b8... 30304", you need to copy and paste this somewhere for the node 2.

Here's a screenshot of what I did and where to fetch the self=enode. I have highlighted this on the screenshot.

<img src ="Screenshots/Node 1 command running.png" alt="mint" width="500"/>


## Running Node 2

Go to the second terminal and let's execute node 2.

```./geth --datadir node2 --port 30304 --rpc --bootnodes "enode://52b7225e22a866aef5e3f634de7a1166392338ff9a0e8e25a22057e2eb11ffa77cfa4409253bec44b15e66d959795d40ade26fb1f7ff27c3b828d560842eda3a@127.0.0.1:30303" --mine --miner.threads 1```

<img src ="Screenshots/Node 2 command running.png" alt="mint" width="500"/>


## Sending transaction

Here is a screenshot of the blockchain when we send money.
<img src ="Screenshots/submitted transaction node 2.png" alt="transaction submitted" width="500"/>

Here is the sent transaction in mycrypto wallet.

<img src ="Screenshots/mycrypto wallet sent.png" alt="transaction submitted" width="500"/>
---