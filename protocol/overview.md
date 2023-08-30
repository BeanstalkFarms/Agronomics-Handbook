# Overview

Beanstalk can be broken down into 7 different Modules consisting of 25 Facets:

* [Sun](sun/) (1 Facet)
* [Silo](silo/) (10 Facets)
* [Field](field/) (2 Facets)&#x20;
* [Barn](barn/) (2 Facets)
* [Market](market/) (1 Facet)
* [Farm](depot/) (5 Facets)
* [Diamond](diamond/) (4 Facets)

### Sun

The Sun handles moving time forward in Beanstalk. It advances Beanstalk to the next Season.

The Sun consists of 1 Facet:

* [`SeasonFacet`](sun/season-facet.md) -> Contains the `gm` function.

### Silo

The Silo offers a passive yield opportunity in the form of Bean seigniorage to Farmers who Deposit Beans and other whitelisted assets. Upon Deposit in the Silo, Farmers receive Stalk and Seeds based on the Bean Denominated Value (BDV) Deposited and the asset Deposited.

The Silo consists of 10 Facets:

* [`SiloFacet`](silo/silo-facet.md) -> Where Farmers Deposit, Withdraw, Claim and Transfer assets in/from the Silo.
* [`BDVFacet`](silo/bdv-facet.md) -> Handles logic for retrieving the BDV of some amount of a whitelisted asset.
* [`WhitelistFacet`](silo/whitelist-facet.md) -> Handles the addition and removal of tokens from the [Deposit Whitelist](https://docs.bean.money/almanac/farm/silo#deposit-whitelist).
* [`ConvertFacet`](silo/convert-facet.md) -> Where Farmers Convert a Deposit of a whitelisted asset to a Deposit of another whitelisted asset.
* [`ConvertGettersFacet`](silo/convert-facet-1.md) -> Contains view functions for Convert data.
* [`EnrootFacet`](silo/convert-facet-2.md) -> Where Farmers Enroot their Unripe Deposits.
* [`ApprovalFacet`](silo/approval-facet.md) -> Contains logic for Deposit approvals and permits.
* [`MetadataFacet`](silo/metadata-facet.md) -> Contains on-chain metadata for the Deposit ERC-1155 tokens.
* [`MigrationFacet`](silo/migration-facet.md) -> Where Farmers migrate to the latest Silo accounting system.
* [`LegacyClaimWithdrawalFacet`](silo/legacy-claim-withdrawal-facet.md) -> Facilitates backwards compatibility for Farmers with unclaimed Withdrawals before the [Silo V3 upgrade](https://bean.money/bip-36).

### Field

The Field is Beanstalk's native credit facility. Anytime Beanstalk is willing to borrow Beans from the market, it issues Soil in the Field. Beans are Sown in exchange for Pods, the Beanstalk-native debt asset. Loans to Beanstalk are issued with a fixed interest rate, known as the Temperature, and an unknown maturity date.

Pods become Harvestable Pods that can be Harvested (redeemed) for 1 Bean each on a First In, First Out (FIFO) basis. There is no penalty for waiting to Harvest Pods.

The Field consists of 2 Facets:

* [`FieldFacet`](field/field-facet.md) -> Where Farmers Sow Beans into Pods and Harvest Pods into Beans.
* [`FundraiserFacet`](field/fundraiser-facet.md) -> Where Farmers create and fund Fundraisers through Sowing non-Bean assets into Pods.

### Barn

The Barn was built after Beanstalk was exploited on April 17, 2022. The Barn distributes Bean rewards to those who hold Fertilizer tokens from participation in the Barn Raise. It also handles the Chopping of Unripe Beans and Unripe LP into their underlying assets at a potential penalty.

{% hint style="warning" %}
In the Beanstalk ecosystem,&#x20;

* **Unfertilized Beans** are referred to as **Sprouts**;
* **Fertilized Beans** are referred to as **Rinsable Sprouts** that can be **Rinsed**; and
* **Underlying** assets are referred to as **Ripe** assets. &#x20;

See [Terminology Discrepancies](../misc/terminology-discrepancies.md).
{% endhint %}

Unfertilized Beans become Fertilized Beans that can be claimed (redeemed) for 1 Bean each on a pari passu basis. There is no penalty for waiting to claim Fertilized Beans.

The Barn consists of 2 Facets:

* [`FertilizerFacet`](barn/fertilizer-facet.md) -> Where Farmers buy Fertilizer with USDC and claim Beans earned from Fertilizer.
* [`UnripeFacet`](barn/unripe-facet.md) -> Allows Farmers to Chop Unripe assets into their underlying assets at a potential penalty.

### Market

The Market houses various DEXs for zero fee trading. Currently only Pods can be traded on the Market.

Pods can be bought and sold in a decentralized, trustless fashion on the [Pod Market](https://docs.bean.money/almanac/farm/market#the-pod-market). The Pod Market creates liquidity for Pods through an on-chain order book.

Sellers can List Pods or Fill open Pod Orders placed by buyers. Buyers can Order Pods or Fill open Pod Listings placed by sellers.

The Market consists of 1 Facet:

* [`MarketplaceFacet`](market/marketplace-facet.md) -> Contains the Pod Market where Farmers create, Fill and Cancel Pod Listings and Orders, as well as transfer Pods.

### Farm

The Farm allows Farmers to call multiple functions in a single transaction and use assets between different function in a composable manner, without those assets every leaving Beanstalk (thanks to [Internal Balances](../overview/internal-balances.md)).

The Farm consists of 5 Facets:

* [`FarmFacet`](depot/farm-facet.md) -> Contains the `farm` function, which allows Farmers to call a series of functions together within Beanstalk.
* [`DepotFacet`](depot/depot-facet.md) -> Wraps the standalone [Pipeline](https://evmpipeline.org/) contract, providing access to Pipeline from Beanstalk through the use of the `farm` function.
* [`TokenFacet`](depot/token-facet.md) -> Supports transferring assets between Internal and External Balances and between different accounts. Also supports Wrap/Unwrap logic for ETH.
* [`TokenSupportFacet`](depot/token-support-facet.md) -> Handles token permits.
* [`CurveFacet`](depot/curve-facet.md) -> Provides an interface to exchange and add/remove liquidity on Curve directly through Beanstalk.

### Diamond

The Diamond Module controls and manages the Beanstalk contract by providing functionality to upgrade and view supported functions in Beanstalk. It also controls which address owns the Beanstalk contract.

The Diamond Module consists of 4 Facets:

* [`DiamondCutFacet`](diamond/diamond-cut-facet.md) -> Provides functionality for the owner to add/remove/replace functions within the Beanstalk contract.
* [`DiamondLoupeFacet`](diamond/diamond-loupe-facet.md) -> Allows anyone to see the available functions within Beanstalk.
* [`OwnershipFacet`](diamond/ownership-facet.md) -> Manages which address owns Beanstalk.
* [`PauseFacet`](diamond/pause-facet.md) -> Allows the owner of Beanstalk to Pause/Unpause Beanstalk.
