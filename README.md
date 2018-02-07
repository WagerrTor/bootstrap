# bootstrap file (blockchain)

### How to install

### Bootstrap the Blockchain Synchronization

Normally the SomeCoin client will download the transaction and network information, called the blockchain, from the network by syncing with the other clients. This process can take quite some time as the [SomeCoin blockchain](https://blockchain.info/charts/blocks-size) is growing bigger and bigger for each day. Luckily there is a safe and fast way to speed up this process. We'll show you how to bootstrap your blockchain to bring your client up to speed in just a few simple steps.

### Requirements

- A fresh install of the somecoin client software.

**For Windows users:**
Open explorer, and type into the address bar:

	%APPDATA%\SomeCoin
    
This will open up the data folder. It should look like the image below. Copy over the bootstrap.dat from your download folder to this directory.

**For OSX users:**
Open Finder by pressing Press [shift] + [cmd] + [g] and enter:

	~/Library/Application Support/SomeCoin/
    
**For Linux users:**
The directory is hidden in your User folder. Go to:

	~/.somecoin/
    
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
    1. Go to the folder where the blocks are. In this case SomeCoin's folder (it's the same for other somecoin forks)

            ```            
            cd "Library/Application Support/SomeCoin/blocks/"
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

    set SOMECOINDATADIR=%APPDATA%\SomeCoin\blocks
    for /F %%x in ('dir /B/D/ON %SOMECOINDATADIR%\blk*.*') do (
      IF NOT [!B!] == [] set B=!B!+
      set FILENAME=%SOMECOINDATADIR%\%%x
      set B=!B!"!FILENAME!"
    )
    copy /b %B% bootstrap.dat
    ```

### Links - How to create my own bootstrap file

  - **How to for Windows, Linux and Mac users**
    - For [Linux/Mac](./../../#how-to-create-my-own-bootstrap-on-linuxmac-method-2) users
    - For [Windows](./../../#how-to-create-my-own-bootstrap-on-windows-method-2) users
  - For advanced users - [manually](./../../#how-to-create-my-own-bootstrap)

### What is actually bootstrap.dat file?

In 2012, the Bitcoin blockchain was growing to 10+ gigabytes and downloading the entire chain from the p2p network was taking an excessive amount of time (multiple days) due to inefficiencies in the way nodes shared block data. In order make it easier to setup a full node, a snapshot of the blockchain data [was distributed](https://bitcointalk.org/index.php?topic=145386.0) by [Jeff Garzik](https://github.com/jgarzik) as a file named bootstrap.dat using BitTorrent. Starting with version 0.8 bitcoind will load and validate initial blockchain data from any file named bootstrap.dat found in its [data directory](https://en.bitcoin.it/wiki/Data_directory#Default_Location).

Today, this is actually slower than syncing normally. In Bitcoin Core version 0.10.0+ the p2p sync process was dramatically improved making it faster than using the bootstrap.dat file. This bootstrapping process is therefore obsolete and discouraged.
