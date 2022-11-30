# Introduction

Beanstalk is a permissionless fiat stablecoin protocol built on Ethereum.

Beanstalk forms the monetary basis of an Ethereum-native, rent-free economy facilitated by the seigniorage of its native fiat currency, a stablecoin called Bean.

Beanstalk's primary objective is to incentivize independent market participants to regularly cross the price of 1 Bean across its value peg of $1 in a sustainable fashion. The stability of the Bean price relative to its value peg is a function of the creditworthiness of Beanstalk—Beanstalk attracts lenders when the price of a Bean is below its value peg to remove Beans from the supply and increase their price.

When the Bean price is too high, Beanstalk mints new Beans and distributes them to various ecosystem participants in a deterministic fashion. This inflation is [the positive carry](https://docs.bean.money/almanac/introduction/why-beanstalk#carrying-costs) that the Beanstalk economy is based on.

Beanstalk implements several novel mechanisms including a first-in-first-out (FIFO) [debt model](https://docs.bean.money/almanac/farm/field#pods) supplemented by [an on-chain order book](https://docs.bean.money/almanac/farm/market#the-pod-market), [a time-weighted staking structure](https://docs.bean.money/almanac/farm/silo#the-stalk-system) that increases the opportunity cost of withdrawing the longer an asset stays deposited in the DAO and [a convert mechanism](https://docs.bean.money/almanac/peg-maintenance/convert) that allows participants to perform peg maintenance while those assets are staked.

Beanstalk strives to create product market fit on both a technical and economic level. In order to service an entire ecosystem, Beanstalk needs to provide a cheap, composable and interoperable interface. However, as protocols become more sophisticated and blockspace more crowded, smart contract architecture complexity can quickly become overwhelming.

Beanstalk pioneers a path forward for devising more efficient and complex systems. Beanstalk is implemented in [Solidity v0.7.6](https://docs.soliditylang.org/) for intended use in the [EVM](https://ethereum.org/en/developers/docs/evm/). Beanstalk leverages [EIP-2535](https://eips.ethereum.org/EIPS/eip-2535) to minimize gas costs and complexity.

Beanstalk consists of 2 main contracts:

* Beanstalk - The protocol responsible for peg maintenance implemented as an [EIP-2535](https://eips.ethereum.org/EIPS/eip-2535) multi-facet proxy.
* Bean – The stablecoin implemented as an [ERC-20](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/) token.

### Contracts

Beanstalk is deployed at [`0xC1E088fC1323b20BCBee9bd1B9fC9546db5624C5`](https://etherscan.io/address/0xc1e088fc1323b20bcbee9bd1b9fc9546db5624c5).

Bean is deployed at [`0xBEA0000029AD1c77D3d5D23Ba2D8893dB9d1Efab`](https://etherscan.io/address/0xBEA0000029AD1c77D3d5D23Ba2D8893dB9d1Efab).

All relevant contract addresses can be found on the [Contracts](https://docs.bean.money/almanac/protocol/contracts) page of the [Farmers' Almanac](https://docs.bean.money/almanac).
