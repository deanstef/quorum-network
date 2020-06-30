# quorum-network
This repository contains a simple setup for [Quorum](https://github.com/jpmorganchase/quorum) blockchain platform.

It is based on the [7nodes](https://github.com/jpmorganchase/quorum-examples) example and offers a simple setup of a Quorum network with or without the Tx Manager for Quorum's privacy features, and with these three supported consensus algorithms:
* Raft
* Clique
* Istanbul

With this example one can easily start up a fully-functioning Quorum Ethereum private network consisting of 7 indipendent Quorum nodes. Each node runs in a single docker container abd exposes RPC APIs and a Geth console for testing different consensus, privacy, and all the expected functionality of an Ethereum platform.

## Run the example
1. Make sure you have `<docker-compose>` installed. If not you can follow [this](https://docs.docker.com/compose/install/) to install Docker Compose,
2. Download and run the example
```
git clone https://github.com/deanstef/quorum-network.git
cd quorum-network
docker-compose up -d
```
3. By default this example runs a Quorum network with Tessera privacy managers and Istanbul BFT consensus. To use another consensus and disable the privacy manager, set the environment variables `QUORUM_CONSENSUS=<raft|clique>` `PRIVATE_CONFIG=ignore`
```
PRIVATE_CONFIG=ignore QUORUM_CONSENSUS=raft docker-compose up -d
```
4. Run `docker ps` to show all the quorum containers (7 nodes and 7 tx managers)
5. Run `docker logs <container-name> -f` to view the logs for a particular container or `docker-compose logs -f` to view all the logs
6. Start interact with the network either by accessing the RPC APIs listed [here](https://eth.wiki/json-rpc/API) or by accessing the `geth` Javascript console
```
$ docker exec -it <container-name> geth attach /qdata/dd/geth.ipc
Welcome to the Geth JavaScript console!

instance: Geth/nodeX-<consensus>/v1.7.2-stable/linux-amd64/go1.9.7
coinbase: 0xd8dba507e85f116b1f7e231ca8525fc9008a6966
at block: 70 (Thu, 18 Oct 2018 14:49:47 UTC)
 datadir: /qdata/dd
 modules: admin:1.0 debug:1.0 eth:1.0 istanbul:1.0 miner:1.0 net:1.0 personal:1.0 rpc:1.0 txpool:1.0 web3:1.0
```
7. Shutdown Quorum Network
```
docker-compose down
```
8. Remove all the volumes with the chain data. *note*: This command will delete all the Docker volumes on your machine
```
docker volume prune -f
```
