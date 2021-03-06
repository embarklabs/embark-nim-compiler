embark-nim-compiler
======

Plugin for [Embark](https://github.com/embark-framework/embark) to compile [Nim contracts](https://github.com/status-im/nimplay)

## Installation

### Plugin

In your embark dapp directory:

```npm install embark-nim-compiler --save```
or
```yarn add embark-nim-compiler```

then add embark-nim-compiler to the plugins section in `embark.json`:

```Json
{
  "plugins": {
    "embark-nim-compiler": {
      "setupBlockchainOptions": true,
      "libHeraPath": "path/to/libHera.so"
    }
  }
}
```

- `setupBlockchainOptions`: boolean that when set to `true`, will change the blockchain config for you. If you set this to `false`, you need to set the blockchain config yourself so that it supports eWasm
- `libHeraPath`: string path to the file `libHera.so` that is used to have Geth use Hera as a VM. Not needed if `setupBlockchainOptions` is `false`

Since you need to have Geth+Hera installed, make sure that the built Geth is in your Path or change `ethereumClientBin` in you blockchain config to point to the Geth executable (absolute path).

### Configs

If you plan to use the eWasm testnet, you will need to have an account with tesnet Ether.

You can find the testnet faucet here: http://ewasm.ethereum.org/faucet/

You will need to connect your Metamask extension to the testnet. To do so, either connect it to you local Geth instance or to a hosted node.

Once you have ETH in your account, add it to the `accounts` section in the blockchain config. You can find information on how to do it here: https://embark.status.im/docs/blockchain_accounts_configuration.html

### Temporary endpoint

You can use our temporary endpoint available at `http://159.65.52.177:8545/`.
This endpoint connects to an eWasm testnet node, but we'll probably shut down at some point, so don't rely on it for production.

## Requirements

- [Embark](https://www.npmjs.com/package/embark) 5.0.0 or higher
- A valid eWasm ready node. See https://github.com/ewasm/testnet for more details
- Docker

### Troubleshooting

If you get an error related to docker or the image `jacqueswww/nimclang`, you might need to pull it first manually using:

```docker pull jacqueswww/nimclang```
