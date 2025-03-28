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
| Block Number | [`136677171`](https://sepolia.arbiscan.io/block/136677171) | |
| --- | | |
| [RollupProxy](src/rollup/RollupProxy.sol) | [`0x444F715E6ECEA6c764cD16298740c64576A76c6A`](https://sepolia.arbiscan.io/address/0x444F715E6ECEA6c764cD16298740c64576A76c6A) | |
| Inbox (proxy) | [`0x1A002Ee708Af6f806D75A10780c813aCaEe309f6`](https://sepolia.arbiscan.io/address/0x1A002Ee708Af6f806D75A10780c813aCaEe309f6) | |
| Outbox (proxy) | [`0x308F5457BE6b903F7501b2D522B66FC7bcEb8a10`](https://sepolia.arbiscan.io/address/0x308F5457BE6b903F7501b2D522B66FC7bcEb8a10) | |
| rollupEventInbox (proxy) | [`0x573E60327545D8b53e2e21038A5A4eABa25E7D4B`](https://sepolia.arbiscan.io/address/0x573E60327545D8b53e2e21038A5A4eABa25E7D4B) | |
| challengeManager (proxy) | [`0x8Dbd902a08E789a4aCfa534C9f113B5b861c35e3`](https://sepolia.arbiscan.io/address/0x8Dbd902a08E789a4aCfa534C9f113B5b861c35e3) | |
| AdminProxy (proxy) | [`0x846C6318e277c9b187A36D200eA8cD92e12c50F4`](https://sepolia.arbiscan.io/address/0x846C6318e277c9b187A36D200eA8cD92e12c50F4) | |
| SequencerInbox (proxy) | [`0xF3b33a6c526dA773bF156d325C0E6C5e6dCcd226`](https://sepolia.arbiscan.io/address/0xF3b33a6c526dA773bF156d325C0E6C5e6dCcd226) | |
| Bridge (proxy) | [`0x89caa9635709eE1d0C4B84731f7A1Cbb2ADa3EDF`](https://sepolia.arbiscan.io/address/0x89caa9635709eE1d0C4B84731f7A1Cbb2ADa3EDF) | |
| UpgradeExecutor (proxy) | [`0xDc2447a502071D4c36CD24a2daDE27311ad4BD3b`](https://sepolia.arbiscan.io/address/0xDc2447a502071D4c36CD24a2daDE27311ad4BD3b) | |
| ValidatorUtils (proxy) | [`0xEb8cad972FDbd5FF3f6f85B40a45CE4D565a1609`](https://sepolia.arbiscan.io/address/0xEb8cad972FDbd5FF3f6f85B40a45CE4D565a1609) | |
| ValidatorWalletCreator (proxy) | [`0x28b6E5A95bDC8b5bfe29f8dCF1947626D9423827`](https://sepolia.arbiscan.io/address/0x28b6E5A95bDC8b5bfe29f8dCF1947626D9423827) | |
| --- | --- | --- |
| [Bridge](./src/bridge/Bridge.sol) | [`0x0A27f7F07B6015cfD458cc95E5586Ce29E66F749`](https://sepolia.arbiscan.io/address/0x0A27f7F07B6015cfD458cc95E5586Ce29E66F749) | |
| [Sequencer Inbox](./src/bridge/SequencerInbox.sol) | [`0xB70aE282941a6f7ADDf7F4c8155A5fA2D99f7E2b`](https://sepolia.arbiscan.io/address/0xB70aE282941a6f7ADDf7F4c8155A5fA2D99f7E2b) | |
| [Inbox](./src/bridge/Inbox.sol) | [`0xcC37a941448F1648f75A2d13f72355D8dDdE2420`](https://sepolia.arbiscan.io/address/0xcC37a941448F1648f75A2d13f72355D8dDdE2420) | |
| [RollupEventInbox](./src/rollup/RollupEventInbox.sol) | [`0xc368132a57C202EfAc9f71506154CD5843254908`](https://sepolia.arbiscan.io/address/0xc368132a57C202EfAc9f71506154CD5843254908) | |
| [Outbox](./src/bridge/Outbox.sol) | [`0x5d16829b94b82ce584d6189091A9b28425FE9F85`](https://sepolia.arbiscan.io/address/0x5d16829b94b82ce584d6189091A9b28425FE9F85) | |
| [ERC20Bridge](./src/bridge/ERC20Bridge.sol) | [`0xc0a426a1C8BDe592Cb8f514ABc72DCf629439e2F`](https://sepolia.arbiscan.io/address/0xc0a426a1C8BDe592Cb8f514ABc72DCf629439e2F) | |
| [SequencerInbox](./src/bridge/SequencerInbox.sol) | [`0x47bC045bF3C94c8DE7c09F718e399192CAa524e7`](https://sepolia.arbiscan.io/address/0x47bC045bF3C94c8DE7c09F718e399192CAa524e7) | |
| [ERC20Inbox](./src/bridge/ERC20Inbox.sol) | [`0x769f9b0D0e8955081926d1067cCe69E5D7c30E0c`](https://sepolia.arbiscan.io/address/0x769f9b0D0e8955081926d1067cCe69E5D7c30E0c) | |
| [ERC20RollupEventInbox](./src/rollup/ERC20RollupEventInbox.sol) | [`0x5de5FA507Ecd039bebc82323ddabBe1e8C0D032c`](https://sepolia.arbiscan.io/address/0x5de5FA507Ecd039bebc82323ddabBe1e8C0D032c) | |
| [ERC20Outbox](./src/bridge/ERC20Outbox.sol) | [`0x22ABE32d9507ce3BFE622f13e1C04Cc9c8048157`](https://sepolia.arbiscan.io/address/0x22ABE32d9507ce3BFE622f13e1C04Cc9c8048157) | |
| [BridgeCreator](./src/rollup/BridgeCreator.sol) | [`0x1F8E6E706e0157BA92709d77Fb744013d9A62CB0`](https://sepolia.arbiscan.io/address/0x1F8E6E706e0157BA92709d77Fb744013d9A62CB0) | |
| [OneStepProver0](./src/osp/OneStepProver0.sol) | [`0x99C76a56dAB5830Db343ADE6d34f27BF7Dc624D2`](https://sepolia.arbiscan.io/address/0x99C76a56dAB5830Db343ADE6d34f27BF7Dc624D2) | |
| [OneStepProverMemory](./src/osp/OneStepProverMemory.sol) | [`0x9721f310B719c2614cD5a8CFBA0689451c8a77E8`](https://sepolia.arbiscan.io/address/0x9721f310B719c2614cD5a8CFBA0689451c8a77E8) | |
| [OneStepProverMath](./src/osp/OneStepProverMath.sol) | [`0x91Ec1e7f6E87ae1Dd1d36918425Fd6A57e2C79A7`](https://sepolia.arbiscan.io/address/0x91Ec1e7f6E87ae1Dd1d36918425Fd6A57e2C79A7) | |
| [OneStepProverHostIo](./src/osp/OneStepProverHostIo.sol) | [`0xA5bABC23787f4B3cf14c5c4f541338b5c047b8a6`](https://sepolia.arbiscan.io/address/0xA5bABC23787f4B3cf14c5c4f541338b5c047b8a6) | |
| [OneStepProofEntry](./src/osp/OneStepProofEntry.sol) | [`0x5D93870a4246EE68239Db3d6f5394103542c2877`](https://sepolia.arbiscan.io/address/0x5D93870a4246EE68239Db3d6f5394103542c2877) | |
| [ChallengeManager](./src/challenge/ChallengeManager.sol) | [`0x768C6681f97857cECF390C1A88E0f67684566656`](https://sepolia.arbiscan.io/address/0x768C6681f97857cECF390C1A88E0f67684566656) | |
| [RollupAdminLogic](./src/rollup/RollupAdminLogic.sol) | [`0x27eDCF66BF754617198823b0874216879326C9F0`](https://sepolia.arbiscan.io/address/0x27eDCF66BF754617198823b0874216879326C9F0) | |
| [RollupUserLogic](./src/rollup/RollupUserLogic.sol) | [`0xe0Af9766439F47D85870707022d456F6AF3a7Ef0`](https://sepolia.arbiscan.io/address/0xe0Af9766439F47D85870707022d456F6AF3a7Ef0) | |
| [ValidatorUtils](./src/rollup/ValidatorUtils.sol) | [`0xEb8cad972FDbd5FF3f6f85B40a45CE4D565a1609`](https://sepolia.arbiscan.io/address/0xEb8cad972FDbd5FF3f6f85B40a45CE4D565a1609) | |
| [ValidatorWalletCreator](./src/rollup/ValidatorWalletCreator.sol) | [`0x28b6E5A95bDC8b5bfe29f8dCF1947626D9423827`](https://sepolia.arbiscan.io/address/0x28b6E5A95bDC8b5bfe29f8dCF1947626D9423827) | |
| [RollupCreator](./src/rollup/RollupCreator.sol) | [`0xc9B07fA60c925c3b1764738AB35551A408e74048`](https://sepolia.arbiscan.io/address/0xc9B07fA60c925c3b1764738AB35551A408e74048) | |
| [DeployHelper](./src/rollup/DeployHelper.sol) | [`0x5E9F1a64594ab52a376933a6E5e57Cdf32ad8F91`](https://sepolia.arbiscan.io/address/0x5E9F1a64594ab52a376933a6E5e57Cdf32ad8F91) | |
| [_RollupProxy_](./src/rollup/RollupProxy.sol) | [`0xe046540801b82C40aFf65d17b7D4206111e6fD1a`](https://sepolia.arbiscan.io/address/0xe046540801b82C40aFf65d17b7D4206111e6fD1a) | |