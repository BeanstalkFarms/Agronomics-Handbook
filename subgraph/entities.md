# Entities

{% hint style="warning" %}
All subgraph documentation is in development and not necessarily up to date. The Beanstalk Subgraph schema can be found [here](https://github.com/BeanstalkFarms/Beanstalk/blob/master/projects/subgraph-beanstalk/schema.graphql). The Bean Subgraph schema can be found [here](https://github.com/BeanstalkFarms/Beanstalk/blob/master/projects/subgraph-bean/schema.graphql).
{% endhint %}

## Snapshot Entity Note

Within the Beanstalk Subgraph, there are many key areas where point in time snapshots are updated and saved for ease of access in the future. These entities contain the current point in time values for their respective period, along with the delta values from the previous snapshot. Delta values are represented as distinct fields. There are both hourly and daily period snapshots for the following base entities:

* `Silo`
* `SiloAsset`
* `Field`
* `PodMarketplace`

These Snapshot entities are not currently included in the parameter tables below.

## Overview

* [`Beanstalk`](entities.md#beanstalk)
* [`Season`](entities.md#season)
* [`Silo`](entities.md#silo)
  * `SiloHourlySnapshot`
  * `SiloDailySnapshot`
* [`SiloAsset`](entities.md#siloasset)
  * `SiloAssetHourlySnapshot`
  * `SiloAssetDailySnapshot`
* [`SiloYield`](entities.md#siloyield)
* [`Field`](entities.md#field)
  * `FieldHourlySnapshot`
  * `FieldDailySnapshot`
* [`Farmer`](entities.md#farmer)
* [`SiloDeposit`](entities.md#silodeposit)
* [`SiloWithdraw`](entities.md#silowithdraw)
* [`Plot`](entities.md#plot)
* [`PodMarketplace`](entities.md#podmarketplace)
  * `PodMarketplaceHourlySnapshot`
  * `PodMarketplaceDailySnapshot`
* [`PodListing`](entities.md#podlisting)
* [`PodOrder`](entities.md#podorder)
* [`PodFill`](entities.md#podfill)
* [`Fertilizer`](entities.md#fertilizer)
* [`FertilizerToken`](entities.md#fertilizertoken)
* [`FertilizerBalance`](entities.md#fertilizerbalance)
* &#x20; [`FertilizerYield`](entities.md#fertilizeryield)

## Beanstalk

Metadata about Beanstalk and the subgraph.

<table><thead><tr><th width="231">Field</th><th width="148.33333333333331">Type</th><th width="386.66666666666674">Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>ID!</code></td><td>Smart contract address of the protocol's main contract (Factory, Registry, etc)</td></tr><tr><td><code>name</code></td><td><code>String!</code></td><td>Name of the protocol, including version. (<em>e.g.</em> Uniswap v3)</td></tr><tr><td><code>slug</code></td><td><code>String!</code></td><td>Slug of protocol, including version. (<em>e.g.</em> uniswap-v3)</td></tr><tr><td><code>schemaVersion</code></td><td><code>String!</code></td><td>Version of the subgraph schema, in SemVer format (<em>e.g.</em> 1.0.0)</td></tr><tr><td><code>subgraphVersion</code></td><td><code>String!</code></td><td>Version of the subgraph implementation, in SemVer format (<em>e.g.</em> 1.0.0)</td></tr><tr><td><code>methodologyVersion</code></td><td><code>String!</code></td><td>Version of the methodology used to compute metrics, loosely based on SemVer format (<em>e.g.</em> 1.0.0) </td></tr><tr><td><code>lastUpgrade</code></td><td><code>BigInt!</code></td><td>Timestamp of the latest diamondCut call</td></tr><tr><td><code>seasons</code></td><td><code>[Season!]!</code></td><td>Season specific data</td></tr><tr><td><code>silo</code></td><td><code>Silo!</code></td><td>Silo level data</td></tr><tr><td><code>field</code></td><td><code>Field!</code></td><td>Field level data</td></tr><tr><td><code>lastSeason</code></td><td><code>Int!</code></td><td>Last Season</td></tr><tr><td><code>activeFarmers</code></td><td><code>[String!]!</code></td><td>Array of the addresses for all active Farmers in the Silo</td></tr><tr><td><code>farmersToUpdate</code></td><td><code>[String!]!</code></td><td>Array of the addresses for all Farmers that had Silo transfers and need Stalk/Seeds/Roots updated</td></tr></tbody></table>

## Season

Information about Season level data.

<table><thead><tr><th width="213">Field</th><th width="157.33333333333331">Type</th><th width="386.66666666666674">Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>ID!</code></td><td>Season number</td></tr><tr><td><code>beanstalk</code></td><td><code>Beanstalk!</code></td><td>Beanstalk contract address</td></tr><tr><td><code>season</code></td><td><code>Int!</code></td><td>Season number in <code>Int</code> form for sorting</td></tr><tr><td><code>createdAt</code></td><td><code>BigInt!</code></td><td>Block timestamp when <code>sunrise</code> was called</td></tr><tr><td><code>price</code></td><td><code>BigDecimal!</code></td><td>Bean price during last <code>sunrise</code></td></tr><tr><td><code>beans</code></td><td><code>BigInt!</code></td><td>Total Bean supply</td></tr><tr><td><code>marketCap</code></td><td><code>BigDecimal!</code></td><td>Bean market cap</td></tr><tr><td><code>deltaB</code></td><td><code>BigInt!</code></td><td>Time weighted deltaB</td></tr><tr><td><code>deltaBeans</code></td><td><code>BigInt!</code></td><td>Change in Bean supply</td></tr><tr><td><code>rewardBeans</code></td><td><code>BigInt!</code></td><td>Amount of Beans minted during <code>sunrise</code></td></tr><tr><td><code>incentiveBeans</code></td><td><code>BigInt!</code></td><td>Amount of Beans paid to <code>sunrise</code> caller</td></tr><tr><td><code>harvestableIndex</code></td><td><code>BigInt!</code></td><td>New Harvestable index for the Season</td></tr></tbody></table>

## Silo

Silo level data for either Beanstalk or individual Farmers is stored here. Use the Beanstalk contract address to view protocol level values.

<table><thead><tr><th width="225.33333333333331">Field</th><th width="259">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>ID!</code></td><td>Address for the Farmer or Beanstalk</td></tr><tr><td><code>beanstalk</code></td><td><code>Beanstalk!</code></td><td>Beanstalk contract address</td></tr><tr><td><code>farmer</code></td><td><code>Farmer</code></td><td>Farmer address if applicable</td></tr><tr><td><code>whitelistedTokens</code></td><td><code>[String!]!</code></td><td>Tokens on the Deposit Whitelist</td></tr><tr><td><code>assets</code></td><td><code>[SiloAsset!]!</code></td><td>Derived field linking to <code>SiloAsset</code></td></tr><tr><td><code>depositedBDV</code></td><td><code>BigInt!</code></td><td>Current BDV of Deposited assets in the Silo</td></tr><tr><td><code>stalk</code></td><td><code>BigInt!</code></td><td>Current Stalk in the Silo</td></tr><tr><td><code>plantableStalk</code></td><td><code>BigInt!</code></td><td>Current Stalk not yet claimed via Plant</td></tr><tr><td><code>seeds</code></td><td><code>BigInt!</code></td><td>Current total Seeds</td></tr><tr><td><code>roots</code></td><td><code>BigInt!</code></td><td>Current total Roots</td></tr><tr><td><code>beanMints</code></td><td><code>BigInt!</code></td><td>Cumulative total of all Bean mints sent to the Silo</td></tr><tr><td><code>activeFarmers</code></td><td><code>Int!</code></td><td>Current number of active Farmer addresses with non-zero Stalk</td></tr><tr><td><code>hourlySnapshots</code></td><td><code>[SiloHourlySnapshot!]!</code></td><td>Derived field linking to <code>SiloHourlySnapshot</code></td></tr><tr><td><code>dailySnapshots</code></td><td><code>[SiloDailySnapshot!]!</code></td><td>Derived field linking to <code>SiloDailySnapshot</code></td></tr></tbody></table>

## SiloAsset

This entity holds asset specific totals and data for tokens found within the Silo.

<table><thead><tr><th width="203.33333333333331">Field</th><th width="301">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>ID!</code></td><td>Silo ID - Asset token address</td></tr><tr><td><code>silo</code></td><td><code>Silo!</code></td><td>Silo ID for which this asset belongs</td></tr><tr><td><code>token</code></td><td><code>String!</code></td><td>Token address of the asset</td></tr><tr><td><code>depositedBDV</code></td><td><code>BigInt!</code></td><td>Current BDV of Deposits</td></tr><tr><td><code>depositedAmount</code></td><td><code>BigInt!</code></td><td>Current token amount of Deposits</td></tr><tr><td><code>withdrawnAmount</code></td><td><code>BigInt!</code></td><td>Current token amount of Withdrawals</td></tr><tr><td><code>farmAmount</code></td><td><code>BigInt!</code></td><td>Current token amount held as an Internal Balance</td></tr><tr><td><code>hourlySnapshots</code></td><td><code>[SiloAssetHourlySnapshot!]!</code></td><td>Derived field linking to <code>SiloAssetHourlySnapshot</code></td></tr><tr><td><code>dailySnapshots</code></td><td><code>[SiloAssetDailySnapshot!]!</code></td><td>Derived field linking to <code>SiloAssetDailySnapshot</code></td></tr></tbody></table>

## SiloYield

Data on what was used and the resulting vAPYs found within the Silo are stored here.

<table><thead><tr><th width="237">Field</th><th width="189.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>ID!</code></td><td>The Season of the yield</td></tr><tr><td><code>season</code></td><td><code>Int!</code></td><td>Season when calculated</td></tr><tr><td><code>beta</code></td><td><code>BigDecimal!</code></td><td>Beta used for EMA</td></tr><tr><td><code>u</code></td><td><code>Int!</code></td><td><em>u</em> value used for EMA</td></tr><tr><td><code>beansPerSeasonEMA</code></td><td><code>BigDecimal!</code></td><td>Bean EMA for the season</td></tr><tr><td><code>twoSeedBeanAPY</code></td><td><code>BigDecimal!</code></td><td>Bean APY for two Seeds per BDV</td></tr><tr><td><code>twoSeedStalkAPY</code></td><td><code>BigDecimal!</code></td><td>Stalk APY for two Seeds per BDV</td></tr><tr><td><code>fourSeedBeanAPY</code></td><td><code>BigDecimal!</code></td><td>Bean APY for four Seeds per BDV</td></tr><tr><td><code>fourSeedStalkAPY</code></td><td><code>BigDecimal!</code></td><td>Stalk APY for four Seeds per BDV</td></tr><tr><td><code>createdAt</code></td><td><code>BigInt!</code></td><td>Block timestamp of creation</td></tr></tbody></table>

## Field

Field level data. Each Farmer and Beanstalk as a whole has their own Field.

<table><thead><tr><th width="223.33333333333331">Field</th><th width="272">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>ID!</code></td><td>Address for the Farmer or Beanstalk</td></tr><tr><td><code>beanstalk</code></td><td><code>Beanstalk!</code></td><td>Beanstalk contract address</td></tr><tr><td><code>farmer</code></td><td><code>Farmer</code></td><td>Farmer address if applicable</td></tr><tr><td><code>season</code></td><td><code>Int!</code></td><td>Latest Season updated</td></tr><tr><td><code>temperature</code></td><td><code>Int!</code></td><td>Current Temperature offered for Sowing</td></tr><tr><td><code>realRateOfReturn</code></td><td><code>BigDecimal!</code></td><td>Temperature / Bean Price</td></tr><tr><td><code>numberOfSowers</code></td><td><code>Int!</code></td><td>Cumulative number of Sowers</td></tr><tr><td><code>numberOfSows</code></td><td><code>Int!</code></td><td>Cumulative number of Sows</td></tr><tr><td><code>sownBeans</code></td><td><code>BigInt!</code></td><td>Cumulative number of Sown Beans</td></tr><tr><td><code>plotIndexes</code></td><td><code>[BigInt!]!</code></td><td>Array of Unharvestable Plot indexes. Used when updating Harvestable amounts during <code>sunrise</code>.</td></tr><tr><td><code>unharvestablePods</code></td><td><code>BigInt!</code></td><td>Current number of Unharvestable Pods</td></tr><tr><td><code>harvestablePods</code></td><td><code>BigInt!</code></td><td>Current number of Harvestable Pods</td></tr><tr><td><code>harvestedPods</code></td><td><code>BigInt!</code></td><td>Current number of Harvested Pods</td></tr><tr><td><code>soil</code></td><td><code>BigInt!</code></td><td>Current amount of available Soil</td></tr><tr><td><code>podIndex</code></td><td><code>BigInt!</code></td><td>Current Pod index for new Plots</td></tr><tr><td><code>podRate</code></td><td><code>BigDecimal!</code></td><td>Current Pod Rate: Unharvestable Pods / Bean supply</td></tr><tr><td><code>hourlySnapshots</code></td><td><code>[FieldHourlySnapshot!]!</code></td><td>Derived field linking to <code>FieldHourlySnapshot</code></td></tr><tr><td><code>dailySnapshots</code></td><td><code>[FieldDailySnapshot!]!</code></td><td>Derived field linking to <code>FieldDailySnapshot</code></td></tr></tbody></table>

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

<table><thead><tr><th width="248">Field</th><th width="145.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>ID!</code></td><td>Account - Token Address - Season</td></tr><tr><td><code>farmer</code></td><td><code>Farmer!</code></td><td>Farmer address</td></tr><tr><td><code>token</code></td><td><code>String!</code></td><td>Token contract address</td></tr><tr><td><code>season</code></td><td><code>Int!</code></td><td>Season of Deposit</td></tr><tr><td><code>amount</code></td><td><code>BigInt!</code></td><td>Current token amount Deposited</td></tr><tr><td><code>depositedAmount</code></td><td><code>BigInt!</code></td><td>Originally Deposited token amount</td></tr><tr><td><code>withdrawnAmount</code></td><td><code>BigInt!</code></td><td>Withdrawn token amount</td></tr><tr><td><code>bdv</code></td><td><code>BigInt!</code></td><td>Current BDV of Deposit</td></tr><tr><td><code>depositedBDV</code></td><td><code>BigInt!</code></td><td>Original BDV of a Deposit</td></tr><tr><td><code>withdrawnBDV</code></td><td><code>BigInt!</code></td><td>Withdrawn BDV of Deposit</td></tr><tr><td><code>hashes</code></td><td><code>[String!]!</code></td><td>Transaction hashes included in original Deposit</td></tr><tr><td><code>createdAt</code></td><td><code>BigInt!</code></td><td>Block timestamp of first Deposit</td></tr><tr><td><code>updatedAt</code></td><td><code>BigInt!</code></td><td>Block timestamp of last update</td></tr></tbody></table>

## SiloWithdraw

Withdrawal level data. Updated to flag whether a Withdrawal has been claimed.

<table><thead><tr><th width="222">Field</th><th width="166.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>ID!</code></td><td>Account - Deposit Token - Current Season</td></tr><tr><td><code>farmer</code></td><td><code>Farmer!</code></td><td>Farmer address</td></tr><tr><td><code>token</code></td><td><code>String!</code></td><td>Token contract address</td></tr><tr><td><code>withdrawSeason</code></td><td><code>Int!</code></td><td>Season withdraw initiated</td></tr><tr><td><code>claimableSeason</code></td><td><code>Int!</code></td><td>Season when claimable</td></tr><tr><td><code>claimed</code></td><td><code>Boolean!</code></td><td>Flag for if withdrawal has been claimed</td></tr><tr><td><code>amount</code></td><td><code>BigInt!</code></td><td>Token amount being withdrawn</td></tr><tr><td><code>hashes</code></td><td><code>[String!]!</code></td><td>Transaction hashes included in this season's withdrawal</td></tr><tr><td><code>createdAt</code></td><td><code>BigInt!</code></td><td>Block timestamp of first withdrawal</td></tr></tbody></table>

## Plot

All details related to a specific Plot.

<table><thead><tr><th width="214.33333333333331">Field</th><th width="180">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>ID!</code></td><td>Plot index</td></tr><tr><td><code>field</code></td><td><code>Field!</code></td><td>Field to which this Plot belongs</td></tr><tr><td><code>farmer</code></td><td><code>Farmer!</code></td><td>Farmer that owns this Plot</td></tr><tr><td><code>source</code></td><td><code>PlotSource!</code></td><td>Enum for the source of this Plot:<br><code>SOW</code>, <code>HARVEST</code>, <code>TRANSFER</code></td></tr><tr><td><code>listing</code></td><td><code>PodListing</code></td><td>Any associated listing of this Plot</td></tr><tr><td><code>season</code></td><td><code>Int!</code></td><td>Season of creation</td></tr><tr><td><code>creationHash</code></td><td><code>String!</code></td><td>Transaction hash of creation</td></tr><tr><td><code>createdAt</code></td><td><code>BigInt!</code></td><td>Block timestamp of creation</td></tr><tr><td><code>updatedAt</code></td><td><code>BigInt!</code></td><td>Block timestamp when updated</td></tr><tr><td><code>index</code></td><td><code>BigInt!</code></td><td>Plot index</td></tr><tr><td><code>beans</code></td><td><code>BigInt!</code></td><td>Beans used to Sow, if any</td></tr><tr><td><code>pods</code></td><td><code>BigInt!</code></td><td>Total Pods in the Plot</td></tr><tr><td><code>sownPods</code></td><td><code>BigInt!</code></td><td>Total Pods Sown, if any</td></tr><tr><td><code>temperature</code></td><td><code>Int!</code></td><td>Temperature when Plot was sown</td></tr><tr><td><code>harvestablePods</code></td><td><code>BigInt!</code></td><td>Number of Pods that are Harvestable</td></tr><tr><td><code>harvestedPods</code></td><td><code>BigInt!</code></td><td>Number of Pods that have been Harvested</td></tr><tr><td><code>fullyHarvested</code></td><td><code>Boolean</code></td><td>Flag for if a Plot has been fully Harvested</td></tr></tbody></table>

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

<table><thead><tr><th width="239.33333333333331">Field</th><th width="195">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>ID!</code></td><td>Account - Plot Index</td></tr><tr><td><code>podMarketplace</code></td><td><code>PodMarketplace!</code></td><td>Pod Market where this Listing was made</td></tr><tr><td><code>historyID</code></td><td><code>String!</code></td><td>Unique string to pull and display all historical activity</td></tr><tr><td><code>plot</code></td><td><code>Plot!</code></td><td>Plot being Listed</td></tr><tr><td><code>farmer</code></td><td><code>Farmer!</code></td><td>Farmer Listing this Plot</td></tr><tr><td><code>createdAt</code></td><td><code>BigInt!</code></td><td>Block timestamp at creation</td></tr><tr><td><code>updatedAt</code></td><td><code>BigInt!</code></td><td>Block timestamp of last update</td></tr><tr><td><code>status</code></td><td><code>MarketStatus!</code></td><td>Enum for valid status:<br><code>ACTIVE</code>, <code>FILLED</code>, <code>FILLED_PARTIAL</code>, <code>CANCELLED</code>, <code>CANCELLED_PARTIAL</code>, <code>EXPIRED</code></td></tr><tr><td><code>fill</code></td><td><code>PodFill</code></td><td>Any associated Fill</td></tr><tr><td><code>originalIndex</code></td><td><code>BigInt!</code></td><td>Original index of the Plot Listed</td></tr><tr><td><code>index</code></td><td><code>BigInt!</code></td><td>Current index of Plot Listed</td></tr><tr><td><code>start</code></td><td><code>BigInt!</code></td><td>Start within Plot for Listing</td></tr><tr><td><code>amount</code></td><td><code>BigInt!</code></td><td>Amount of Pods Listed</td></tr><tr><td><code>originalAmount</code></td><td><code>BigInt!</code></td><td>Total amount of original Listing</td></tr><tr><td><code>remainingAmount</code></td><td><code>BigInt!</code></td><td>Remaining amount left to be Filled</td></tr><tr><td><code>filledAmount</code></td><td><code>BigInt!</code></td><td>Amount Filled on this Listing</td></tr><tr><td><code>filled</code></td><td><code>BigInt!</code></td><td>Total amount Filled from original Listing</td></tr><tr><td><code>cancelledAmount</code></td><td><code>BigInt!</code></td><td>Amount Cancelled</td></tr><tr><td><code>pricePerPod</code></td><td><code>Int!</code></td><td>Market v1 price per Pod</td></tr><tr><td><code>minFillAmount</code></td><td><code>BigInt!</code></td><td>Minimum amount needed to Fill this Listing</td></tr><tr><td><code>maxHarvestableIndex</code></td><td><code>BigInt!</code></td><td>Max Harvestable index before Listing expires</td></tr><tr><td><code>pricingFunction</code></td><td><code>Bytes</code></td><td>Market v2 pricing function</td></tr><tr><td><code>mode</code></td><td><code>Int!</code></td><td>Sale Bean mode (Internal/External)</td></tr><tr><td><code>pricingType</code></td><td><code>Int</code></td><td>Market v2 pricing type</td></tr><tr><td><code>creationHash</code></td><td><code>String!</code></td><td>Transaction hash at time of initial entity creation.</td></tr></tbody></table>

## PodOrder

Details regarding a specific Pod Order.

<table><thead><tr><th>Field</th><th width="205.33333333333331">Type</th><th>Descriptoin</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>ID!</code></td><td>Order ID emitted by event</td></tr><tr><td><code>podMarketplace</code></td><td><code>PodMarketplace!</code></td><td>Marketplace used for Order</td></tr><tr><td><code>historyID</code></td><td><code>String!</code></td><td>Unique string to pull and display all historical activity</td></tr><tr><td><code>farmer</code></td><td><code>Farmer!</code></td><td>Farmer placing the Order</td></tr><tr><td><code>createdAt</code></td><td><code>BigInt!</code></td><td>Block timestamp at creation</td></tr><tr><td><code>updatedAt</code></td><td><code>BigInt!</code></td><td>Block timestamp at last update</td></tr><tr><td><code>status</code></td><td><code>MarketStatus!</code></td><td>Enum for valid status:<br><code>ACTIVE</code>, <code>FILLED</code>, <code>FILLED_PARTIAL</code>, <code>CANCELLED</code>, <code>CANCELLED_PARTIAL</code>, <code>EXPIRED</code></td></tr><tr><td><code>fills</code></td><td>[<code>PodFill!]!</code></td><td>Any associated <code>PodFill</code> IDs</td></tr><tr><td><code>podAmount</code></td><td><code>BigInt!</code></td><td>V1 - Original amount of the Ordered Pods</td></tr><tr><td><code>beanAmount</code></td><td><code>BigInt!</code></td><td>V2 - Original amount of Beans used to Order Pods</td></tr><tr><td><code>podAmountFilled</code></td><td><code>BigInt!</code></td><td>Current Filled amount</td></tr><tr><td><code>beanAmountFilled</code></td><td><code>BigInt!</code></td><td>Bean amount Filled</td></tr><tr><td><code>minFillAmount</code></td><td><code>BigInt!</code></td><td>Minimum amount needed to Fill this Order</td></tr><tr><td><code>maxPlaceInLine</code></td><td><code>BigInt!</code></td><td>Max Place in Line for Pods to Fill the Order</td></tr><tr><td><code>pricePerPod</code></td><td><code>Int!</code></td><td>Market v1 price per Pod</td></tr><tr><td><code>pricingFunction</code></td><td><code>Bytes</code></td><td>Market v2 pricing function</td></tr><tr><td><code>pricingType</code></td><td><code>Int</code></td><td>Market v2 pricing type</td></tr><tr><td><code>creationHash</code></td><td><code>String!</code></td><td>Transaction hash at time of initial entity creation.</td></tr></tbody></table>

## PodFill

Fill data for both Listings and Orders.

<table><thead><tr><th width="199">Field</th><th width="192.33333333333331">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>ID!</code></td><td>Beanstalk address - Order/Listing index - transaction hash</td></tr><tr><td><code>podMarketplace</code></td><td><code>PodMarketplace!</code></td><td>Marketplace associated with this Fill</td></tr><tr><td><code>createdAt</code></td><td><code>BigInt!</code></td><td>Block timestamp at creation</td></tr><tr><td><code>listing</code></td><td><code>PodListing</code></td><td>Associated Listing, if any</td></tr><tr><td><code>order</code></td><td><code>PodOrder</code></td><td>Associated Order, if any</td></tr><tr><td><code>from</code></td><td><code>String!</code></td><td>Account Filling the Listing/Order</td></tr><tr><td><code>to</code></td><td><code>Farmer!</code></td><td>Account Filling the Listing/Order</td></tr><tr><td><code>amount</code></td><td><code>BigInt!</code></td><td>Number of Pods Filled</td></tr><tr><td><code>index</code></td><td><code>BigInt!</code></td><td>Index of Plot transferred</td></tr><tr><td><code>start</code></td><td><code>BigInt!</code></td><td>Start of Plot transferred</td></tr><tr><td><code>costInBeans</code></td><td><code>BigInt</code></td><td>Total Beans used to Fill Listing/Order</td></tr></tbody></table>

## Fertilizer

Global Fertilizer data.

<table><thead><tr><th width="133.33333333333331">Field</th><th width="252">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>ID!</code></td><td>Contract address for Fertilizer</td></tr><tr><td><code>supply</code></td><td><code>BigInt!</code></td><td>Total overall supply for Fertilizer tokens</td></tr><tr><td><code>tokens</code></td><td><code>[FertilizerToken!]!</code></td><td>Derived field to <code>FertilizerToken</code></td></tr></tbody></table>

## FertilizerToken

ID level information for Fertilizer tokens. BPF = Beans Per Fertilizer.

<table><thead><tr><th width="189.33333333333331">Field</th><th width="263">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>ID!</code></td><td>Total BPF for purchase</td></tr><tr><td><code>fertilizer</code></td><td><code>Fertilizer!</code></td><td>Fertilizer contract address</td></tr><tr><td><code>supply</code></td><td><code>BigInt!</code></td><td>Total supply for this humidity</td></tr><tr><td><code>humidity</code></td><td><code>BigDecimal!</code></td><td>Humidity paid for this ID</td></tr><tr><td><code>endBpf</code></td><td><code>BigInt!</code></td><td>Ending BPF on creation</td></tr><tr><td><code>startBpf</code></td><td><code>BigInt!</code></td><td>Starting BPF on creation</td></tr><tr><td><code>season</code></td><td><code>Int!</code></td><td>Season created</td></tr><tr><td><code>balances</code></td><td><code>[FertilizerBalance!]!</code></td><td>Derived field to <code>FertilizerBalance</code></td></tr></tbody></table>

## FertilizerBalance

Balance details by Farmer and Fertilizer token.

<table><thead><tr><th width="226.33333333333331">Field</th><th width="219">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>id</code></td><td><code>ID!</code></td><td>Fertilizer Token - Farmer address</td></tr><tr><td><code>fertilizerToken</code></td><td><code>FertilizerToken!</code></td><td>ID of Fertilizer token </td></tr><tr><td><code>farmer</code></td><td><code>Farmer!</code></td><td>Farmer that owns the Fertilizer</td></tr><tr><td><code>amount</code></td><td><code>BigInt!</code></td><td>Current balance of the token</td></tr></tbody></table>

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
