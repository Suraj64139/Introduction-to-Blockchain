# Blockchain Pratcticals
# Metamask Wallet 
This repository contains my blockchain practical's screenshots and transaction hash.

# Create Metamask Wallet (Sepolia Testnet)
 # Introduction
This is a practical task demonstrate how to create a Metamask wallet and perform a transaction using the Sepolia Testnet.

# Transaction details
Network : Sepolia Testent Amount Sent : 0.05 ETH Transaction hash:<br>
https://sepolia.etherscan.io/tx/0x2cca4b95ae11e4229bfb1290ac21e44fff9c7029453683cbc3bf4ce4cc2c885b Status : Successful

# Getting Sepolia ETH from Faucet
1.Visited google cloud Sepolia Faucet. <br>
2.Logged in with my google account. <br>
3.Entered my Metamask wallet address.<br>
4.Clicked on "Request 0.05 ETH".<br>
5.ETH was sent to my wallet within a few seconds.<br>
6.Verified the transaction on sepolia Etherscan.<br>



# Hyperledger-Fabric
<br>
# 1. Install Golang <br>
```
sudo apt install golang-go
```
<br>
Installs Golang, which is necessary for running Hyperledger Fabric binaries.
<br>

# Screenshot
<br>

![image alt](https://github.com/Suraj64139/Introduction-to-Blockchain/blob/3fe434e77a455a2f1d89afd574cc2efb9937357d/Screenshot%202025-04-14%20165201.png)



# 2. Check Docker Version
```
docker --version
```
<br>
Verifies that Docker is installed and running correctly.
<br>
# Screenshot
<br>

![image alt](https://github.com/Suraj64139/Introduction-to-Blockchain/blob/fad6e939efb493a5dfa73b8162baf19620e55dbe/Screenshot%202025-04-14%20165256.png)


# 3. Check Docker Compose Version
```
docker compose version
```
<br>
Verifies the installation of Docker Compose.
<br>
# Screenshot

![image alt](https://github.com/Suraj64139/Introduction-to-Blockchain/blob/f0e7030e2934003edd227856f12738ef5f78c4f6/Screenshot%202025-04-14%20165406.png)


# 4. List Files in Current Directory
```
ls
```
<br>
Shows the list of files and folders in the current directory.

# 5. Clone the Fabric Samples Repository and Move into the Cloned Folder
```
git clone https://github.com/fabric-samples.git; cd fabric-samples
```
<br>
Downloads the official Hyperledger Fabric sample code from GitHub.
<br>
Enters the cloned folder where Fabric examples are available.
<br>
# Screenshot

![image alt](https://github.com/Suraj64139/Introduction-to-Blockchain/blob/a412e11ccf757b0f3b822865b25107a96a146c2c/Screenshot%202025-04-14%20165816.png)



# 6. Download Fabric Binaries
```
curl -sSL https://bit.ly/2ysbOFE | bash -s
```
<br>
Downloads necessary Fabric binaries and Docker images like peer, orderer, and cryptogen.
<br>
# Screenshot


![image alt](https://github.com/Suraj64139/Introduction-to-Blockchain/blob/ca0f84356a691dc6682a0bc77347ffdfe86e14eb/Screenshot%202025-04-14%20165931.png)
<br>

![image alt](https://github.com/Suraj64139/Introduction-to-Blockchain/blob/2337089bd13809a3d510b910077ad7ecb3ce270c/Screenshot%202025-04-14%20165957.png)


# 7. Enter the Test Network Directory
```
cd test-network
```
<br>
Navigates to the directory that contains scripts for running a sample Fabric network.
<br>
# Screenshot


![image alt](https://github.com/Suraj64139/Introduction-to-Blockchain/blob/3c5672e4da437766ad0b846cb3cfa0b02061a965/Screenshot%202025-04-14%20170312.png)


# 8. View the Network Script
```
./network.sh
```
<br>
Shows the options available with the network.sh script.
<br>
# Screenshot

![image alt](https://github.com/Suraj64139/Introduction-to-Blockchain/blob/5a4cb5c56549fe0e8ded50e1e58ee57e020eaa2c/Screenshot%202025-04-14%20170340.png)
<br>


# 9. Start the Fabric Network
```
./network.sh up
```
<br>
Starts the network by launching peer, orderer, and CA containers, and generates the required cryptographic materials.
<br>
# Screenshot
<br>

![image alt](https://github.com/Suraj64139/Introduction-to-Blockchain/blob/d5e2ad3d9d254e803597461ce181c49d3b97c6c7/Screenshot%202025-04-14%20170408.png)


# 10. Create a Channel
```
./network.sh createChannel
```
<br>
Creates a default channel (usually named mychannel) and joins the peers to it.
<br>
# Screenshot
<br>

![image alt](https://github.com/Suraj64139/Introduction-to-Blockchain/blob/b7d42d82b8e413f468afb6713ac7bfb01565fbd1/Screenshot%202025-04-14%20170433.png)
<br>


![image alt](https://github.com/Suraj64139/Introduction-to-Blockchain/blob/ab7222491cdb67b6f7bcbe52e2876b05f6c4ccfe/Screenshot%202025-04-14%20170452.png)

# 11. Shut Down the Network
```
./network.sh down
```
<br>
Stops all containers and deletes the crypto material and artifacts created during the setup.
<br>
# Screenshot





