# PIVX bootstrap file

### How to install

### Bootstrap the Blockchain Synchronization

Normally the Pivx client will download the transaction and network information, called the blockchain, from the network by syncing with the other clients. This process can take quite some time as the [Pivx blockchain](https://blockchain.info/charts/blocks-size) is growing bigger and bigger for each day. Luckily there is a safe and fast way to speed up this process. We'll show you how to bootstrap your blockchain to bring your client up to speed in just a few simple steps.

### Requirements

- A fresh install of the pivx client software.

**For Windows users:**
Open explorer, and type into the address bar:

	%APPDATA%\Pivx
    
This will open up the data folder. It should look like the image below. Copy over the bootstrap.dat from your download folder to this directory.

**For OSX users:**
Open Finder by pressing Press [shift] + [cmd] + [g] and enter:

	~/Library/Application Support/Pivx/
    
**For Linux users:**
The directory is hidden in your User folder. Go to:

	~/.pivx/
    
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
    1. Go to the folder where the blocks are. In this case Pivx's folder (it's the same for other pivx forks)

            ```            
            cd "Library/Application Support/Pivx/blocks/"
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

    set PIVXDATADIR=%APPDATA%\Pivx\blocks
    for /F %%x in ('dir /B/D/ON %PIVXDATADIR%\blk*.*') do (
      IF NOT [!B!] == [] set B=!B!+
      set FILENAME=%PIVXDATADIR%\%%x
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
 - Block height: `1024200`
 - Block hash: `59f2179b2faf487df93d9511906a237df9f4ee4bf3d4ae55f913e4549b2923a3`
 - Tx: `2191554`
 - Date: `2018-02-07 02:37:59`
 - Date (epoch): `1517971079`
 - Progress: `1.000001`
 - Cache: `26376`

### Block 1024200
```

{
    "hash" : "59f2179b2faf487df93d9511906a237df9f4ee4bf3d4ae55f913e4549b2923a3",
    "confirmations" : 25,
    "size" : 461,
    "height" : 1024200,
    "version" : 4,
    "merkleroot" : "fe3af83af3e05ac4da83448dfb8c43c61aa5e7a537729c88f5780ce1bcead8f1",
    "acc_checkpoint" : "876c9cf6a013a9bb8d536133d41d6d8875023e941a5d297801e6e0799b63af4d",
    "tx" : [
        "c28fd1825bd3f4ba1277dce2307ecabeb0fc68f65290758394aa1a827ccb016d",
        "52b184a746d34cfbd51d1e39decc2b36f920304c2c8a77c092c09221ad78a3c7"
    ],
    "time" : 1517971079,
    "nonce" : 0,
    "bits" : "1a5dc043",
    "difficulty" : 178952.28853461,
    "chainwork" : "00000000000000000000000000000000000000000000001c0c5179d59a00d17f",
    "previousblockhash" : "1dab864555cea797f9889abc5816a73141713f5c65b19e4fdf0e809d65391d56",
    "nextblockhash" : "b0115bcd9dc3517f8fe9456f26d8543398e833722bc56944e4dcb662e4d9dc66",
    "moneysupply" : 55509369.06461308,
    "zPIVsupply" : {
        "1" : 12689.00000000,
        "5" : 14250.00000000,
        "10" : 59960.00000000,
        "50" : 67000.00000000,
        "100" : 204500.00000000,
        "500" : 197000.00000000,
        "1000" : 359000.00000000,
        "5000" : 370000.00000000,
        "total" : 1284399.00000000
    }
}


```

### Genesis block
```
{
    "hash" : "0000041e482b9b9691d98eefb48473405c0b8ec31b76df3797c74a78680ef818",
    "confirmations" : 1024233,
    "size" : 302,
    "height" : 0,
    "version" : 1,
    "merkleroot" : "1b2ef6e2f28be914103a277377ae7729dcd125dfeb8bf97bd5964ba72b6dc39b",
    "acc_checkpoint" : "0000000000000000000000000000000000000000000000000000000000000000",
    "tx" : [
        "61f4bf0581936cd9ea64d537720d9eb08483e5e0273cec15f6fd33ca12ea7f61"
    ],
    "time" : 1454124731,
    "nonce" : 2402015,
    "bits" : "1e0ffff0",
    "difficulty" : 0.00024414,
    "chainwork" : "0000000000000000000000000000000000000000000000000000000000100010",
    "nextblockhash" : "000005504fa4a6766e854b2a2c3f21cd276fd7305b84f416241fd4431acbd12d",
    "moneysupply" : 0.00000000,
    "zPIVsupply" : {
        "1" : 0.00000000,
        "5" : 0.00000000,
        "10" : 0.00000000,
        "50" : 0.00000000,
        "100" : 0.00000000,
        "500" : 0.00000000,
        "1000" : 0.00000000,
        "5000" : 0.00000000,
        "total" : 0.00000000
    }
}
```

### What is actually bootstrap.dat file?

In 2012, the Bitcoin blockchain was growing to 10+ gigabytes and downloading the entire chain from the p2p network was taking an excessive amount of time (multiple days) due to inefficiencies in the way nodes shared block data. In order make it easier to setup a full node, a snapshot of the blockchain data [was distributed](https://bitcointalk.org/index.php?topic=145386.0) by [Jeff Garzik](https://github.com/jgarzik) as a file named bootstrap.dat using BitTorrent. Starting with version 0.8 bitcoind will load and validate initial blockchain data from any file named bootstrap.dat found in its [data directory](https://en.bitcoin.it/wiki/Data_directory#Default_Location).

Today, this is actually slower than syncing normally. In Bitcoin Core version 0.10.0+ the p2p sync process was dramatically improved making it faster than using the bootstrap.dat file. This bootstrapping process is therefore obsolete and discouraged.
