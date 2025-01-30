## Install Docker

### Pull Privasea docker image
```bash
docker pull privasea/acceleration-node-beta
```

### Node program configuration
1. Create directories
```bash
mkdir -p privasea/config && cd privasea
```

2. Get the keystore file
```
docker run -it -v "$HOME/privasea/config:/app/config"  \
privasea/acceleration-node-beta:latest ./node-calc new_keystore
```
* Enter a password for your keystore file

![image](https://github.com/user-attachments/assets/417187be-8d51-4cfc-b90f-1e4c1f5225e8)

* Save the key details
* Save `UTC--2025...` file generated in `/root/privasea/config/` in your local pc

3. Rename the keystore file in the `privasea/config` folder to `wallet_keystore`:
```console
mv $HOME/privasea/config/UTC--*  ./wallet_keystore 
```

### Link node address and reward address
1. Connect a metamask wallet for receiving rewards
2. Press on Set one up now

![image](https://github.com/user-attachments/assets/727c834e-bbc4-47fd-acda-35795ce380b6)

3. Enter your node address saved in previous steps and set up your node
* `KEYSTORE_PASSWORD=`: Replace `password` with your keystore password into the command then execute it
```
docker run  -d   -v "$HOME/privasea/config:/app/config" \
  -e KEYSTORE_PASSWORD=password  \
  privasea/acceleration-node-beta:latest
```
