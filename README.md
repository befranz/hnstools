# hnstools
Tools for Handshake full nodes (hsd and Bob Wallet)

## Basic Requirements
The following components need to be installed

* Bash Shell on Linux, MacOS or Windows 10 with WSL (Windows Subsystem for Linux) 
* Handshake full node 
  * hsd (https://github.com/handshake-org/hsd) OR
  * Bob Wallet - includes hsd (https://github.com/kyokan/bob-wallet)
* Handshake hs-client (https://github.com/handshake-org/hs-client)
* curl, jq, idn2

## Tool 1: mynames
Creates a list of all names a specific wallet is holding.

### Installation / Update
```
cd
git clone https://github.com/befranz/hnstools.git
cp hnstools/hnstools.cfg ~/hnstools.cfg
nano ~/hnstools.cfg      # and adjust your Config File (see below)
```
To update this repository
```
cd ~/hnstools
git pull
```

### Config File ~/hnstools.cfg

Create a file with a text editor in your home directory called **hnstools.cfg**. Set **API-Key** and **password** for hsd / Bob Wallet. If the full node runs on same machine you usually don't change anything else. Otherwise you probably know what to change. This config file will also be used for other tools which might come in the future.

```
HNS_API="<Your API-Key>"
HNS_PW="<Your Password>"

HNS_IP="127.0.0.1"
HNS_NPORT="12037"
HNS_WPORT="12039"
```

### Start
**Syntax**: ~/hnstools/mynames \<Wallet Name\>
  
It creates CSV file **~/hnstools/\<Wallet Name\>-mynames.csv** with following data:
WALLET,OPEN,CURRENT,EXPIRE,LASTACTION,NAME,PRICE,SYMBOL,STATUS,REGISTERED

The list contains not only registered names but also revealed names which are currently owned by this wallet. Ownership may change if a higher bid was revealed after the list was created.
