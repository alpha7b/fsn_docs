# FSN wallet development guide

This document mainly describes the desposit, withdrawal, transfer, query and other interfaces involved in the development of FSN, such as exchanges, mining pools, wallets, etc., and how to one-click deploy FSN node.

## Deploy FSN node

FSN node supports two deployment methods:

1. docker image one-click deployment, docker image address: https://hub.docker.com/u/fusionnetwork

2. source code compilation and deployment

### 1. Docker deployment

Run the command on a Linux system:

`bash -c "$(curl -fsSL https://raw.githubusercontent.com/FUSIONFoundation/efsn/master/QuickNodeSetup/fsnNode.sh)"`

If you select miner during the deployment process, you need to enter the keystore file content and password. For details, please refer to: https://fusionnetworks.zendesk.com/hc/en-us/categories/360001967614-Staking-On-Fusion-MainNet

### 2. Source code compilation and deployment

1. Synchronize code

`git clone https://github.com/FUSIONFoundation/efsn.git`

2. Compile the source (golang > 1.11):

`cd efsn && make efsn`

3. Run node

`./build/bin/efsn console`

4. Open the RPC interface as a backend synchronized node

`nohup ./build/bin/efsn --datadir ./node1/ --rpc --rpcaddr 0.0.0.0 --rpcapi net,fsn,eth,web3 --rpcport 9001 --rpccorsdomain "*" &`

For test network, please add `--testnet` parameter.

As a synchronized node, it is necessary to open the `--gcmode=archive` parameter to query all historical data. At block height  770,000, it occupies more than 100G of hard disk space. In this mode, it is necessary to prepare server storage space in advance (>300G is recommended).The default non-archive mode runs about 1G, but it is not possible to query some historical data.

## Connect to FSN wallet

FSN node code is forked from [go - ethereum] (https://github.com/ethereum/go-ethereum). The RPC interface is compatible with ETH. Upper application interface is compatible with [web3. Js] (https://github.com/ethereum/web3.js). FSN's Ticket, Asset, Timelock USAN, Swap, Staking functions provides [RPC extension interface](https://github.com/FUSIONFoundation/efsn/wiki/FSN-RPC-API) and [web3 extension interface](https://github.com/FUSIONFoundation/web3-fusion-extend).


