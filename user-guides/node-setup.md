# Node Setup

If you would like to setup a general node on your local machine to participate and store data for the Blockchain, the you can do so by following these step:

1. Download the Genesis.JSON file from here.
2. Execute this bash script.

```
DATA_PATH="./reapchain_data/1"
rm -rf $DATA_PATH

./reapchaind init my-node --chain-id reapchain --home $DATA_PATH

cp ---DOWNLOADED-GENESIS-FILE---  $DATA_PATH/config/genesis.json

sed -i 's/allow_duplicate_ip = false/allow_duplicate_ip = true/g' $DATA_PATH/config/config.toml

sed -i "s/persistent_peers = .*/persistent_peers = \"dc5df6f60fde5882e849719227b4a3e34e78b5e5@3.37.240.100:27100/\"/g" $DATA_PATH/config/config.toml
./reapchaind start --home $DATA_PATH 

```
