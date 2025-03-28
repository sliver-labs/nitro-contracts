# Arbitrum Nitro Rollup Contracts
> See project specific content [below](#semicolon-fingers)

This is the package with the smart contract code that powers Arbitrum Nitro and Espresso integration.
It includes the rollup and fraud proof smart contracts, as well as interfaces for interacting with precompiles.

## Deploy contracts to Sepolia

### 1. Compile contracts

Compile these contracts locally by running

```bash
git clone https://github.com/offchainlabs/nitro-contracts
cd nitro-contracts
yarn install
yarn build
yarn build:forge
```

### 2. Setup environment variables and config files

Copy `.env.sample.goerli` to `.env` and fill in the values. Add an [Etherscan api key](https://docs.etherscan.io/getting-started/viewing-api-usage-statistics), [Infura api key](https://docs.infura.io/dashboard/create-api) and a private key which has some funds on sepolia.
This private key will be used to deploy the rollup. We have already deployed a `ROLLUP_CREATOR_ADDRESS` which has all the associated espresso contracts initialized.

If you want to deploy your own rollup creator, you can leave the `ROLLUP_CREATOR_ADDRESS` empty and follow the steps on step 3.

If you want to use the already deployed `RollupCreator`, you can update the `ROLLUP_CREATOR_ADDRESS` with the address of the deployed rollup creator [here](espresso-deployments/sepolia.json) and follow the steps on step 4 to create the rollup.

### 3. Deploy Rollup Creator and initialize the espresso contracts

Run the following command to deploy the rollup creator and initialize the espresso contracts.

`npx hardhat run scripts/deployment.ts --network sepolia`

This will deploy the rollup creator and initialize the espresso contracts.

### 4. Create the rollup

Change the `config.ts.example` to `config.ts` and update the config specific to your rollup. Then run the following command to create the rollup if you haven't already done so.

`npx hardhat run scripts/createEthRollup.ts --network sepolia`

## Deployed contract addresses

Deployed contract addresses can be found in the [espress-deployments folder](./espresso-deployments/).

## License

Nitro is currently licensed under a [Business Source License](./LICENSE.md), similar to our friends at Uniswap and Aave, with an "Additional Use Grant" to ensure that everyone can have full comfort using and running nodes on all public Arbitrum chains.

The Additional Use Grant also permits the deployment of the Nitro software, in a permissionless fashion and without cost, as a new blockchain provided that the chain settles to either Arbitrum One or Arbitrum Nova.

For those that prefer to deploy the Nitro software either directly on Ethereum (i.e. an L2) or have it settle to another Layer-2 on top of Ethereum, the [Arbitrum Expansion Program (the "AEP")](https://docs.arbitrum.foundation/assets/files/Arbitrum%20Expansion%20Program%20Jan182024-4f08b0c2cb476a55dc153380fa3e64b0.pdf) was recently established. The AEP allows for the permissionless deployment in the aforementioned fashion provided that 10% of net revenue is contributed back to the Arbitrum community in accordance with the requirements of the AEP.


## Semicolon Fingers
> Information regarding semicolon fingers

- Chain ID :: `1066601` (testnet) _and `16661` (mainnet)_
- Owner address :: `0x96e03e38aD4B5EF728f4C5F305eddBB509B652d0` ([sepolia](https://sepolia.arbiscan.io/address/0x96e03e38aD4B5EF728f4C5F305eddBB509B652d0), [arbOne](https://arbiscan.io/address/0x96e03e38aD4B5EF728f4C5F305eddBB509B652d0))
- Secondary address :: `0x9378Bc37A3d5668AdB1377dF6c2F8e23A95bcDDe`

### Contracts

| Contract | Sepolia | ArbOne |
| :--- | :---: | :---: |
| Block Number | [`136686442`](https://sepolia.arbiscan.io/block/136686442) | |
| **proxies** | <hr/> | |
| [RollupProxy](src/rollup/RollupProxy.sol) | [`0x74bF5fEbc2114E6A348D7e164Bc0f3B194B7C57d`](https://sepolia.arbiscan.io/address/0x74bF5fEbc2114E6A348D7e164Bc0f3B194B7C57d) | |
| Inbox (proxy) | [`0xCD3De7052c0DC752631DddABE4fcd1C5c40045df`](https://sepolia.arbiscan.io/address/0xCD3De7052c0DC752631DddABE4fcd1C5c40045df) | |
| Outbox (proxy) | [`0x708e766445720220A1C471965CB337505f4720f9`](https://sepolia.arbiscan.io/address/0x708e766445720220A1C471965CB337505f4720f9) | |
| rollupEventInbox (proxy) | [`0x905e03B6abC969BAe7f3A5D578A15FE4e43161cC`](https://sepolia.arbiscan.io/address/0x905e03B6abC969BAe7f3A5D578A15FE4e43161cC) | |
| challengeManager (proxy) | [`0x5Fa27FE03a12944460c0e2C30a21De9BD214AF41`](https://sepolia.arbiscan.io/address/0x5Fa27FE03a12944460c0e2C30a21De9BD214AF41) | |
| AdminProxy (proxy) | [`0x81022Ac78076d38d867119e0cAcC39FD1fAA3057`](https://sepolia.arbiscan.io/address/0x81022Ac78076d38d867119e0cAcC39FD1fAA3057) | |
| SequencerInbox (proxy) | [`0x50791a160C7A4C9b004FE52952F25F53F7Bb6F2E`](https://sepolia.arbiscan.io/address/0x50791a160C7A4C9b004FE52952F25F53F7Bb6F2E) | |
| Bridge (proxy) | [`0xb8771932743aBde3Fb2813A7c0f2dec4399Ffc95`](https://sepolia.arbiscan.io/address/0xb8771932743aBde3Fb2813A7c0f2dec4399Ffc95) | |
| UpgradeExecutor (proxy) | [`0xefF62a54E3279159cc4162B44AB804E0a1Fd8721`](https://sepolia.arbiscan.io/address/0xefF62a54E3279159cc4162B44AB804E0a1Fd8721) | |
| ValidatorUtils (proxy) | [`0x45d55fCC763b7B45a6ADE053dA1124E92233e255`](https://sepolia.arbiscan.io/address/0x45d55fCC763b7B45a6ADE053dA1124E92233e255) | |
| ValidatorWalletCreator (proxy) | [`0x5c630FC1817cB5475Bf67e10d8eF783137477D8F`](https://sepolia.arbiscan.io/address/0x5c630FC1817cB5475Bf67e10d8eF783137477D8F) | |
| **impl** | <hr/> |  |
| [Bridge](./src/bridge/Bridge.sol) | [`0x20392616F9F62c0e939ff57432461C59f0FFAF2A`](https://sepolia.arbiscan.io/address/0x20392616F9F62c0e939ff57432461C59f0FFAF2A) | |
| [Sequencer Inbox](./src/bridge/SequencerInbox.sol) | [`0x83F6a5bF65A6CdFb0a954bcb54f83D407B1efb0f`](https://sepolia.arbiscan.io/address/0x83F6a5bF65A6CdFb0a954bcb54f83D407B1efb0f) | |
| [Inbox](./src/bridge/Inbox.sol) | [`0xe8b94A3c819006f676645B4742a41bBb2d82A7D3`](https://sepolia.arbiscan.io/address/0xe8b94A3c819006f676645B4742a41bBb2d82A7D3) | |
| [RollupEventInbox](./src/rollup/RollupEventInbox.sol) | [`0x9ee41ba435b8CFBF78A1B54eCa656C0846A19305`](https://sepolia.arbiscan.io/address/0x9ee41ba435b8CFBF78A1B54eCa656C0846A19305) | |
| [Outbox](./src/bridge/Outbox.sol) | [`0x8573CF3563196b4aeDfEc7495834337d15F87B6C`](https://sepolia.arbiscan.io/address/0x8573CF3563196b4aeDfEc7495834337d15F87B6C) | |
| [ERC20Bridge](./src/bridge/ERC20Bridge.sol) | [`0xecBBcD5A49acc3995a6aD09c85FcF7550D2b6C42`](https://sepolia.arbiscan.io/address/0xecBBcD5A49acc3995a6aD09c85FcF7550D2b6C42) | |
| [SequencerInbox](./src/bridge/SequencerInbox.sol) | [`0x2ade9e0dfbd6E69805F0B7a0fAcA17593F1fDDde`](https://sepolia.arbiscan.io/address/0x2ade9e0dfbd6E69805F0B7a0fAcA17593F1fDDde) | |
| [ERC20Inbox](./src/bridge/ERC20Inbox.sol) | [`0x92D3659C3307C0AC102fD6a8e2306dd030Cb1bD2`](https://sepolia.arbiscan.io/address/0x92D3659C3307C0AC102fD6a8e2306dd030Cb1bD2) | |
| [ERC20RollupEventInbox](./src/rollup/ERC20RollupEventInbox.sol) | [`0x91ae153eDa47303A9f6A5cc8367143888f7E89ed`](https://sepolia.arbiscan.io/address/0x91ae153eDa47303A9f6A5cc8367143888f7E89ed) | |
| [ERC20Outbox](./src/bridge/ERC20Outbox.sol) | [`0x461df8F14dEc51597f949E4c3aa998a446CC9768`](https://sepolia.arbiscan.io/address/0x461df8F14dEc51597f949E4c3aa998a446CC9768) | |
| [BridgeCreator](./src/rollup/BridgeCreator.sol) | [`0xAa4fF23A6CD4EB2cdE2c93FD9ccc061FEf29D717`](https://sepolia.arbiscan.io/address/0xAa4fF23A6CD4EB2cdE2c93FD9ccc061FEf29D717) | |
| [OneStepProver0](./src/osp/OneStepProver0.sol) | [`0x26F0284FAF8150D361a098925a703CB7b95D8AAd`](https://sepolia.arbiscan.io/address/0x26F0284FAF8150D361a098925a703CB7b95D8AAd) | |
| [OneStepProverMemory](./src/osp/OneStepProverMemory.sol) | [`0x0606E22abe4494B4EB310c5A9C424D21BC3e81d8`](https://sepolia.arbiscan.io/address/0x0606E22abe4494B4EB310c5A9C424D21BC3e81d8) | |
| [OneStepProverMath](./src/osp/OneStepProverMath.sol) | [`0x71e655F2aBD44F97F2A310eC23e869d2d42c8964`](https://sepolia.arbiscan.io/address/0x71e655F2aBD44F97F2A310eC23e869d2d42c8964) | |
| [OneStepProverHostIo](./src/osp/OneStepProverHostIo.sol) | [`0x021Cd87b6B6177574acbD3645d57F351bf2c4279`](https://sepolia.arbiscan.io/address/0x021Cd87b6B6177574acbD3645d57F351bf2c4279) | |
| [OneStepProofEntry](./src/osp/OneStepProofEntry.sol) | [`0xefd87bD0Bef61501cF83E8e1EDa4458A6Ccba8f0`](https://sepolia.arbiscan.io/address/0xefd87bD0Bef61501cF83E8e1EDa4458A6Ccba8f0) | |
| [ChallengeManager](./src/challenge/ChallengeManager.sol) | [`0xf48baaa578E03fff9Cf0fC016DE6703843b008aB`](https://sepolia.arbiscan.io/address/0xf48baaa578E03fff9Cf0fC016DE6703843b008aB) | |
| [RollupAdminLogic](./src/rollup/RollupAdminLogic.sol) | [`0x4B16eF8019d2fec23E45511Ed3031D342C227093`](https://sepolia.arbiscan.io/address/0x4B16eF8019d2fec23E45511Ed3031D342C227093) | |
| [RollupUserLogic](./src/rollup/RollupUserLogic.sol) | [`0x58f172ACfEF95908cf160f17041AFe6523b7dCa8`](https://sepolia.arbiscan.io/address/0x58f172ACfEF95908cf160f17041AFe6523b7dCa8) | |
| [ValidatorUtils](./src/rollup/ValidatorUtils.sol) | [`0x45d55fCC763b7B45a6ADE053dA1124E92233e255`](https://sepolia.arbiscan.io/address/0x45d55fCC763b7B45a6ADE053dA1124E92233e255) | |
| [ValidatorWalletCreator](./src/rollup/ValidatorWalletCreator.sol) | [`0x5c630FC1817cB5475Bf67e10d8eF783137477D8F`](https://sepolia.arbiscan.io/address/0x5c630FC1817cB5475Bf67e10d8eF783137477D8F) | |
| [RollupCreator](./src/rollup/RollupCreator.sol) | [`0xeB57AA3de012A2aEe4A7B63b0C8Ba8c670F5a6eA`](https://sepolia.arbiscan.io/address/0xeB57AA3de012A2aEe4A7B63b0C8Ba8c670F5a6eA) | |
| [DeployHelper](./src/rollup/DeployHelper.sol) | [`0x4E5b06f6fC6C26a008B8b79e7395D7B0d853F68A`](https://sepolia.arbiscan.io/address/0x4E5b06f6fC6C26a008B8b79e7395D7B0d853F68A) | |
| [_RollupProxy_](./src/rollup/RollupProxy.sol) | [`0xF461bC07c6fe9FC4aE2323560eADB2Cd62813f9F`](https://sepolia.arbiscan.io/address/0xF461bC07c6fe9FC4aE2323560eADB2Cd62813f9F) | |