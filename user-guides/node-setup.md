# Node Setup

If you would like to setup a general node on your local machine to participate and store data for the Blockchain, the you can do so by following these step:

1. Download the Genesis.JSON file from here.
2. Execute this bash script.

```
DATA_PATH="./reapchain_data/1"
rm -rf $DATA_PATH
./reapchaind init my-node --chain-id mercury --home $DATA_PATH
cp ---DOWNLOADED-GENESIS-FILE---  $DATA_PATH/config/genesis.json
sed -i "s/persistent_peers = .*/persistent_peers = \"9ebf4d066ea092a7965e73f3f3d463e9b9162df7@13.124.192.87:27000\"/g" $DATA_PATH/config/config.toml
./reapchaind start --home $DATA_PATH 

```
