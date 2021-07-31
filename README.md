# Binance Smart Chain node Docker image

## QuickStart

```
- git clone repo
- docker build binance-smart-chain-node-docker -t binance-smart-chain-node //build image
```

```
docker run -d -v /data/bsc:/root --name binance-smart-chain-node \
-p 127.0.0.1:8575:8575 -p 127.0.0.1:8576:8576 -p 127.0.0.1:6060:6060 -p 30311:30311 -p 30311:30311/udp \
binance-smart-chain-node --syncmode snap --cache 4096
```

Blockchain data will be stored at `/data/bsc` folder.

`config.toml` will be created if not exists at `/data/bsc/.bsc/config.toml`

## Check sync status

```
docker exec binance-smart-chain-node bsc attach --exec eth.syncing

docker logs -f binance-smart-chain-node
```

## JSONRPC

* HTTP JSONRPC at port 8545
* WebSocket at 8546
* IPC (unix socket) at /data/bsc/.bsc/geth.ipc

Test it using [geth_linux](https://github.com/binance-chain/bsc/releases) binary: 

```
geth_linux attach http://localhost:8545
geth_linux attach ws://localhost:8546
geth_linux attach /data/bsc/.bsc/geth.ipc
# Last one needs root privileges
```

## More info

[original BSC repo](https://github.com/binance-chain/bsc)
