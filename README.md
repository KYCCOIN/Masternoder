# Masternode run

# KYCC-MNSetupGuide
![Example-Logo](https://i.imgur.com/MoIR36F.png)
# KYC Coin Masternode Setup Guide (Ubuntu 18.04)
This guide will assist you in setting up a KYC Coin Masternode on a Linux Server running Ubuntu 18.04.

If you require further assistance contact the [support team](https://kyccoin.io/)
***
## Requirements
1) **100,000 KYCC**
2) **VPS ([Vultr](https://www.vultr.com/?ref=7485061)) running Linux Ubuntu 18.04**
3) **Windows or MAC OS X local wallet**
4) **SSH client such as [Bitvise](https://dl.bitvise.com/BvSshClient-Inst.exe)**
***
## Contents
* [Section A](#Section-A) - Creating the VPS within [Vultr](https://www.vultr.com/?ref=7485061)
* [Section B](#Section-B) - Downloading and installing Bitvise
* [Section C](#Section-C) - Connecting to the VPS and Getting the Ubuntu Server ready via Bitvise
* [Section D](#Section-D) - Preparing the local wallet
* [Section E](#Section-E) - Editing the configs
* [Section F](#Section-F) - Starting the masternode
***

## <a name = "Section-A"></a> Section A - Creating the VPS within [Vultr](https://www.vultr.com/?ref=7485061) 
***Step 1***
* Register at [Vultr](https://www.vultr.com/?ref=7485061)
***

***Step 2***
* After you have added funds to your account go [here](https://my.vultr.com/deploy/) and choose Server - Cloud Compute

![Example-Location](https://i.imgur.com/CLZoQqU.jpg)
***

***Step 3*** 
* Choose a server location (preferably somewhere close to you)

![Example-Location](https://i.imgur.com/ppJsmNP.jpg)
***

***Step 4***
* Choose a server type: 64 bit OS -> Ubuntu 18.04

![Example-OS](https://i.imgur.com/RHQZqdY.jpg)
***

***Step 5***
* Choose a server size: $5/month

![Example-OS](https://i.imgur.com/3wUalLX.jpg)
***

***Step 6*** 
* Set a Server Hostname & Label (name it whatever you want)

![Example-hostname](https://i.imgur.com/B9AI933.jpg)
![Example-hostname](https://i.imgur.com/h5AK4Ws.jpg)
***

***Step 7***
* Click `Deploy now`

![Example-Deploy](https://i.imgur.com/nnbmVsR.jpg)
***


[:arrow_up: Contents :arrow_up:](#Contents)


## <a name = "Section-B"></a> Section B - Downloading and installing BitVise

***Step 1***
* Download Bitvise [here](https://dl.bitvise.com/BvSshClient-Inst.exe)
***

***Step 2***
* Select the correct installer depending upon your operating system. Then follow the install instructions
***


[:arrow_up: Contents :arrow_up:](#Contents)


## <a name = "Section-C"></a> Section C - Connecting to the VPS and Getting the Ubuntu Server ready via Bitvise

***Step 1***
* Click on your server

![Example-Vultr](https://i.imgur.com/Y89kxuj.jpg)
***

***Step 2***
* Copy your VPS IP

![Example-Vultr](https://i.imgur.com/FhxJpco.jpg)
***

***Step 3***
* Open the bitvise application and fill in the `Host` box with the IP

![Example-BitviseInstaller](https://i.imgur.com/3gBkpPA.png)
***

***Step 4***
* Copy the root password from the VULTR server page

![Example-RootPass](https://i.imgur.com/OdQMuHv.jpg)
***

***Step 5***
* type `root` as the username
* type `password` as the Initial method
* type password
* then press `Login`

![Example-RootPass](https://i.imgur.com/XyIjCRu.png)

* then press "Accept and Save"

![Example-RootPass](https://i.imgur.com/L3PV70k.png)
***

***Step 6 (Updating)***
* Paste the code below into the Bitvise terminal then press enter

```
sudo apt-get update
```

![Example-RootPassEnter](https://i.imgur.com/kLZQj4N.png)
***

***Step 7 (Install all required libraries)***

***Step 7.1***
* Paste the code below into the Bitvise terminal then press enter:

```
sudo apt-get install git automake build-essential libtool autotools-dev autoconf pkg-config libssl-dev libboost-all-dev software-properties-common
```

![Example-RootPassEnter](https://i.imgur.com/odimnQp.png)

When prompted do you want to continue? [Y/n]

Enter `Y` and press enter

![Example-RootPassEnter](https://i.imgur.com/7ZkWHhq.png)


***Step 7.2***
* Paste the code below into the Bitvise terminal then press enter:

```
sudo add-apt-repository ppa:bitcoin/bitcoin
```

![Example-RootPassEnter](https://i.imgur.com/yvcvSqE.png)

Press enter to continue

![Example-RootPassEnter](https://i.imgur.com/6gEyLe6.png)


***Step 7.3***
* Paste the code below into the Bitvise terminal then press enter:

```
sudo apt-get update
```

![Example-RootPassEnter](https://i.imgur.com/MOVh4Wl.png)

***Step 7.4***
* Paste the code below into the Bitvise terminal then press enter:

```
sudo apt-get install libdb4.8-dev libdb4.8++-dev libminiupnpc-dev
```

![Example-RootPassEnter](https://i.imgur.com/VXd6B7Q.png)

When prompted do you want to continue? [Y/n]

Enter `Y` and press enter

![Example-RootPassEnter](https://i.imgur.com/Y7H29Ij.png)
***

***Step 8 (download daemon on VPS)***

***Step 8.1***
* Paste the code below into the Bitvise terminal then press enter:

```
wget https://github.com/KYCCOIN/kyccoin/releases/download/v1.0/kyccoin-1.0.0-x86_64-linux.tar
```

![Example-RootPassEnter](https://i.imgur.com/LBEfFev.png)

***Step 8.2***
* Paste the code below into the Bitvise terminal then press enter:

```
tar -xvf kyccoin-1.0.0-x86_64-linux.tar
cd kyccoin-1.0.0-x86_64-linux
chmod -f 777 kyccoind
chmod -f 777 kyccoin-cli
chmod -f 777 kyccoin-tx
./kyccoind -daemon
```

![Example-RootPassEnter](https://i.imgur.com/iJsvWUk.png)

Once you’ve run the Daemon for the first time it has created the folder structure where the blockchain and all config files are going to be.

***Step 8.3***
* Paste the code below into the Bitvise terminal then press enter:
```
./kyccoin-cli stop
```

![Example-RootPassEnter](https://i.imgur.com/smQjEV8.png)

***


[:arrow_up: Contents :arrow_up:](#Contents)


## <a name = "Section-D"></a> Section D - Preparing the local wallet

In your Wallet-App go to: Tools -> Debug console.  

![Example-Debugconsole](https://i.imgur.com/vbXQU3z.png)

follow these steps:


***Step 1***
* Paste the code below into the Debug console then press enter:

```
getnewaddress MN1
```

answer: KK1qGYWSU1uZuWSiL8MCNkRhZEgkRVWpnA

![Example-getnewaddress](https://i.imgur.com/SDq2Ofs.png)


***Step 2***
* Paste the code below into the Debug console then press enter:

```
sendtoaddress KK1qGYWSU1uZuWSiL8MCNkRhZEgkRVWpnA 100000
```

answer: 27c0982931c33f06a2a9643948fd4a2d917cbe49e586b9d4125d6ecd9d20c215

![Example-sendtoaddress](https://i.imgur.com/8UjFekU.png)


***Step 3***
* Paste the code below into the Debug console then press enter:

```
masternode genkey
```

answer: 8Yu25CwVF77zGkdVArTGt8XL9aQRHAZEW8U6SDpHcGEC3V5j8hC

![Example-genkey](https://i.imgur.com/sdA1e9U.png)


***Step 4***
* Paste the code below into the Debug console then press enter:

```
masternode outputs
```

answer: 
  "txhash": "27c0982931c33f06a2a9643948fd4a2d917cbe49e586b9d4125d6ecd9d20c215",
  "outputidx": 0

![Example-outputs](https://i.imgur.com/SmUM3BT.png)


[:arrow_up: Contents :arrow_up:](#Contents)


## <a name = "Section-E"></a> Section E - Editing the configs


***Step 1***
* Editing the configs via Bitvise terminal

Let's open the kyccoin.conf (using Nano) located in the .kyccoin folder

This folder was created by the daemon on the first run!

*Nano is a great console text editor. If nano is not preinstalled on your system, paste the code below into the Bitvise terminal then press enter:*   
   *`apt-get install nano`*

Paste the code below into the Bitvise terminal then press enter:

```
nano /root/.kyccoin/kyccoin.conf
```

![Example-conf](https://i.imgur.com/Ape65Gd.png)

Paste the code below into the Bitvise terminal then press enter (this is configuration for masternode setup):

```
rpcuser={CHOOSE A RANDOM USER}
rpcpassword={CHOOSE A RANDOM PASSWORD}
rpcallowip=127.0.0.1
port=19222
rpcport=19444
listen=1
server=1
daemon=1
maxconnections=256
masternode=1
externalip={YOUR SERVER IP:19222}
masternodeprivkey={YOURPRIVKEY - WE WILL GET THAT LATER}
logtimestamps=1
masternodeaddr={YOUR SERVER IP}
```

which should result in something like that:

![Example-conf](https://i.imgur.com/2Njc7q0.png)

Save the config (Ctrl+X --> Y --> Enter)

`Ctrl+x`

![Example-conf](https://i.imgur.com/Tpliyj2.png)

`Y`

![Example-conf](https://i.imgur.com/Y0fjevl.png)

`Enter`

![Example-conf](https://i.imgur.com/MUOY9fB.png)


***Step 2***
* Editing the configs in your Wallet-App

Go to the tools tab within the wallet and click open "masternode configuration file"

![Example-configuration](https://i.imgur.com/hzvCw2z.png)

* Fill in the form  
* For `Alias` type something like "MN1" don't use spaces  
* The `Address` is the IP and port of your server (this will be in the Bitvise terminal that you still have open)  
* The `PrivKey` is your masternode private key (This is also in the Bitvise terminal that you have open)  
* The `TxHash` is the transaction ID/long key that you copied to the text file  
* The `Output Index` is the 0 or 1 that you copied to your text file  

![Example-configuration](https://i.imgur.com/qzUsCAO.png)

Click "File Save"


[:arrow_up: Contents :arrow_up:](#Contents)


## <a name = "Section-F"></a> Section F - Starting the masternode


***Step 1***
* Starting the daemon on the Ubuntu server:

```
./kyccoind
```

![Example-starting](https://i.imgur.com/CfRsD5m.png)

The daemon should start minimized.   
You’ll only see a message like this:   

```
kyccoin server starting
```

![Example-starting](https://i.imgur.com/b9esk3r.png)

wait for the full sync before continuing:

```
./kyccoin-cli mnsync status
```

You should see: "RequestedMasternodeAssets" : 999, (this means full sync)

![Example-mnsync](https://i.imgur.com/6kBPfsd.png)

***Step 2***
* Move on your Wallet-App

Wait for the transaction to have at least 16 confirmations before continuing.

![Example-confirmations](https://i.imgur.com/C5JT3eg.png)

* Close out of the wallet and reopen Wallet  
* Go to the Masternodes
* select MN1
* click Start alias
* click Yes

![Example-startmasternode](https://i.imgur.com/8nlraWO.png)

* click ok

![Example-startmasternode](https://i.imgur.com/oFnwDOG.png)

which should result in something like that:

![Example-startmasternode](https://i.imgur.com/VDcYXCN.png)

***Step 3***
* Check the status of your masternode within the VPS by using the command below:

```
./kyccoin-cli masternode status
```

You should see:

![Example-status](https://i.imgur.com/goqxWbk.png)

If you do, congratulations! You have now setup a masternode.  
If you do not, please contact me or any other support

[:arrow_up: Contents :arrow_up:](#Contents)
