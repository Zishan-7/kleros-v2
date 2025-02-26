# @kleros/kleros-v2-contracts

Smart contracts for Kleros v2

## Deployed Addresses

Refresh the list of deployed contracts by running `./scripts/generateDeploymentsMarkdown.sh`.

#### Chiado

- [ArbitrableExample](https://blockscout.com/gnosis/chiado/address/0xf534e055758884c71304028814Ba25B2CE6903e5)
- [DisputeResolver](https://blockscout.com/gnosis/chiado/address/0x433eD78895df1df7668C40b3e82d54410331F942)
- [ForeignGatewayOnGnosis](https://blockscout.com/gnosis/chiado/address/0x2357ef115E98d171b083105E9b398231206989A3)
- [SortitionSumTreeFactory](https://blockscout.com/gnosis/chiado/address/0xc7e3BF90299f6BD9FA7c3703837A9CAbB5743636)
- [TokenBridge](https://blockscout.com/gnosis/chiado/address/0xbb3c86f9918C3C1d83668fA84e79E876d147fFf2)
- [WETH](https://blockscout.com/gnosis/chiado/address/0x2DFC9c3141268e6eac04a7D6d98Fbf64BDe836a8)
- [WETHFaucet](https://blockscout.com/gnosis/chiado/address/0x22CB016c4b57413ca4DF5F1AC44a0E0d3c69811F)
- [WPNKFaucet](https://blockscout.com/gnosis/chiado/address/0x5898aeE045A25B276369914c3448B72a41758B2c)
- [WrappedPinakionV2](https://blockscout.com/gnosis/chiado/address/0xD75E27A56AaF9eE7F8d9A472a8C2EF2f65a764dd)
- [xKlerosLiquidV2](https://blockscout.com/gnosis/chiado/address/0x34E520dc1d2Db660113b64724e14CEdCD01Ee879)

#### Goerli

- [PNK](https://goerli.etherscan.io/token/0xA3B02bA6E10F55fb177637917B1b472da0110CcC)

#### Arbitrum Goerli

- [PNK](https://goerli.arbiscan.io/token/0x4DEeeFD054434bf6721eF39Aa18EfB3fd0D12610)
- [ArbitrableExample](https://goerli.arbiscan.io/address/0xb0338F2E3D832F3086e5681EAD329520A8d88CD6)
- [BlockHashRNG](https://goerli.arbiscan.io/address/0x68eE49dfD9d76f3386257a3D0e0A85c0A5519bBD)
- [DAI](https://goerli.arbiscan.io/address/0x70A704Dce4cCC00568Cc142C86D07Ec71C944a39)
- [DAIFaucet](https://goerli.arbiscan.io/address/0x82C3FF40B0DB79b84bB97Df7792D759bDfAD1eAb)
- [DisputeKitClassic](https://goerli.arbiscan.io/address/0x0245A93ABd9c5b2d767B2D98cE6d5e612208E474)
- [DisputeResolver](https://goerli.arbiscan.io/address/0xcDC05c8d2EEEe384359Bd22E8631528B6b0564e9)
- [HomeGatewayToGnosis](https://goerli.arbiscan.io/address/0x1807b0049D412a3208d840D74725e404a55E297E)
- [KlerosCore](https://goerli.arbiscan.io/address/0x8Af82E2F8890acb4AB84cbaB3c4C4Eb3E965CF24)
- [PNKFaucet](https://goerli.arbiscan.io/address/0xcc9dA0E6Fe98934781A57C861C939AC36989990d)
- [PolicyRegistry](https://goerli.arbiscan.io/address/0xED503aBA65B28D81444294D1eAa5d84CeFdC2C58)
- [RandomizerRNG](https://goerli.arbiscan.io/address/0xa90f7D2e35718FDE9AD96c8B6667AFcAa4BEfd4d)
- [SortitionModule](https://goerli.arbiscan.io/address/0x5Ae75Db8B66B574b2c5C29eE4D32cc9Fe62bfdEE)
- [WETH](https://goerli.arbiscan.io/address/0xddE1b84E43505432Fdf5F810ebB9373dD37e9230)
- [WETHFaucet](https://goerli.arbiscan.io/address/0x87Efe303Cbc866320c14805C4D6cd04f426FBB17)

## Getting Started

### Install the Dependencies

```bash
yarn install
```

### Run Tests

```bash
yarn test
```

### Compile the Contracts

```bash
yarn build
```

### Run Linter on Files

```bash
yarn lint
```

### Fix Linter Issues on Files

```bash
yarn fix
```

### Deploy Instructions

**NOTICE:** the commands below work only if you are inside the `contracts/` directory.

#### 0. Set the Environment Variables

Copy `.env.example` file as `.env` and edit it accordingly.

```bash
cp .env.example .env
```

The following env vars are required:

- `PRIVATE_KEY`: the private key of the deployer account used for the testnets.
- `MAINNET_PRIVATE_KEY`: the private key of the deployer account used for Mainnet.
- `INFURA_API_KEY`: the API key for infura.

The ones below are optional:

- `ETHERSCAN_API_KEY`: to verify the source of the newly deployed contracts on **Etherscan**.
- `ARBISCAN_API_KEY`: to verify the source of the newly deployed contracts on **Arbitrum**.
- `GNOSISSCAN_API_KEY`: to verify the source of the newly deployed contracts on **Gnosis chain**.

#### 1. Update the Constructor Parameters (optional)

If some of the constructor parameters (such as the Meta Evidence) needs to change, you need to update the files in the `deploy/` directory.

#### 2. Deploy to a Local Network

The complete deployment is multi-chain, so a deployment to the local network can only simulate either the Home chain or the Foreign chain.

**Shell 1: the node**

```bash
yarn hardhat node --tags nothing
```

**Shell 2: the deploy script**

```bash
yarn deploy --network localhost --tags <Arbitration|VeaMock|ForeignGatewayOnEthereum|HomeGateway>
```

#### 3. Deploy to Public Testnets

```bash
# ArbitrumGoerli to Chiado
yarn deploy --network arbitrumGoerli --tags Arbitration
yarn deploy --network chiado --tags ForeignGatewayOnGnosis
yarn deploy --network chiado --tags KlerosLiquidOnGnosis
yarn deploy --network chiado --tags ForeignArbitrable
yarn deploy --network arbitrumGoerli --tags HomeGatewayToGnosis

# Goerli
yarn deploy --network arbitrumGoerli --tags Arbitration
yarn deploy --network goerli --tags ForeignGatewayOnEthereum
yarn deploy --network arbitrumGoerli --tags HomeGatewayToEthereum
```

The deployed addresses should be displayed to the screen after the deployment is complete. If you missed them, you can always go to the `deployments/<network>` directory and look for the respective file.

#### Running Test Fixtures

**Shell 1: the node**

```bash
yarn hardhat node --tags Arbitration,VeaMock
```

**Shell 2: the test scripts**

```bash
yarn test --network localhost
```

#### 4. Verify the Source Code

This must be done for each network separately.

```bash
# explorer
yarn etherscan-verify --network <arbitrumGoerli|arbitrum|chiado|gnosischain|goerli|mainnet>

# sourcify
yarn sourcify --network <arbitrumGoerli|arbitrum|chiado|gnosischain|goerli|mainnet>

```

## Ad-hoc procedures

### Populating the policy registry and courts

#### 1/ Export the registry data from V1

```bash
for network in mainnet gnosischain
do
  yarn hardhat run scripts/getPoliciesV1.ts  --network $network | tee config/policies.v1.$network.json
  yarn hardhat run scripts/getCourtsV1.ts --network $network | tee config/courts.v1.$network.json
done
```

#### 2/ Import the data to V2 - Local Network

:warning: By default this script populates from `*.mainnet.json`. To populate from `*.gnosischain.json`, set the variable `USE_GNOSIS` to true inside [scripts/populateCourts.ts](scripts/populateCourts.ts).

:warning: It is possible to switch to testnet-friendly court parameters by setting the variable `TESTING_PARAMETERS` to true inside [scripts/populateCourts.ts](scripts/populateCourts.ts).

Shell 1:

```bash
yarn hardhat node --tags Arbitration
```

Shell 2:

```bash
yarn hardhat run scripts/populatePolicyRegistry.ts --network localhost
yarn hardhat run scripts/populateCourts.ts --network localhost
```

#### 3/ Import the data to V2 - Public Testnet

```bash
yarn hardhat run scripts/populatePolicyRegistry.ts --network arbitrumGoerli
yarn hardhat run scripts/populateCourts.ts --network arbitrumGoerli
```

### Generate deployment artifacts for existing contracts

#### Usage

```bash
scripts/generateDeploymentArtifact.sh <network> <address>
```

#### Example: WETH on Gnosis chain

```bash
scripts/generateDeploymentArtifact.sh gnosischain 0xf8d1677c8a0c961938bf2f9adc3f3cfda759a9d9 > deployments/gnosischain/WETH.json
```

### Push the contracts to a Tenderly project

Ensure that your `$TENDERLY_PROJECT` and `$TENDERLY_USERNAME` is set correctly in `.env`.

```bash
yarn tenderly-verify --network goerli
yarn tenderly-verify --network arbitrumGoerli
```
