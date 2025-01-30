# Set up and operate Privanetix node
Follow this guide to set up and operate Privanetix node
* 1% total supply is allocated privasea node contributors.
* Leaderboard ends in 30 days.
* The node leaderboard is based solely on device performance and node uptime; staked tokens do not influence rankings.
* Make sure you join [ImHuman Application](https://github.com/0xmoei/privaseaAI/blob/main/README.md#8-join-imhuman-application-built-by-privasea) at the end of running the node

![image](https://github.com/user-attachments/assets/749bd88b-94bf-4cea-98b8-342a4e2124ab)

#

## System Requirement
You node's tier relies on your specification. You can run the node on a system with minimum spec

![image](https://github.com/user-attachments/assets/5dcf9fc7-bd82-44c5-a3cb-7a3b68cb07dd)

# Setup Instructions
### 1. Install Dependecies
```
sudo apt-get update && sudo apt-get upgrade -y
sudo apt install curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev  -y
```
### 2. Install Docker
```
sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Test Docker
sudo docker run hello-world
```

### 3. Pull Privasea docker image
```bash
docker pull privasea/acceleration-node-beta
```

### 4. Node program configuration
**1. Create directories**
```bash
mkdir -p privasea/config && cd privasea
```

**2. Get the keystore file**
```
docker run -it -v "$HOME/privasea/config:/app/config"  \
privasea/acceleration-node-beta:latest ./node-calc new_keystore
```
* Enter a password for your keystore file

![image](https://github.com/user-attachments/assets/417187be-8d51-4cfc-b90f-1e4c1f5225e8)

* Save the key details
* Save `UTC--2025...` file generated in `/root/privasea/config/` in your local pc

**3. Rename the keystore file in the `privasea/config` folder to `wallet_keystore`:**
```console
mv $HOME/privasea/config/UTC--*  ./wallet_keystore 
```

### 5. Link node address and reward address
**1. Connect an EVM reward wallet to the [dashboard](https://deepsea-beta.privasea.ai/privanetixNode) to bind your node keystore with your reward wallet**
* You can use a seprate wallet than your node key for your reward wallet
  
**2. Press on Set one up now**

![image](https://github.com/user-attachments/assets/727c834e-bbc4-47fd-acda-35795ce380b6)

**3. Enter your node address saved in previous steps and set up your node**

![image](https://github.com/user-attachments/assets/82885607-9e5f-4312-9580-3595d2eced3d)


### 6. Run Node
**1. Enter the following command to start your node**
* `KEYSTORE_PASSWORD=`: Replace `password` with your keystore password into the command then execute it
```
docker run  -d   -v "$HOME/privasea/config:/app/config" \
  -e KEYSTORE_PASSWORD=password  \
  privasea/acceleration-node-beta:latest
```

**2. Check logs**
```
docker ps -a
```
* Replace `CONTAINER_ID` with the Container ID of the Privasea docker
```
docker logs -f CONTAINER_ID
```

### 7. Stake to your Node
**1. Get faucet [here](https://deepsea-beta.privasea.ai/deepSeaFaucet) for EVM wallet connected to the dashbaord**
* You will receive 1 $TPRAI on Arbitrum Sepolia
* Do not claim faucet with multiple wallets, final rewards are based on Node uptime and performance, not your staked tokens.

**2. Click your node "Details" and Stake 1 $TPRAI on it**

![Screenshot_600](https://github.com/user-attachments/assets/8dea9953-99b7-4546-bbd8-1f1dff526215)

**3. After a few hours, Pre-staking will change to Staked and you start receiving rewards**

![image](https://github.com/user-attachments/assets/5d73dd2d-3b3a-48fd-b428-5015dbaaaee8)

#

# 8. Join ImHuman Application built by Privasea
10% of total supply is allocated to ImHuman app contributors
* You might need to link your node's reward to ImHuman app later before TGE

1. Download mobile app: https://privasea.ai/download-app
2. Create an account
3. Enter boost code: `hhdj2AB`
4. Send Arbitrum ETH to your app wallet
5. Mint your Proof of Humanity NFT for 0.0016 ETH by scanning your face
6. Complete other tasks in the app and claim XPs

![image](https://github.com/user-attachments/assets/8ebe0f30-73e6-4423-ac53-5f47e18fc78c)

