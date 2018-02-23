# Build an ethereum blockchain
Tutorial from https://medium.freecodecamp.org/from-what-is-blockchain-to-building-a-blockchain-within-an-hour-4e738efc819d

### 1. Install Ethereum from PPA

    ./01-install-ethereum.sh

### 2. Create the Genesis Block
Create the very first initial block of the chain. The only block without a predecessor.

    ./02-create-genesis-block.sh

### 3. Create the Blockchain
Run a blockchain.

    ./03-run-blockchain.sh

Other nodes will be able to join the network by specifying the enode address
it looks like `enode://492394f34dd6745e4b6c9aa7ee4bc536863e678d956c61c4aa7c7982f0cd8bd1f737e0f155e105e917d3165c4e1227963adeff9de596986251663e5b8e7bfbd9@[::]:30303`
You will have to replace the IP (`[::]`) by your public IP address.

### 4. Create your account and mine some blocks
Open a new terminal

    ./04-launch-console.sh

In the console, run the following commands

    personalAccountNumber = personal.newAccount()

Note down your account number (example: 0xf93d625d3440a6722c4cd65820c43fc8863150f7)

Check how many coins you have in your wallet

    eth.getBalance(personalAccountNumber)

You should have 0 coins
There are 2 ways to get ether into your account, either somebody sends you some , or you mine transaction blocks and get rewarded with ether in turn.
Since you are all alone in your private network at this point, your only option right now is to mine some blocks and get rewarded.
Mining in the real or Main Ethereum blockchain is pretty difficult and would need specialized hardware such as dedicated GPUs. However, mining for blocks in a private chain is easy to do, since we specified the difficulty level to be very low in our genesis file, remember? We can simply start mining using the following code

    miner.start()

After a few minutes, (the DAG must first be generated, then some blocks are mined), run the `eth.getBalance(personalAccountNumber)`

To stop the miner

    miner.stop()
