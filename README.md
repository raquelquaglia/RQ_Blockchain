# RQ_Blockchain POA
Homework
# Steps to Start the Network:

## Step One: Install MyCrypto and Create your Wallet

 1.- Open a browser and navigate to the MyCrpyto download link(https://download.mycrypto.com/).
 2.- Download the correct version, based on your operating system.
 3.- Follow the installation wizard.
 4.- Open MyCrypto.
 5.- Select "Create New Wallet".
 6.- Select "Generate a Wallet".
 7.- Select "Generate a Mnemonic Phrase".
 8.- Write down the mnemonic phrase provided.
 9.- Provide the mnemonic phrase.
10.- Select "View & Send".
11.-Select "Mnemonic Phrase".
12.-Input your mnemonic phrase.
13.-Select "Choose address".
14.-Select "Testnet (ETH)" for the "Addresses" dropdown.
15.-Select the first address and select "Unlock".
16.-Write down your "Account Address".
17.-Select "Wallet Info".
18.-Write down your "Private Key".
![image](https://user-images.githubusercontent.com/75185700/117178284-805a4a80-ad97-11eb-99b5-49681c7c7643.png)
Crypto Wallet Account is Created, Balance is zero.

![image](https://user-images.githubusercontent.com/75185700/117178769-01194680-ad98-11eb-8060-1a8c8cb472cf.png)
Crypto Wallet Account is been funded

# Step Two: Install Go Ethereum Tools

1.- Open a browser and navigate to the Go Ethereum Tools download link(https://geth.ethereum.org/downloads/)
2.- Scroll down to the "Stable Releases" section.
3.- Download "Geth & Tools 1.9.25".
4.- Decompress the archive found in your "Downloads" folder, and rename the decompressed folder as "Blockchain-Tools".

# Step Three: Navigate to "Blockchain-Tools" Folder in Terminal

Open Git Bash (or Terminal, for Mac).
Navigate to your "Blockchain-Tools" folder.

# Step Four: Create your NODE (at least 2 NODES)

1.- Create accounts for two nodes for the network with a separate `datadir` for each using `geth`.
        * ./geth --datadir node1 account new
        * ./geth --datadir node2 account new
 
# Step Five: Generate your genesis block.

1.- Run `puppeth`, name your network, and select the option to configure a new genesis block.
2.- Choose the `Clique (Proof of Authority)` consensus algorithm.
3.- Paste both account addresses from the first step one at a time into the list of accounts to seal.
4.- Paste them again in the list of accounts to pre-fund. There are no block rewards in PoA, so you'll need to pre-fund.
5.- You can choose `no` for pre-funding the pre-compiled accounts (0x1 .. 0xff) with wei. This keeps the genesis cleaner.
6.- Complete the rest of the prompts, and when you are back at the main menu, choose the "Manage existing genesis" option.
7.- Export genesis configurations. This will fail to create two of the files, but you only need `networkname.json`.

# Step Six: Initialize the nodes with the genesis' json file.

1.- Using `geth`, initialize each node with the new `networkname.json`.
 ./geth --datadir node1 init networkname.json
 ./geth --datadir node2 init networkname.json
### Now the nodes can be used to begin mining blocks.

 # Step Six: Run the nodes in separate terminal windows with the commands:
*  ./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock
*  ./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock
    * **NOTE:** Type your password and hit enter - even if you can't see it visually!

##    Your private PoA blockchain should now be running!



















