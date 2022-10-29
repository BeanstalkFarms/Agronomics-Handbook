# Silo

Farmers can Deposit assets on the [Deposit Whitelist](https://docs.bean.money/farm/silo#deposit-whitelist) into the Silo in exchange for Stalk and Seeds. The number of Stalk and Seeds received is dependent on the BDV at the time of Deposit, the Stalk per BDV and the Seeds per BDV. Stalk entitles Farmers to a pro-rata portion of Bean seignorage distributed to the Silo and Seeds grown into 0.0001 Stalk each Season.

A Farmer can Withdraw at any time, but must forfeit all Stalk and Seeds associated with the Deposit. All Withdrawals are subject to an unlock period (currently set to the remainder of the current Season). Once a Withdraw is complete, it can be Claimed at any time.

Farmers can also convert a Deposited asset into a different one via the Convert function if the ability to convert between those two assets is on the [Convert Whitelist](https://docs.bean.money/peg-maintenance/convert#convert-whitelist). Each Convert type must be approved via governance and the Convert functionality must be added to `LibConvert`.

#### Adding and Removing Assets on the Deposit Whitelist

Assets can only be Deposited into the Silo if the assets are on the Deposit Whitelist. A token is considered on the Deposit Whitelist if it has a non-zero Silo Settings in Beanstalk’s storage. Silo Settings for each asset on the Deposit Whitelist are stored in the `s.ss` mapping in [`AppStorage`](../../overview/app-storage.md) defined as:

```solidity
struct SiloSettings {
    bytes4 selector;
    uint32 seeds;
    uint32 stalk;
}

mapping(address => Storage.SiloSettings) ss;
```

* The key used in the mapping is the ERC-20 token address.
* `selector` is a function selector that calculates the BDV of a given `amount` of the token. `selector` should be an encoded `external view` function added to the Beanstalk diamond. BDV is represented with 6 decimal places.
* `seeds` is the number of Seeds per BDV that a Farmer receives for Depositing this asset. For example, `seeds` is 2 for Bean and 4 for BEAN:3CRV LP tokens.
* `stalk` is the number of Stalk per BDV that a Farmer receives for Depositing this asset. Because Stalk has 10 decimals compared to the 6 that BDV has, 10,000 equals 1. `stalk` is 10,000 for both Bean and BEAN:3CRV LP tokens.

Tokens can be added to the Deposit Whitelist via BIP. In order to Whitelist a token, an address, BDV function selector, Stalk per BDV and Seeds per BDV must be included in the proposal. The BDV function selector must either already be added to Beanstalk or be added as a part of the BIP.

Similarly, tokens can be Dewhitelisted (removed from the Deposit Whitelist) via BIP.

#### Bean Denominated Value

All Deposited assets are valued based on the Bean Denominated Value (BDV) at the time Deposit. Each asset on the Deposit Whitelist has a unique BDV function in the [`BDVFacet`](bdv-facet.md) to calculate the BDV of a given amount of the asset.

#### Stalk and Seeds

Stalk entitles the Farmer to a pro rata portion of at least 1/3 of Bean mints and 1 Stalk is 1 vote in Governance. Beans mints allocated to the Silo are called Earned Beans. Farmers also receive 1 Earned Stalk and 2 Earned Seeds for each Earned Bean.

Each Seed grows 0.0001 Stalk every Season. Stalk grown from Seeds is called Grown Stalk.

There are 3 types of Stalk:

* Stalk -> Stalk stored in a Farmer’s account storage. Stalk is acquired by Depositing, Converting, Updating or Planting.
* Earned Stalk -> A Farmer receives 1 Earned Stalk for each Earned Bean. Earned Stalk automatically compounds and receives a portion of Bean mints. Earned Stalk is claimed as part of the `plant()` function, which turns it into Stalk. Because it is considered active, Earned Stalk has already been minted and it is included in the `totalStalk()` and `balanceOfStalk()` counts. To the Farmer, Earned Stalk is no different from Stalk and just serves as an indicator of how much Stalk has been earned through Bean seignorage since the last `plant()` call.
* Grown Stalk -> 0.0001 Grown Stalk is grown from every Seed each Season. Grown Stalk is **not** considered active and thus does not receive a pro rata portion of Bean mints. It is claimed via the `update()` function in Beanstalk, which turns it into Stalk. Because Grown Stalk is not active, Stalk isn’t minted until Grown Stalk is updated and thus Grown Stalk is **not** included in the `totalStalk()` and `balanceOfStalk()` counts.

{% hint style="warning" %}
In the Beanstalk ecosystem, **Update** (i.e., updating Grown Stalk) is referred to as **Mow** (i.e., Mowing Grown Stalk). See [Terminology Discrepancies](../../misc/terminology-discrepancies.md).
{% endhint %}

There are 2 types of Seeds:

* Seeds → Seeds stored in a Farmer’s account storage. Seeds are acquired by Depositing, Planting and in certain cases, Converting.&#x20;
* Earned Seeds → A Farmer receives 2 Earned Seeds for each Earned Bean. Earned Seeds are **not** active. Earned Seeds can be claimed via the `plant()` function, which turns them into Seeds. Because Earned Seeds are **not** active, they are not included in the `totalSeeds()` or `balanceOfSeeds()` function.

{% hint style="warning" %}
In the Beanstalk ecosystem, **Earned Seeds** are referred to as **Plantable Seeds**. See [Terminology Discrepancies](../../misc/terminology-discrepancies.md).
{% endhint %}

#### Deposit

Farmers can deposit Whitelisted ERC-20 tokens in the Silo in exchange for Stalk and Seeds via the `deposit()` function. `deposit()` first calls the BDV function selector stored in Storage to calculate the BDV of the Deposit. It then distributes Stalk and Seeds to the Farmer based on the Stalk per BDV and Seeds per BDV.

A Deposit is stored in the current Season to record at what Season the Seeds associated with the Deposit started accruing Grown Stalk. The total Seeds and Stalk associated with a Deposit can be calculated as:

```solidity
seeds = depositBdv * s.ss[token].seeds;
stalk = depositBdv * s.ss[token].stalk + (currentSeason - depositSeason) * seeds
```

Deposits are stored in the Account storage as:

```solidity
mapping(address => mapping(uint32 => Deposit)) deposits;

struct Deposit {
    uint128 amount;
    uint128 bdv;
}
```

* The mapping is from token address to Season to Deposit.
* `amount` is the amount of tokens in the Deposit. A Farmer can Withdraw up to `amount`.
* `bdv` is the BDV of the amount of tokens at the time of Deposit.

#### Withdraw

Farmers can Withdraw any Deposit via the `withdrawDeposit()` or `withdrawDeposits()` functions. When a Farmer Withdraws, they specific the token, the Season(s) of the Deposit(s) and the corresponding amount(s) to Withdraw.

In order to Withdraw a Deposit, a Farmer must burn all of the Stalk and Seeds associated with the Deposit.

A Withdraw is locked for a certain number of Seasons. This number is stored in `s.season.withdrawSeasons`. This number is equal to the # of full Seasons required for Withdraw plus 1. The plus 1 accounts for the partial Season that Farmer Withdraws in.

The Season of a Withdrawal is equal to the Season at which the Withdrawal can be Claimed (Not the Season that the Withdrawal is initiated).

A Withdraw is in the following mapping:

```solidity
mapping(address => mapping(uint32 => uint256)) withdrawals;
```

* The mapping is from token address to Season to amount

#### Claim Withdrawal

Farmers can Claim Withdrawals that have been unlocked via the `claimWithdrawal()` and `claimWithdrawals()` functions. A Withdrawal is Claimable if the current Season is greater than or equal to the Season of the Withdrawal. A Withdrawal is Claimed by specifying the token and Season(s) of the Withdrawals to Claim. When a Withdrawals is Claimed, the Withdrawal is deleted and the Farmer receives the corresponding amount of the underlying token.

#### Convert

Farmers can Convert one asset on the Deposit Whitelist (Token A) to another asset on the Deposit Whitelist (Token B) if Converting from Token A to Token B is on the Convert Whitelist. `convert()` takes in a `convertData` payload that stores the encoded Convert data payload. Convert data is encoded so that different Convert types can have different parameters as necessary. However, each Convert type must specify at least the Convert type and the amount to Convert. Farmers must also specify the Season(s) of Deposits and corresponding amounts to Convert.

Convert does 3 main actions:

1. Converts some amount of Token A to Token B via `LibConvert`;
2. Removes Deposits of Token A equal to the amount of Token A that was Converted; and
3. Adds a Deposit of Token B equal to the amount received in Convert.

Convert uses the maximum of the BDV of Token A and Token B so that BDV is never lost. Thus, the Farmer won’t lose any Stalk during Convert, but may still gain Stalk depending the BDV of Token B. Seeds can be gained or lost depending on the Seeds per BDV of Token B versus Token A.

Grown Stalk is preserved during Convert and the Season that Converted assets are Deposited into is depending on the number of Grown Stalk:

```solidity
depositSeason = currentSeason - (grownStalk / depositSeeds)
```

Converts may have a maximize amount that can be converted from Token A to Token B. For instance, Deposited Beans can only be converted into Deposited BEAN:3CRV LP tokens if the price in the BEAN:3CRV pool is greater than $1 after the Convert. This can be retrieved via the `getMaxAmountIn()` function.

The `getAmountOut()` function returns the expected output amount of a given Convert.

New Converts can be approved via adding new Convert types to `LibConvertData` and adding the Convert case to `LibConvert`.
