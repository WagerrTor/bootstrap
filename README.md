# Wagerr bootstrap file

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
 - Block height: `220979`
 - Block hash: `05546d5502001e00ba5845cd6794a66f0150114585a38b7831b2acae86cae218`
 - Tx: `2191554`
 - Date: `2018-07-21 15:18:24`
 - Date (epoch): `1532179104`

### Block 220979
```
{
  "hash": "05546d5502001e00ba5845cd6794a66f0150114585a38b7831b2acae86cae218",
  "confirmations": 2,
  "size": 504,
  "height": 220979,
  "version": 4,
  "merkleroot": "450c12ea240fbcc226867a7be021cf41229bd5642371c90d0a9ee7f10758f159",
  "acc_checkpoint": "677974c9c552aa9b51fb185c9c3944cba2144f6d59f4bfd24c5141534ecd51b8",
  "tx": [
    "a3d44962f41a056f69ed6cabf8f1ea2de21433e2d63dafe2bc701ac6ec8e4342",
    "c70c3f8b9218dfe8d7cf4ed26047a0d3c10a0727eb9d18a41b6faa6bd80db8c6"
  ],
  "time": 1532179104,
  "nonce": 0,
  "bits": "1a10a582",
  "difficulty": 1007836.181222535,
  "chainwork": "00000000000000000000000000000000000000000000003778e28bc23bcfb0da",
  "previousblockhash": "d2bc457137c5447b1c9ac14262f28e3c0601ea5355fc0d34067253eaea6594f1",
  "nextblockhash": "98418423a68c18ca3e494d639fcc0f166faf0c01e68ac1d60f62a632e6c24d04",
  "moneysupply": 55299034.35179498,
  "zWGRsupply": {
    "1": 2019.00000000,
    "5": 1520.00000000,
    "10": 8270.00000000,
    "50": 14000.00000000,
    "100": 62000.00000000,
    "500": 89000.00000000,
    "1000": 293000.00000000,
    "5000": 1870000.00000000,
    "total": 2339809.00000000
  }
}



```

### Genesis block
```
{
  "hash": "000007b9191bc7a17bfb6cedf96a8dacebb5730b498361bf26d44a9f9dcc1079",
  "confirmations": 220445,
  "size": 312,
  "height": 0,
  "version": 1,
  "merkleroot": "c4d06cf72583752c23b819fa8d8cededd1dad5733d413ea1f123f98a7db6af13",
  "acc_checkpoint": "0000000000000000000000000000000000000000000000000000000000000000",
  "tx": [
    "c4d06cf72583752c23b819fa8d8cededd1dad5733d413ea1f123f98a7db6af13"
  ],
  "time": 1518696181,
  "nonce": 96620932,
  "bits": "1e0ffff0",
  "difficulty": 0.000244140625,
  "chainwork": "0000000000000000000000000000000000000000000000000000000000100010",
  "nextblockhash": "000001364c4ed20f1b240810b5aa91fee23ae9b64b6e746b594b611cf6d8c87b",
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
