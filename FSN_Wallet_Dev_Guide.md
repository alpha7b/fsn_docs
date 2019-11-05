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

4. Open RPC interface for the backend synchronization node

`nohup ./build/bin/efsn --datadir ./node1/ --rpc --rpcaddr 0.0.0.0 --rpcapi net,fsn,eth,web3 --rpcport 9001 --rpccorsdomain "*" &`

For test network, please add '--testnet' parameter.


