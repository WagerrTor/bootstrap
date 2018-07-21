# Wagerr testnet bootstrap file

### How to install

### Bootstrap the Blockchain Synchronization

Normally the Wagerr client will download the transaction and network information, called the blockchain, from the network by syncing with the other clients. This process can take quite some time as the [Wagerr blockchain](https://blockchain.info/charts/blocks-size) is growing bigger and bigger for each day. Luckily there is a safe and fast way to speed up this process. We'll show you how to bootstrap your blockchain to bring your client up to speed in just a few simple steps.

### Requirements

- A fresh install of the wagerr client software.

**For Windows users:**
Open explorer, and type into the address bar:

	%APPDATA%\Wagerr
    
This will open up the data folder. It should look like the image below. Copy over the bootstrap.dat from your download folder to this directory.

**For OSX users:**
Open Finder by pressing Press [shift] + [cmd] + [g] and enter:

	~/Library/Application Support/Wagerr/
    
**For Linux users:**
The directory is hidden in your User folder. Go to:

	~/.wagerr/
    
### Importing the blockchain
Now start the Wagerr client software. It should show "Importing blocks from disk".

Wait until the import finishes. The client will download the last days not covered by the import. Congratulations you have successfully imported the blockchain!

### Is this safe?

Yes, the above method is safe. The download contains only raw blockchain data and the client verifies this on import. Do not download the blockchain from unofficial sources, especially if they provide `*.rev` and `*.sst` files. These files are not verified and can contain malicious edits.

### How to create my own bootstrap?

The block files are in the same format as the bootstrap file. Their format is really simple: just concatenate all blocks after prefixing them by the network number (to avoid mixing the testnets) and the block length. 

        [network number] [length] [block header] [block transactions]
        [network number] [length] [block header] [block transactions]
        [network number] [length] [block header] [block transactions]

### How to create my own bootstrap on Linux/Mac (method 2)?

We simply cat all blk000*.dat files into bootstrap.dat

    1. Open terminal
    1. Go to the folder where the blocks are. In this case Wagerr's folder (it's the same for other wagerr forks)

            ```            
            cd "Library/Application Support/Wagerr/blocks/"
            ```

    1. concatenate all the blk files
            
            ```        
            cat blk000*.dat > bootstrap.dat
            ```

    1. Done.

### How to create my own bootstrap on Windows (method 2)?

Making your own bootstrap.dat is simple in windows, just run this command from your datadir/blocks dir

    ```
    Copy /b blk00000.dat+blk00001.dat+blk00002.dat bootstrap.dat
    ```

This batch script can make your life easier on windows, you need to run it from datadir/blocks directory:

    ```
    @echo off 
    setlocal enableDelayedExpansion 

    set WAGERRDATADIR=%APPDATA%\Wagerr\blocks
    for /F %%x in ('dir /B/D/ON %WAGERRDATADIR%\blk*.*') do (
      IF NOT [!B!] == [] set B=!B!+
      set FILENAME=%WAGERRDATADIR%\%%x
      set B=!B!"!FILENAME!"
    )
    copy /b %B% bootstrap.dat
    ```

### Links - How to create my own bootstrap file

  - **How to for Windows, Linux and Mac users**
    - For [Linux/Mac](./../../#how-to-create-my-own-bootstrap-on-linuxmac-method-2) users
    - For [Windows](./../../#how-to-create-my-own-bootstrap-on-windows-method-2) users
  - For advanced users - [manually](./../../#how-to-create-my-own-bootstrap)

Bootstrap file (_bootstrap.dat_)
 - Block height: `41384`
 - Block hash: `4480d89de6711113608aa5cb5db8b17788fb81d01f91f10afbb272e83a017bd5`
 - Tx: `87935`
 - Date: `2018-07-21 15:37:29`
 - Date (epoch): `1532180249`
 - Progress: `1.000001`
 - Cache: `27571`

### Block 41384
```
{
  "hash": "4480d89de6711113608aa5cb5db8b17788fb81d01f91f10afbb272e83a017bd5",
  "confirmations": 1,
  "size": 461,
  "height": 41384,
  "version": 4,
  "merkleroot": "3822fcc4422b51fcf18c3bcc0fc0a141a1f8bbc6f277947d5e784aedb4f97527",
  "acc_checkpoint": "72089db425e22522c7ea6ba5a2d08676e23b7b2da38250679a0b5e184a7e4078",
  "tx": [
    "c6eefc881ed3af4767da758bebffb97056462bfd5e6499801a999216d49d9707",
    "d2d3b2d4235a964c1e5890b84ba76a0fa8b7b4fb7a9bc5ed395c86bb96175589"
  ],
  "time": 1532180249,
  "nonce": 0,
  "bits": "1b082afd",
  "difficulty": 8023.459600629935,
  "chainwork": "00000000000000000000000000000000000000000000000216a45975ea6c0fb3",
  "previousblockhash": "41d30b2572bcea8ec9444e1841a453840f0f7ed6ec026eba90df15c0ecda701d",
  "moneysupply": 237359272.19103867,
  "zWGRsupply": {
    "1": 134.00000000,
    "5": 290.00000000,
    "10": 1070.00000000,
    "50": 2450.00000000,
    "100": 6400.00000000,
    "500": 21000.00000000,
    "1000": 61000.00000000,
    "5000": 195000.00000000,
    "total": 287344.00000000
  }
}
```

### Genesis block
```
{
  "hash": "00000fdc268f54ff1368703792dc046b1356e60914c2b5b6348032144bcb2de5",
  "confirmations": 41383,
  "size": 312,
  "height": 0,
  "version": 1,
  "merkleroot": "c4d06cf72583752c23b819fa8d8cededd1dad5733d413ea1f123f98a7db6af13",
  "acc_checkpoint": "0000000000000000000000000000000000000000000000000000000000000000",
  "tx": [
    "c4d06cf72583752c23b819fa8d8cededd1dad5733d413ea1f123f98a7db6af13"
  ],
  "time": 1518696182,
  "nonce": 75183976,
  "bits": "1e0ffff0",
  "difficulty": 0.000244140625,
  "chainwork": "0000000000000000000000000000000000000000000000000000000000100010",
  "nextblockhash": "00000385558ec1b9af7f939e1626a3116b9fb988c86c2f915e6451e8efcd0521",
  "moneysupply": 0.00000000,
  "zWGRsupply": {
    "1": 0.00000000,
    "5": 0.00000000,
    "10": 0.00000000,
    "50": 0.00000000,
    "100": 0.00000000,
    "500": 0.00000000,
    "1000": 0.00000000,
    "5000": 0.00000000,
    "total": 0.00000000
  }
}
```

### What is actually bootstrap.dat file?

In 2012, the Bitcoin blockchain was growing to 10+ gigabytes and downloading the entire chain from the p2p network was taking an excessive amount of time (multiple days) due to inefficiencies in the way nodes shared block data. In order make it easier to setup a full node, a snapshot of the blockchain data [was distributed](https://bitcointalk.org/index.php?topic=145386.0) by [Jeff Garzik](https://github.com/jgarzik) as a file named bootstrap.dat using BitTorrent. Starting with version 0.8 bitcoind will load and validate initial blockchain data from any file named bootstrap.dat found in its [data directory](https://en.bitcoin.it/wiki/Data_directory#Default_Location).

Today, this is actually slower than syncing normally. In Bitcoin Core version 0.10.0+ the p2p sync process was dramatically improved making it faster than using the bootstrap.dat file. This bootstrapping process is therefore obsolete and discouraged.
