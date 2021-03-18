# Istanbul extraData Config File


## Dependencies
- [istanbul-tools](https://github.com/getamis/istanbul-tools)
- [ethereum-private-key-to-address](https://www.npmjs.com/package/ethereum-private-key-to-address)

The config.toml in this repo is the configuration file required by the `istanbul-tools` command used to create the `extraData` field for the `istanbul` consensus.
This file contains the list of Ethereum addresses generated from the *nodekeys*. To generate the ethereum address starting from the node's private key use the `ethereum-private-key-to-address` tool.
