This README is obsolete, see the wiki of this repository.

***
## 0. Introduction
This README explains the work I have done on my first internship at XYZ Technology.
Author: Eray Kurtuluş

## 1. How to set up a Bitcoin Lightning Node on a Raspberry Pi
### 1.1. Introduction
Lightning Network is an attempt to solve a few problems that the Bitcoin is suffering: scalability (number of transactions per second), speed (time required to confirm a transaction,), cost (fee to pay for each transaction).

The basic idea is to create a “channel” between 2 participants (let’s say A and B) and place some funds in, for example 1 BTC each. This requires a transaction on the Bitcoin blockchain, that locks the funds in a 2 multisig address.

A and B can now make as many transactions as they want “off-chain”, they just need to exchange an updated “balance-sheet”: that is transaction signed by the other party (so it’s missing one of the signatures) that is not propagated to the bitcoin mainnet (yet), and that pays the updated funds to the participants.

Because the transactions are stored “off-chain”, A and B don’t need to wait for a confirmation from the main blockchain (instant transaction) nor to pay a fee to the mainnet miners (low fees).

At any moment, a participant can make the balance-sheet “real”, signing the latest multisig transaction received from (and signed by) the other party, and broadcasting it as a regular Bitcoin transaction: the channel is now closed.

In this section, we're going to set up a Lightning Node that is connected to this network. We're going to experiment on the Bitcoin testnet blockchain. I've used a headless Raspberry Pi with a fresh Raspbian installation for this, but the steps are very similar on other Linux distributions.

### 1.2. Preparations
#### 1.2.1. Download and Verify the Bitcoin Testnet Blockchain on Your PC
We need to download the Bitcoin testnet blockchain and verify all the blocks and transactions to this date. Doing this on an RPi might take a long time. The testnet blockchain is currently ~30GB. We can download and verify the blockchain on our personal computer and then transfer the files to the RPi using scp. You may skip this and directly download and verify the blockchain on the device you want to set up as a Lightning Node. (Installation instructions will be more detailed for an RPi on the following sections)

Download Bitcoin Core from: https://bitcoincore.org/en/download/

Choose the right option depending on your OS.

Extract the archive and install the software as you normally do. 

Run bitcoind with the command "sudo bitciond -testnet" or -if you want to use the GUI- with the command "sudo bitcoin-qt -testnet".

Start downloading and verifying the blockchain. Later, we will copy this to our RPi.

#### 1.2.2 Install Raspbian Lite to the RPi
Download the latest Raspbian Lite image from: https://www.raspberrypi.org/downloads/raspbian/

Write the image to an SD card, you may follow the instructions on: https://www.raspberrypi.org/documentation/installation/installing-images/

Boot the RPi.

#### 1.2.3 Configure RPi




### A. References
https://medium.com/coinmonks/bitcoin-lightning-network-run-your-node-at-home-for-fun-and-no-profit-da5b61be2ba9
https://stadicus.github.io/RaspiBolt/
