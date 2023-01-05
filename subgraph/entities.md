# Entities

{% hint style="warning" %}
All subgraph documentation is under active development. The subgraph schema can be found [here](https://github.com/BeanstalkFarms/Beanstalk-Subgraph/blob/master/schema.graphql).
{% endhint %}

## Snapshot Entity Note

Within the Beanstalk Subgraph, there are many key areas where point in time snapshots are updated and saved for ease of access in the future. These entities contain the current point in time values for their respective period, along with the delta values from the previous snapshot. Delta values are represented as distinct fields. There are both hourly and daily period snapshots for the following base entities:

* `Silo`
* `SiloAsset`
* `Field`
* `PodMarketplace`

These Snapshot entities are not currently included in the parameter tables below.

## Overview

* ``[`Beanstalk`](entities.md#beanstalk)``
* ``[`Season`](entities.md#season)``
* ``[`Silo`](entities.md#silo)``
  * `SiloHourlySnapshot`
  * `SiloDailySnapshot`
* ``[`SiloAsset`](entities.md#siloasset)``
  * `SiloAssetHourlySnapshot`
  * `SiloAssetDailySnapshot`
* ``[`SiloYield`](entities.md#siloyield)``
* ``[`Field`](entities.md#field)``
  * `FieldHourlySnapshot`
  * `FieldDailySnapshot`
* ``[`Farmer`](entities.md#farmer)``
* ``[`SiloDeposit`](entities.md#silodeposit)``
* ``[`SiloWithdraw`](entities.md#silowithdraw)``
* ``[`Plot`](entities.md#plot)``
* ``[`PodMarketplace`](entities.md#podmarketplace)``
  * `PodMarketplaceHourlySnapshot`
  * `PodMarketplaceDailySnapshot`
* ``[`PodListing`](entities.md#podlisting)``
* ``[`PodOrder`](entities.md#podorder)``
* ``[`PodFill`](entities.md#podfill)``
* ``[`Fertilizer`](entities.md#fertilizer)``
* ``[`FertilizerToken`](entities.md#fertilizertoken)``
* ``[`FertilizerBalance`](entities.md#fertilizerbalance)``
* &#x20; [`FertilizerYield`](entities.md#fertilizeryield)

## Beanstalk

Metadata about Beanstalk and the subgraph.

| Field                | Type         | Description                                                                                        |
| -------------------- | ------------ | -------------------------------------------------------------------------------------------------- |
| `id`                 | `ID!`        | Smart contract address of the protocol's main contract (Factory, Registry, etc)                    |
| `name`               | `String!`    | Name of the protocol, including version. (_e.g._ Uniswap v3)                                       |
| `slug`               | `String!`    | Slug of protocol, including version. (_e.g._ uniswap-v3)                                           |
| `schemaVersion`      | `String!`    | Version of the subgraph schema, in SemVer format (_e.g._ 1.0.0)                                    |
| `subgraphVersion`    | `String!`    | Version of the subgraph implementation, in SemVer format (_e.g._ 1.0.0)                            |
| `methodologyVersion` | `String!`    | Version of the methodology used to compute metrics, loosely based on SemVer format (_e.g._ 1.0.0)  |
| `lastUpgrade`        | `BigInt!`    | Timestamp of the latest diamondCut call                                                            |
| `seasons`            | `[Season!]!` | Season specific data                                                                               |
| `silo`               | `Silo!`      | Silo level data                                                                                    |
| `field`              | `Field!`     | Field level data                                                                                   |
| `lastSeason`         | `Int!`       | Last Season                                                                                        |
| `activeFarmers`      | `[String!]!` | Array of the addresses for all active Farmers in the Silo                                          |
| `farmersToUpdate`    | `[String!]!` | Array of the addresses for all Farmers that had Silo transfers and need Stalk/Seeds/Roots updated  |

## Season

Information about Season level data.

| Field              | Type          | Description                               |
| ------------------ | ------------- | ----------------------------------------- |
| `id`               | `ID!`         | Season number                             |
| `beanstalk`        | `Beanstalk!`  | Beanstalk contract address                |
| `season`           | `Int!`        | Season number in `Int` form for sorting   |
| `createdAt`        | `BigInt!`     | Block timestamp when `sunrise` was called |
| `price`            | `BigDecimal!` | Bean price during last `sunrise`          |
| `beans`            | `BigInt!`     | Total Bean supply                         |
| `marketCap`        | `BigDecimal!` | Bean market cap                           |
| `deltaB`           | `BigInt!`     | Time weighted deltaB                      |
| `deltaBeans`       | `BigInt!`     | Change in Bean supply                     |
| `rewardBeans`      | `BigInt!`     | Amount of Beans minted during `sunrise`   |
| `incentiveBeans`   | `BigInt!`     | Amount of Beans paid to `sunrise` caller  |
| `harvestableIndex` | `BigInt!`     | New Harvestable index for the Season      |

## Silo

Silo level data for either Beanstalk or individual Farmers is stored here. Use the Beanstalk contract address to view protocol level values.

| Field               | Type                     | Description                                                   |
| ------------------- | ------------------------ | ------------------------------------------------------------- |
| `id`                | `ID!`                    | Address for the Farmer or Beanstalk                           |
| `beanstalk`         | `Beanstalk!`             | Beanstalk contract address                                    |
| `farmer`            | `Farmer`                 | Farmer address if applicable                                  |
| `whitelistedTokens` | `[String!]!`             | Tokens on the Deposit Whitelist                               |
| `assets`            | `[SiloAsset!]!`          | Derived field linking to `SiloAsset`                          |
| `depositedBDV`      | `BigInt!`                | Current BDV of Deposited assets in the Silo                   |
| `stalk`             | `BigInt!`                | Current Stalk in the Silo                                     |
| `plantableStalk`    | `BigInt!`                | Current Stalk not yet claimed via Plant                       |
| `seeds`             | `BigInt!`                | Current total Seeds                                           |
| `roots`             | `BigInt!`                | Current total Roots                                           |
| `beanMints`         | `BigInt!`                | Cumulative total of all Bean mints sent to the Silo           |
| `activeFarmers`     | `Int!`                   | Current number of active Farmer addresses with non-zero Stalk |
| `hourlySnapshots`   | `[SiloHourlySnapshot!]!` | Derived field linking to `SiloHourlySnapshot`                 |
| `dailySnapshots`    | `[SiloDailySnapshot!]!`  | Derived field linking to `SiloDailySnapshot`                  |

## SiloAsset

This entity holds asset specific totals and data for tokens found within the Silo.

| Field             | Type                          | Description                                        |
| ----------------- | ----------------------------- | -------------------------------------------------- |
| `id`              | `ID!`                         | Silo ID - Asset token address                      |
| `silo`            | `Silo!`                       | Silo ID for which this asset belongs               |
| `token`           | `String!`                     | Token address of the asset                         |
| `depositedBDV`    | `BigInt!`                     | Current BDV of Deposits                            |
| `depositedAmount` | `BigInt!`                     | Current token amount of Deposits                   |
| `withdrawnAmount` | `BigInt!`                     | Current token amount of Withdrawals                |
| `farmAmount`      | `BigInt!`                     | Current token amount held as an Internal Balance   |
| `hourlySnapshots` | `[SiloAssetHourlySnapshot!]!` | Derived field linking to `SiloAssetHourlySnapshot` |
| `dailySnapshots`  | `[SiloAssetDailySnapshot!]!`  | Derived field linking to `SiloAssetDailySnapshot`  |

## SiloYield

Data on what was used and the resulting vAPYs found within the Silo are stored here.

| Field               | Type          | Description                      |
| ------------------- | ------------- | -------------------------------- |
| `id`                | `ID!`         | The Season of the yield          |
| `season`            | `Int!`        | Season when calculated           |
| `beta`              | `BigDecimal!` | Beta used for EMA                |
| `u`                 | `Int!`        | _u_ value used for EMA           |
| `beansPerSeasonEMA` | `BigDecimal!` | Bean EMA for the season          |
| `twoSeedBeanAPY`    | `BigDecimal!` | Bean APY for two Seeds per BDV   |
| `twoSeedStalkAPY`   | `BigDecimal!` | Stalk APY for two Seeds per BDV  |
| `fourSeedBeanAPY`   | `BigDecimal!` | Bean APY for four Seeds per BDV  |
| `fourSeedStalkAPY`  | `BigDecimal!` | Stalk APY for four Seeds per BDV |
| `createdAt`         | `BigInt!`     | Block timestamp of creation      |

## Field

Field level data. Each Farmer and Beanstalk as a whole has their own Field.

| Field               | Type                      | Description                                                                                   |
| ------------------- | ------------------------- | --------------------------------------------------------------------------------------------- |
| `id`                | `ID!`                     | Address for the Farmer or Beanstalk                                                           |
| `beanstalk`         | `Beanstalk!`              | Beanstalk contract address                                                                    |
| `farmer`            | `Farmer`                  | Farmer address if applicable                                                                  |
| `season`            | `Int!`                    | Latest Season updated                                                                         |
| `temperature`       | `Int!`                    | Current Temperature offered for Sowing                                                        |
| `realRateOfReturn`  | `BigDecimal!`             | Temperature / Bean Price                                                                      |
| `numberOfSowers`    | `Int!`                    | Cumulative number of Sowers                                                                   |
| `numberOfSows`      | `Int!`                    | Cumulative number of Sows                                                                     |
| `sownBeans`         | `BigInt!`                 | Cumulative number of Sown Beans                                                               |
| `plotIndexes`       | `[BigInt!]!`              | Array of Unharvestable Plot indexes. Used when updating Harvestable amounts during `sunrise`. |
| `unharvestablePods` | `BigInt!`                 | Current number of Unharvestable Pods                                                          |
| `harvestablePods`   | `BigInt!`                 | Current number of Harvestable Pods                                                            |
| `harvestedPods`     | `BigInt!`                 | Current number of Harvested Pods                                                              |
| `soil`              | `BigInt!`                 | Current amount of available Soil                                                              |
| `podIndex`          | `BigInt!`                 | Current Pod index for new Plots                                                               |
| `podRate`           | `BigDecimal!`             | Current Pod Rate: Unharvestable Pods / Bean supply                                            |
| `hourlySnapshots`   | `[FieldHourlySnapshot!]!` | Derived field linking to `FieldHourlySnapshot`                                                |
| `dailySnapshots`    | `[FieldDailySnapshot!]!`  | Derived field linking to `FieldDailySnapshot`                                                 |

## Farmer

The Farmer entity is unique in the fact that it is comprised completely of derived fields. This is to aid in the exploration and querying of the information on a specific address.

| Field         | Type                    | Description                          |
| ------------- | ----------------------- | ------------------------------------ |
| `id`          | `ID!`                   | Farmer's address                     |
| `silo`        | `Silo`                  | Derived field to `Silo`              |
| `deposits`    | `[SiloDeposit!]!`       | Derived field to `SiloDeposit`       |
| `withdraws`   | `[SiloWithdraw!]!`      | Derived field to `SiloWithdraw`      |
| `field`       | `Field`                 | Derived field to `Field`             |
| `plots`       | `[Plot!]!`              | Derived field to `Plot`              |
| `listings`    | `[PodListing!]!`        | Derived field to `PodListing`        |
| `orders`      | `[PodOrder!]!`          | Derived field to `PodOrder`          |
| `fills`       | `[PodFill!]!`           | Derived field to `PodFill`           |
| `fertilizers` | `[FertilizerBalance!]!` | Derived field to `FertilizerBalance` |

## SiloDeposit

Individual Silo Deposit data. Updated upon Withdrawals for the net Deposited amounts and BDV.

| Field             | Type         | Description                                     |
| ----------------- | ------------ | ----------------------------------------------- |
| `id`              | `ID!`        | Account - Token Address - Season                |
| `farmer`          | `Farmer!`    | Farmer address                                  |
| `token`           | `String!`    | Token contract address                          |
| `season`          | `Int!`       | Season of Deposit                               |
| `amount`          | `BigInt!`    | Current token amount Deposited                  |
| `depositedAmount` | `BigInt!`    | Originally Deposited token amount               |
| `withdrawnAmount` | `BigInt!`    | Withdrawn token amount                          |
| `bdv`             | `BigInt!`    | Current BDV of Deposit                          |
| `depositedBDV`    | `BigInt!`    | Original BDV of a Deposit                       |
| `withdrawnBDV`    | `BigInt!`    | Withdrawn BDV of Deposit                        |
| `hashes`          | `[String!]!` | Transaction hashes included in original Deposit |
| `createdAt`       | `BigInt!`    | Block timestamp of first Deposit                |
| `updatedAt`       | `BigInt!`    | Block timestamp of last update                  |

## SiloWithdraw

Withdrawal level data. Updated to flag whether a Withdrawal has been claimed.

| Field             | Type         | Description                                             |
| ----------------- | ------------ | ------------------------------------------------------- |
| `id`              | `ID!`        | Account - Deposit Token - Current Season                |
| `farmer`          | `Farmer!`    | Farmer address                                          |
| `token`           | `String!`    | Token contract address                                  |
| `withdrawSeason`  | `Int!`       | Season withdraw initiated                               |
| `claimableSeason` | `Int!`       | Season when claimable                                   |
| `claimed`         | `Boolean!`   | Flag for if withdrawal has been claimed                 |
| `amount`          | `BigInt!`    | Token amount being withdrawn                            |
| `hashes`          | `[String!]!` | Transaction hashes included in this season's withdrawal |
| `createdAt`       | `BigInt!`    | Block timestamp of first withdrawal                     |

## Plot

All details related to a specific Plot.

| Field             | Type          | Description                                                                                               |
| ----------------- | ------------- | --------------------------------------------------------------------------------------------------------- |
| `id`              | `ID!`         | Plot index                                                                                                |
| `field`           | `Field!`      | Field to which this Plot belongs                                                                          |
| `farmer`          | `Farmer!`     | Farmer that owns this Plot                                                                                |
| `source`          | `PlotSource!` | <p>Enum for the source of this Plot:<br><code>SOW</code>, <code>HARVEST</code>, <code>TRANSFER</code></p> |
| `listing`         | `PodListing`  | Any associated listing of this Plot                                                                       |
| `season`          | `Int!`        | Season of creation                                                                                        |
| `creationHash`    | `String!`     | Transaction hash of creation                                                                              |
| `createdAt`       | `BigInt!`     | Block timestamp of creation                                                                               |
| `updatedAt`       | `BigInt!`     | Block timestamp when updated                                                                              |
| `index`           | `BigInt!`     | Plot index                                                                                                |
| `beans`           | `BigInt!`     | Beans used to Sow, if any                                                                                 |
| `pods`            | `BigInt!`     | Total Pods in the Plot                                                                                    |
| `sownPods`        | `BigInt!`     | Total Pods Sown, if any                                                                                   |
| `temperature`     | `Int!`        | Temperature when Plot was sown                                                                            |
| `harvestablePods` | `BigInt!`     | Number of Pods that are Harvestable                                                                       |
| `harvestedPods`   | `BigInt!`     | Number of Pods that have been Harvested                                                                   |
| `fullyHarvested`  | `Boolean`     | Flag for if a Plot has been fully Harvested                                                               |

## PodMarketplace

Aggregated data surrounding the Pod Market.

| Field                  | Type                               | Description                                             |
| ---------------------- | ---------------------------------- | ------------------------------------------------------- |
| `id`                   | `ID!`                              | Contract address of Beanstalk                           |
| `season`               | `Int!`                             | Current Season of the Pod Market                        |
| `listingIndexes`       | `[BigInt!]!`                       | Indexes of Listed {lots                                 |
| `orders`               | `[PodOrder!]!`                     | Active Pod Order IDs                                    |
| `allListings`          | `[PodListing!]!`                   | Derived field for all historical  `PodListing` entities |
| `allOrders`            | `[PodOrder!]!`                     | Derived field for all historical  `PodOrder` entities   |
| `listedPods`           | `BigInt!`                          | Current cumulative Pods Listed for sale                 |
| `filledListedPods`     | `BigInt!`                          | Current cumulative Pod Listings Filled                  |
| `expiredListedPods`    | `BigInt!`                          | Current cumulative Pod Listings that expired            |
| `cancelledListedPods`  | `BigInt!`                          | Current cumulative Pod Listings that are Cancelled      |
| `availableListedPods`  | `BigInt!`                          | Current total of Pods available for purchase            |
| `orderedPods`          | `BigInt!`                          | Current cumulative Pod Orders created                   |
| `filledOrderedPods`    | `BigInt!`                          | Current cumulative Pod Orders that were Filled          |
| `cancelledOrderedPods` | `BigInt!`                          | Current cumulative Pod Orders that were Cancelled       |
| `podVolume`            | `BigInt!`                          | Current cumulative Pod volume                           |
| `beanVolume`           | `BigInt!`                          | Current cumulative Bean volume                          |
| `hourlySnapshots`      | `[PodMarketplaceHourlySnapshot!]!` | Derived field to `PodMarketplaceHourlySnapshot`         |
| `dailySnapshots`       | `[PodMarketplaceDailySnapshot!]!`  | Derived field to `PodMarketplaceDailySnapshot`          |

## PodListing

Details regarding a specific Pod Listing.

| Field                 | Type              | Description                                                                                                                                                                          |
| --------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `id`                  | `ID!`             | Account - Plot Index                                                                                                                                                                 |
| `podMarketplace`      | `PodMarketplace!` | Pod Market where this Listing was made                                                                                                                                               |
| `historyID`           | `String!`         | Unique string to pull and display all historical activity                                                                                                                            |
| `plot`                | `Plot!`           | Plot being Listed                                                                                                                                                                    |
| `farmer`              | `Farmer!`         | Farmer Listing this Plot                                                                                                                                                             |
| `createdAt`           | `BigInt!`         | Block timestamp at creation                                                                                                                                                          |
| `updatedAt`           | `BigInt!`         | Block timestamp of last update                                                                                                                                                       |
| `status`              | `MarketStatus!`   | <p>Enum for valid status:<br><code>ACTIVE</code>, <code>FILLED</code>, <code>FILLED_PARTIAL</code>, <code>CANCELLED</code>, <code>CANCELLED_PARTIAL</code>, <code>EXPIRED</code></p> |
| `fill`                | `PodFill`         | Any associated Fill                                                                                                                                                                  |
| `originalIndex`       | `BigInt!`         | Original index of the Plot Listed                                                                                                                                                    |
| `index`               | `BigInt!`         | Current index of Plot Listed                                                                                                                                                         |
| `start`               | `BigInt!`         | Start within Plot for Listing                                                                                                                                                        |
| `amount`              | `BigInt!`         | Amount of Pods Listed                                                                                                                                                                |
| `originalAmount`      | `BigInt!`         | Total amount of original Listing                                                                                                                                                     |
| `remainingAmount`     | `BigInt!`         | Remaining amount left to be Filled                                                                                                                                                   |
| `filledAmount`        | `BigInt!`         | Amount Filled on this Listing                                                                                                                                                        |
| `filled`              | `BigInt!`         | Total amount Filled from original Listing                                                                                                                                            |
| `cancelledAmount`     | `BigInt!`         | Amount Cancelled                                                                                                                                                                     |
| `pricePerPod`         | `Int!`            | Market v1 price per Pod                                                                                                                                                              |
| `minFillAmount`       | `BigInt!`         | Minimum amount needed to Fill this Listing                                                                                                                                           |
| `maxHarvestableIndex` | `BigInt!`         | Max Harvestable index before Listing expires                                                                                                                                         |
| `pricingFunction`     | `Bytes`           | Market v2 pricing function                                                                                                                                                           |
| `mode`                | `Int!`            | Sale Bean mode (Internal/External)                                                                                                                                                   |
| `pricingType`         | `Int`             | Market v2 pricing type                                                                                                                                                               |
| `creationHash`        | `String!`         | Transaction hash at time of initial entity creation.                                                                                                                                 |

## PodOrder

Details regarding a specific Pod Order.

| Field              | Type              | Descriptoin                                                                                                                                                                          |
| ------------------ | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `id`               | `ID!`             | Order ID emitted by event                                                                                                                                                            |
| `podMarketplace`   | `PodMarketplace!` | Marketplace used for Order                                                                                                                                                           |
| `historyID`        | `String!`         | Unique string to pull and display all historical activity                                                                                                                            |
| `farmer`           | `Farmer!`         | Farmer placing the Order                                                                                                                                                             |
| `createdAt`        | `BigInt!`         | Block timestamp at creation                                                                                                                                                          |
| `updatedAt`        | `BigInt!`         | Block timestamp at last update                                                                                                                                                       |
| `status`           | `MarketStatus!`   | <p>Enum for valid status:<br><code>ACTIVE</code>, <code>FILLED</code>, <code>FILLED_PARTIAL</code>, <code>CANCELLED</code>, <code>CANCELLED_PARTIAL</code>, <code>EXPIRED</code></p> |
| `fills`            | \[`PodFill!]!`    | Any associated `PodFill` IDs                                                                                                                                                         |
| `podAmount`        | `BigInt!`         | V1 - Original amount of the Ordered Pods                                                                                                                                             |
| `beanAmount`       | `BigInt!`         | V2 - Original amount of Beans used to Order Pods                                                                                                                                     |
| `podAmountFilled`  | `BigInt!`         | Current Filled amount                                                                                                                                                                |
| `beanAmountFilled` | `BigInt!`         | Bean amount Filled                                                                                                                                                                   |
| `minFillAmount`    | `BigInt!`         | Minimum amount needed to Fill this Order                                                                                                                                             |
| `maxPlaceInLine`   | `BigInt!`         | Max Place in Line for Pods to Fill the Order                                                                                                                                         |
| `pricePerPod`      | `Int!`            | Market v1 price per Pod                                                                                                                                                              |
| `pricingFunction`  | `Bytes`           | Market v2 pricing function                                                                                                                                                           |
| `pricingType`      | `Int`             | Market v2 pricing type                                                                                                                                                               |
| `creationHash`     | `String!`         | Transaction hash at time of initial entity creation.                                                                                                                                 |

## PodFill

Fill data for both Listings and Orders.

| Field            | Type              | Description                                                |
| ---------------- | ----------------- | ---------------------------------------------------------- |
| `id`             | `ID!`             | Beanstalk address - Order/Listing index - transaction hash |
| `podMarketplace` | `PodMarketplace!` | Marketplace associated with this Fill                      |
| `createdAt`      | `BigInt!`         | Block timestamp at creation                                |
| `listing`        | `PodListing`      | Associated Listing, if any                                 |
| `order`          | `PodOrder`        | Associated Order, if any                                   |
| `from`           | `String!`         | Account Filling the Listing/Order                          |
| `to`             | `Farmer!`         | Account Filling the Listing/Order                          |
| `amount`         | `BigInt!`         | Number of Pods Filled                                      |
| `index`          | `BigInt!`         | Index of Plot transferred                                  |
| `start`          | `BigInt!`         | Start of Plot transferred                                  |
| `costInBeans`    | `BigInt`          | Total Beans used to Fill Listing/Order                     |

## Fertilizer

Global Fertilizer data.

| Field    | Type                  | Description                                |
| -------- | --------------------- | ------------------------------------------ |
| `id`     | `ID!`                 | Contract address for Fertilizer            |
| `supply` | `BigInt!`             | Total overall supply for Fertilizer tokens |
| `tokens` | `[FertilizerToken!]!` | Derived field to `FertilizerToken`         |

## FertilizerToken

ID level information for Fertilizer tokens. BPF = Beans Per Fertilizer.

| Field        | Type                    | Description                          |
| ------------ | ----------------------- | ------------------------------------ |
| `id`         | `ID!`                   | Total BPF for purchase               |
| `fertilizer` | `Fertilizer!`           | Fertilizer contract address          |
| `supply`     | `BigInt!`               | Total supply for this humidity       |
| `humidity`   | `BigDecimal!`           | Humidity paid for this ID            |
| `endBpf`     | `BigInt!`               | Ending BPF on creation               |
| `startBpf`   | `BigInt!`               | Starting BPF on creation             |
| `season`     | `Int!`                  | Season created                       |
| `balances`   | `[FertilizerBalance!]!` | Derived field to `FertilizerBalance` |

## FertilizerBalance

Balance details by Farmer and Fertilizer token.

| Field             | Type               | Description                       |
| ----------------- | ------------------ | --------------------------------- |
| `id`              | `ID!`              | Fertilizer Token - Farmer address |
| `fertilizerToken` | `FertilizerToken!` | ID of Fertilizer token            |
| `farmer`          | `Farmer!`          | Farmer that owns the Fertilizer   |
| `amount`          | `BigInt!`          | Current balance of the token      |

## FertilizerYield

| Field               | Type          | Description                                                                                                 |
| ------------------- | ------------- | ----------------------------------------------------------------------------------------------------------- |
| `id`                | `ID!`         | Season being calculated                                                                                     |
| `season`            | `Int!`        | Current season                                                                                              |
| `humidity`          | `BigDecimal!` | Current humidity for new fertilizer                                                                         |
| `outstandingFert`   | `BigInt!`     | Current total fertilizer still outstanding                                                                  |
| `beansPerSeasonEMA` | `BigDecimal!` | Current Bean EMA                                                                                            |
| `deltaBpf`          | `BigDecimal!` | Current new beans per outstanding fertilizer                                                                |
| `simpleAPY`         | `BigDecimal!` | Simplified APY adjusted for the length of time needed to return total principal and yield based on humidity |
| `createdAt`         | `BigInt!`     | Block timestamp at creation                                                                                 |
