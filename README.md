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
| Block Number | [`136641312`](https://sepolia.arbiscan.io/block/136641312) | |
| --- | | |
| [RollupProxy](src/rollup/RollupProxy.sol) | [`0x2d76669A245923724afED0a90D882Cc69B0E160b`](https://sepolia.arbiscan.io/address/0x2d76669A245923724afED0a90D882Cc69B0E160b) | |
| Inbox (proxy) | [`0x04753159d7870d3d818199241653734f7467479A`](https://sepolia.arbiscan.io/address/0x04753159d7870d3d818199241653734f7467479A) | |
| Outbox (proxy) | [`0x43A9365cbc3DaCF9456D90b52BcF4E79D4D2d0bf`](https://sepolia.arbiscan.io/address/0x43A9365cbc3DaCF9456D90b52BcF4E79D4D2d0bf) | |
| rollupEventInbox (proxy) | [`0x5378263B31277d8947d96c8109C713A29ab75a41`](https://sepolia.arbiscan.io/address/0x5378263B31277d8947d96c8109C713A29ab75a41) | |
| challengeManager (proxy) | [`0xEFdcE02b77a07Ec931a59ff16b2a46558E09A4C4`](https://sepolia.arbiscan.io/address/0xEFdcE02b77a07Ec931a59ff16b2a46558E09A4C4) | |
| AdminProxy (proxy) | [`0xf44C2D4F255D3DC5Fe99304EbF36F96E649C5Ac7`](https://sepolia.arbiscan.io/address/0xf44C2D4F255D3DC5Fe99304EbF36F96E649C5Ac7) | |
| SequencerInbox (proxy) | [`0xeb586ADc16b7BA2B575A6AFC901Ab293C0feA7CB`](https://sepolia.arbiscan.io/address/0xeb586ADc16b7BA2B575A6AFC901Ab293C0feA7CB) | |
| Bridge (proxy) | [`0x8C076C00465b97D7ad949F61D018dD8139347Cb4`](https://sepolia.arbiscan.io/address/0x8C076C00465b97D7ad949F61D018dD8139347Cb4) | |
| ValidatorUtils (proxy) | [`0x002CdA7f3A37f2dbE949c1e72f584Ded51bE2f18`](https://sepolia.arbiscan.io/address/0x002CdA7f3A37f2dbE949c1e72f584Ded51bE2f18) | |
| ValidatorWalletCreator (proxy) | [`0x151Cb2fB60Eb76bE30A68991AB8A667eF445dbb8`](https://sepolia.arbiscan.io/address/0x151Cb2fB60Eb76bE30A68991AB8A667eF445dbb8) | |
| --- | --- | --- |
| [Bridge](./src/bridge/Bridge.sol) | [`0x004bb5E37b305aAae08B578507e9Ec452de32f42`](https://sepolia.arbiscan.io/address/0x004bb5E37b305aAae08B578507e9Ec452de32f42) | |
| [Sequencer Inbox](./src/bridge/SequencerInbox.sol) | [`0xa0c4CeBa57F26417B8D17B656Ae6dB3B20ec8FFf`](https://sepolia.arbiscan.io/address/0xa0c4CeBa57F26417B8D17B656Ae6dB3B20ec8FFf) | |
| [Inbox](./src/bridge/Inbox.sol) | [`0x964d85d9D41615450dFC90c6571a9bF552aCE015`](https://sepolia.arbiscan.io/address/0x964d85d9D41615450dFC90c6571a9bF552aCE015) | |
| [RollupEventInbox](./src/rollup/RollupEventInbox.sol) | [`0xf9C0ecAfBA977cA30DE65dc7a4D0c37727D32D65`](https://sepolia.arbiscan.io/address/0xf9C0ecAfBA977cA30DE65dc7a4D0c37727D32D65) | |
| [Outbox](./src/bridge/Outbox.sol) | [`0x36de6a1D34a302c6671BeadE36df4C6Cf992c5A7`](https://sepolia.arbiscan.io/address/0x36de6a1D34a302c6671BeadE36df4C6Cf992c5A7) | |
| [ERC20Bridge](./src/bridge/ERC20Bridge.sol) | [`0x5cbB0aAC23a38453daBE7971812FB52e804853F1`](https://sepolia.arbiscan.io/address/0x5cbB0aAC23a38453daBE7971812FB52e804853F1) | |
| [SequencerInbox](./src/bridge/SequencerInbox.sol) | [`0xCc0d712200F3EC7Fb2fF41D39ae5399b05EE9E46`](https://sepolia.arbiscan.io/address/0xCc0d712200F3EC7Fb2fF41D39ae5399b05EE9E46) | |
| [ERC20Inbox](./src/bridge/ERC20Inbox.sol) | [`0xA7AFF26156ac7ff2Bdc9D8578dFbA8988cdF16d8`](https://sepolia.arbiscan.io/address/0xA7AFF26156ac7ff2Bdc9D8578dFbA8988cdF16d8) | |
| [ERC20RollupEventInbox](./src/rollup/ERC20RollupEventInbox.sol) | [`0xB47519713BFd4Db870e5034F1b46c75728DC1f2A`](https://sepolia.arbiscan.io/address/0xB47519713BFd4Db870e5034F1b46c75728DC1f2A) | |
| [ERC20Outbox](./src/bridge/ERC20Outbox.sol) | [`0xA608fa00A90d087D0C1857dB3DaF19064c084382`](https://sepolia.arbiscan.io/address/0xA608fa00A90d087D0C1857dB3DaF19064c084382) | |
| [BridgeCreator](./src/rollup/BridgeCreator.sol) | [`0xe237F3E6E200c3Ca86d43589c29AFbc902475A12`](https://sepolia.arbiscan.io/address/0xe237F3E6E200c3Ca86d43589c29AFbc902475A12) | |
| [OneStepProver0](./src/osp/OneStepProver0.sol) | [`0x67c09cbc133f275ad92a75000C284f3B0E7bd069`](https://sepolia.arbiscan.io/address/0x67c09cbc133f275ad92a75000C284f3B0E7bd069) | |
| [OneStepProverMemory](./src/osp/OneStepProverMemory.sol) | [`0x83F4Ca37e100D9A8a302fF2ED55Bf0E72209617F`](https://sepolia.arbiscan.io/address/0x83F4Ca37e100D9A8a302fF2ED55Bf0E72209617F) | |
| [OneStepProverMath](./src/osp/OneStepProverMath.sol) | [`0x935B442E21F92faab695E443cB35B24B18182DD1`](https://sepolia.arbiscan.io/address/0x935B442E21F92faab695E443cB35B24B18182DD1) | |
| [OneStepProverHostIo](./src/osp/OneStepProverHostIo.sol) | [`0xCDb6C8e801ef5da50ab854457e118d9bD38Da341`](https://sepolia.arbiscan.io/address/0xCDb6C8e801ef5da50ab854457e118d9bD38Da341) | |
| [OneStepProofEntry](./src/osp/OneStepProofEntry.sol) | [`0x95A67279a3847c0ea5f363053ADe7F818F04793D`](https://sepolia.arbiscan.io/address/0x95A67279a3847c0ea5f363053ADe7F818F04793D) | |
| [ChallengeManager](./src/challenge/ChallengeManager.sol) | [`0x3ee63272313F8Bd00E2FEDb805662907B9266Af9`](https://sepolia.arbiscan.io/address/0x3ee63272313F8Bd00E2FEDb805662907B9266Af9) | |
| [RollupAdminLogic](./src/rollup/RollupAdminLogic.sol) | [`0x14b236AAe5CeeA87267b02e314eddB260e495e7F`](https://sepolia.arbiscan.io/address/0x14b236AAe5CeeA87267b02e314eddB260e495e7F) | |
| [RollupUserLogic](./src/rollup/RollupUserLogic.sol) | [`0x8e601AAEcB2078DC7228541DF17A1dC54C271a5d`](https://sepolia.arbiscan.io/address/0x8e601AAEcB2078DC7228541DF17A1dC54C271a5d) | |
| [ValidatorUtils](./src/rollup/ValidatorUtils.sol) | [`0x002CdA7f3A37f2dbE949c1e72f584Ded51bE2f18`](https://sepolia.arbiscan.io/address/0x002CdA7f3A37f2dbE949c1e72f584Ded51bE2f18) | |
| [ValidatorWalletCreator](./src/rollup/ValidatorWalletCreator.sol) | [`0x151Cb2fB60Eb76bE30A68991AB8A667eF445dbb8`](https://sepolia.arbiscan.io/address/0x151Cb2fB60Eb76bE30A68991AB8A667eF445dbb8) | |
| [RollupCreator](./src/rollup/RollupCreator.sol) | [`0x03AfbdEfA11cf56fC7d0bd6F04fF23A0c72C22EC`](https://sepolia.arbiscan.io/address/0x03AfbdEfA11cf56fC7d0bd6F04fF23A0c72C22EC) | |
| [DeployHelper](./src/rollup/DeployHelper.sol) | [`0x0325F6f793525D18cfb665607031f3DC24092632`](https://sepolia.arbiscan.io/address/0x0325F6f793525D18cfb665607031f3DC24092632) | |
| [_RollupProxy_](./src/rollup/RollupProxy.sol) | [`0x235Ae718Ac6aAaE0089349Ca0226F272117075Fa`](https://sepolia.arbiscan.io/address/0x235Ae718Ac6aAaE0089349Ca0226F272117075Fa) | |