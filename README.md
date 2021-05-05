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



## Step Two: Install Go Ethereum Tools

1.- Open a browser and navigate to the Go Ethereum Tools download link(https://geth.ethereum.org/downloads/)

2.- Scroll down to the "Stable Releases" section.

3.- Download "Geth & Tools 1.9.25".

4.- Decompress the archive found in your "Downloads" folder, and rename the decompressed folder as "Blockchain-Tools".

## Step Three: Navigate to "Blockchain-Tools" Folder in Terminal

Open Git Bash (or Terminal, for Mac).

Navigate to your "Blockchain-Tools" folder.

## Step Four: Create your NODE (at least 2 NODES)

1.- Create accounts for two nodes for the network with a separate `datadir` for each using `geth`.

        * ./geth --datadir node1 account new
       
        * ./geth --datadir node2 account new
![image](https://user-images.githubusercontent.com/75185700/117207009-1a7eba80-adb9-11eb-9968-5520ba84a4c2.png)


 
## Step Five: Generate your genesis block.

1.- Run `puppeth`, name your network, and select the option to configure a new genesis block.

2.- Choose the `Clique (Proof of Authority)` consensus algorithm.

3.- Paste both account addresses from the first step one at a time into the list of accounts to seal.

4.- Paste them again in the list of accounts to pre-fund. There are no block rewards in PoA, so you'll need to pre-fund.

5.- You can choose `no` for pre-funding the pre-compiled accounts (0x1 .. 0xff) with wei. This keeps the genesis cleaner.

6.- Complete the rest of the prompts, and when you are back at the main menu, choose the "Manage existing genesis" option.

7.- Export genesis configurations. This will fail to create two of the files, but you only need `networkname.json`.
![image](https://user-images.githubusercontent.com/75185700/117206764-dd1a2d00-adb8-11eb-9d8d-50901d97d228.png)
![image](https://user-images.githubusercontent.com/75185700/117206794-e5726800-adb8-11eb-9cc4-81add6c00c7c.png)


## Step Six: Initialize the nodes with the genesis' json file.

1.- Using `geth`, initialize each node with the new `networkname.json`.

 ./geth --datadir node1 init networkname.json
 ![image](https://user-images.githubusercontent.com/75185700/117206682-c378e580-adb8-11eb-8105-92005d816479.png)

 
 ./geth --datadir node2 init networkname.json
 ![image](https://user-images.githubusercontent.com/75185700/117206652-b956e700-adb8-11eb-950e-b610ac8b7761.png)

 
### Now the nodes can be used to begin mining blocks.

 ## Step Six: Run the nodes in separate terminal windows with the commands:
 
./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock

./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock

    * **NOTE:** Type your password and hit enter - even if you can't see it visually!
    * 
![image](https://user-images.githubusercontent.com/75185700/117207308-70ebf900-adb9-11eb-85f4-751ca74c84d4.png)

![image](https://user-images.githubusercontent.com/75185700/117207281-6a5d8180-adb9-11eb-94d7-d4be2e22abd8.png)


###    Your private PoA blockchain should now be running!

## Step Seven: With both nodes up and running, the blockchain can be added to MyCrypto for testing.

1.- Open the MyCrypto app, then click `Change Network` at the bottom left:
![image](https://user-images.githubusercontent.com/75185700/117198272-71cb5d80-adae-11eb-8792-b37e27709d63.png)

2.- Click "Add Custom Node", then add the custom network information that you set in the genesis.

3.- Make sure that you scroll down to choose `Custom` in the "Network" column to reveal more options like `Chain ID`:
![image](https://user-images.githubusercontent.com/75185700/117198445-a6d7b000-adae-11eb-938f-a08b8bd4c813.png)

4.- Type `ETH` in the Currency box.

5.- In the Chain ID box, type the chain id you generated during genesis creation.

6.- In the URL box type: `http://127.0.0.1:8545`.  This points to the default RPC port on your local machine.

7.- Finally, click `Save & Use Custom Node`. 


## Step Eight: After connecting to the custom network in MyCrypto, it can be tested by sending money between accounts.

1.- Select the `View & Send` option from the left menu pane, then click `Keystore file`.
![image](https://user-images.githubusercontent.com/75185700/117198538-c53dab80-adae-11eb-88ba-ee699164228e.png) Keystore File

2.- On the next screen, click `Select Wallet File`, then navigate to the keystore directory inside your Node1 directory, select the file located there, provide your password when prompted and then click `Unlock`.

3.- This will open your account wallet inside MyCrypto. 
![image](https://user-images.githubusercontent.com/75185700/117199871-55c8bb80-adb0-11eb-9866-943e4798e063.png)

4.- This is the balance that was pre-funded for this account in the genesis configuration; however, these millions of ETH tokens are just for testing purposes.   
![image](https://user-images.githubusercontent.com/75185700/117200216-d7b8e480-adb0-11eb-9eff-db0e98b4e6ba.png)

![image](https://user-images.githubusercontent.com/75185700/117178769-01194680-ad98-11eb-8060-1a8c8cb472cf.png)
Crypto Wallet Account is been funded  

6.- In the `To Address` box, type the account address from Node2, then fill in an arbitrary amount of ETH:
![image](https://user-images.githubusercontent.com/75185700/117203965-4b5cf080-adb5-11eb-83a8-fc8ef4867e13.png)

7.- Confirm the transaction by clicking "Send Transaction", and the "Send" button in the pop-up window.  
![image](https://user-images.githubusercontent.com/75185700/117204257-af7fb480-adb5-11eb-82be-afeb792539dd.png)

8.- Click the `Check TX Status` when the green message pops up, confirm the logout:
![image](https://user-images.githubusercontent.com/75185700/117204314-c58d7500-adb5-11eb-96fd-88da5605dadd.png)

9.- You should see the transaction go from `Pending` to `Successful` in around the same blocktime you set in the genesis.

10.- You can click the `Check TX Status` button to update the status.
![image](https://user-images.githubusercontent.com/75185700/117204490-f9689a80-adb5-11eb-8ab2-4215b0a3a437.png)

Successful transaction!
![image](https://user-images.githubusercontent.com/75185700/117204615-2157fe00-adb6-11eb-8b41-b9e74c12cb71.png)


# Congratulations, you successfully created your own private blockchain with PoA!
















