# G1G2 Contract Deployment Demo

This project demonstrates how to use hardhat or foundry to deploy a contract to g1g2 rollup network.

## Prerequisites

- Access to G1G2's Alpha Testnet: https://alpha.g1g2.xyz
- Network setup: https://alpha.g1g2.xyz/doc/setup


## Deploy with Hardhat

1. If you haven't already, install [nodejs](https://nodejs.org/en/download/) and [yarn](https://classic.yarnpkg.com/lang/en/docs/install).
2. Run `yarn install` to install dependencies.
3. Create a `.env` file following the example `.env.example` in the root directory. Change `PRIVATE_KEY` to your own account private key in the `.env`.
4. Run `yarn compile` to compile the contract.
5. Run `yarn deploy:alpha` to deploy the contract on the G1G2 Alpha Testnet.
6. Run `yarn test` for hardhat tests.


## Deploy with Foundry

1. Install Foundry.
    ```shell
    curl -L https://foundry.paradigm.xyz | bash
    foundryup
    ```
2. Build the project.
    ```
    forge build
    ```
3. Deploy the contract.
    ```
    forge create --rpc-url https://alpha.g1g2.xyz/l2 \
      --value <lock_amount> \
      --constructor-args <unlock_time> \
      --private-key <your_private_key> \
      --legacy \
      contracts/Lock.sol:Lock
    ```
  - `<lock_amount>` is the amount of `TSETH` to be locked in the contract. Try setting this to some small amount, like `0.0000001ether`.
  - `<unlock_time>` is the Unix timestamp after which the funds locked in the contract will become available for withdrawal. Try setting this to some Unix timestamp in the future, like `1696118400` (this Unix timestamp corresponds to October 1, 2023).
  
  For example:
  ```
  forge create --rpc-url https://alpha.g1g2.xyz/l2 --value 0.00000000002ether --constructor-args 1696118400 --private-key <your private key> --legacy contracts/Lock.sol:Lock
  ```
  
## Support

Join our Discord: https://discord.gg/egXKdrSWpb
