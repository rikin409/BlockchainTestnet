# SithNet

## SithNet FAQ
- Proof of Authority Consesus
- 10 second block mining time
- 2 authorized mining nodes
- Currency: ETH
## Installs/Dependencies

1) Python
2) Geth Tools
3) MyCrypto

## Setup

In order to create this testnet, please navigate to the directory in which you have installed geth. Once there, the first thing that needs to be done is create 2 accounts (public/private keypairs). The command for setting up these accounts is as follows:

**./geth --datadir sithnode1 account new**

**./geth --datadir sithnode2 account new**

Now you will notice that two new directories have appeared, "sithnode1" and "sithnode2". These two will be our two initil wallets and mining nodes. Please naviagte to the keystore directories in each of these and copy down the public addresses as follows:

![](./screenshots/PublicAddress-1.png)

After you have saved both of your public addresses we will move on to creating the genisis configurations. In order to do so please run **./puppeth**.

Follow the insutructions and select the following options:
- Proof of Authority
- 10 second block mining time
- Allow sealing from both public addresses we saved earlier (0x.....)
- Prefund both public addresses we saved earlier (0x.....)

Once complete please export your configurations to "sithnode.json". Now you are ready to initialize your blockchain! In order to do so run the following commands:

**./geth --datadir sithnode1 init sithnet.json**

**./geth --datadir sithnode2 init sithnet.json**

Now time to start mining! Follow the instructions below to initilaize both nodes as mining nodes:

**./geth --datadir sithnode1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock**

Please note down the enode address that will show up in the terminal at this point.

**./geth --datadir sithnode2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes "enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock**

Great news, your blockchain is now live and mining!

## Transactions

In order to transact on your newly formed blockchain, please go ahead and open mycrypto. Please navigate to "Change network" and then to "Add Custom Node". Then please select "custom" under Network. Now please name your Node and network and select the options as follows: 

![](./screenshots/MyCryptoCustomNetwork.png)

Now please open one of your keystore files in mycrypto and send a transaction! Congrats you are a crypto expert now!
