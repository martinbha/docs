# Node Setup

If you would like to setup a general node on your local machine to participate and store data for the Blockchain, the you can do so by following these step:

* Download the Genesis.json file from [here](https://raw.githubusercontent.com/reapchain/testnets/e9f5839fb7d26f036dd5099e49c9b63d0a208b53/genesis.json).
* Check the integrity of the genesis.json file with this:

```
sha1sum genesis.json
```

* Your output should be the same as the following:&#x20;

```
f2f40bfc58e3812bcbecbeb96b4be9201dd7e9d5  genesis.json
```

* Create a Bash Script using the following as a template

```
#!/bin/bash
DATA_PATH="./reapchain_data/1"
rm -rf $DATA_PATH
./reapchaind init my-node --chain-id mercury --home $DATA_PATH
cp ---DOWNLOADED-GENESIS-FILE---  $DATA_PATH/config/genesis.json
sed -i 's/enable = false/enable = true/g' $DATA_PATH/config/app.toml
sed -i "s/laddr = \"tcp:\/\/127.0.0.1:26657\"/laddr = \"tcp:\/\/------YOUR IP ADDRESS------:27100\"/g" $DATA_PATH/config/config.toml
sed -i "s/laddr = \"tcp:\/\/0.0.0.0:26656\"/laddr = \"tcp:\/\/------YOUR IP ADDRESS------:27000\"/g" $DATA_PATH/config/config.toml
sed -i "s/persistent_peers = .*/persistent_peers = \"8a360cdeed68ae452346e46520136569a86cd783@3.34.158.5:27000\"/g" $DATA_PATH/config/config.toml
./reapchaind start --home $DATA_PATH


```

* Replace "---DOWNLOADED-GENESIS-FILE---" with the path of the downloaded Genesis File
* Replace "------YOUR IP ADDRESS------" with your local IP Address
* Execute the bash.
