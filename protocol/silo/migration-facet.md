# Migration Facet

{% hint style="warning" %}
Note that this page has not been updated to reflect the current state of Beanstalk, but is left here as a reference.
{% endhint %}

The Migration Facet contains functions related to [Silo V3](https://bean.money/bip-36). Farmers are required to migrate to the new accounting system created by the Silo V3 upgrade.

## Call Functions

### [Mow and Migrate](https://github.com/BeanstalkFarms/Beanstalk/blob/9f286e1f1b1e67bc40d35aaf4b16e5c6d83ebdd9/protocol/contracts/beanstalk/silo/MigrationFacet.sol#L41)

```solidity
function mowAndMigrate(
    address account, 
    address[] calldata tokens, 
    uint32[][] calldata seasons,
    uint256[][] calldata amounts,
    uint256 stalkDiff,
    uint256 seedsDiff,
    bytes32[] calldata proof
) external payable;
```

Migrates a Farmer's Deposits from the old (Seasons based) to the new Silo (Stems based) accounting system.

When migrating an account, a user must submit all of the account's Deposits or the migration will not pass because the Seed check will fail. The Seed check adds up the BDV of all submitted Deposits, multiplies by the corresponding Seed amount for each token type, then compares that to the total Seeds stored for that user. If everything matches, the migration is valid.

| Parameter   | Type          | Description                                                                    |
| ----------- | ------------- | ------------------------------------------------------------------------------ |
| `account`   | `address`     | Address of the account to migrate.                                             |
| `tokens`    | `address[]`   | Array of whitelisted token addresses to migrate.                               |
| `seasons`   | `uint256[][]` | The Seasons for the Deposits.                                                  |
| `amounts`   | `uint256[][]` | The amounts of those Deposits which are to be migrated.                        |
| `stalkDiff` | `uint256`     | Discrepancy between the calculated Stalk and the actual Stalk the account has. |
| `seedsDiff` | `uint256`     | Discrepancy between the calculated Seeds and the actual Seeds the account has. |
| `proof`     | `bytes32[]`   | The Merkle proof that confirms `stalkDiff` and `seedsDiff`.                    |

### [Mow and Migrate No Deposits](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/MigrationFacet.sol#L63)

```solidity
function mowAndMigrateNoDeposits(address account) external payable;
```

Migrate an account to Silo V3 that has no Deposits.

| Parameter | Type      | Description                        |
| --------- | --------- | ---------------------------------- |
| `account` | `address` | Address of the account to migrate. |

## View Functions

### [Balance Of Legacy Seeds](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/MigrationFacet.sol#L67)

```solidity
function balanceOfLegacySeeds(address account) external view returns (uint256);
```

Gets balance of Seeds for a Farmer that hasn't migrated.

| Parameter | Type      | Description         |
| --------- | --------- | ------------------- |
| `account` | `address` | A Farmer's address. |

| Return Value | Description                                |
| ------------ | ------------------------------------------ |
| `uint256`    | Balance of Seeds for an unmigrated Farmer. |

### [Balance Of Grown Stalk up to Stems Deployment](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/MigrationFacet.sol#L71)

```solidity
function balanceOfGrownStalkUpToStemsDeployment(address account)
    external
    view
    returns (uint256);
```

Gets a Farmer's balance of Grown Stalk at the time of Stems deployment (Silo V3 upgrade).

| Parameter | Type      | Description        |
| --------- | --------- | ------------------ |
| `account` | `address` | Address of Farmer. |

| Return Value | Description                                                        |
| ------------ | ------------------------------------------------------------------ |
| `uint256`    | Grown Stalk balance for `account` at the time of Stems deployment. |

### [Get Deposit Legacy](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/MigrationFacet.sol#L90)

```solidity
function getDepositLegacy(
    address account,
    address token,
    uint32 season
) external view returns (uint128, uint128);
```

Locate the token amount and BDV for a Farmer's Deposit in legacy storage.

| Parameter | Type      | Description                                   |
| --------- | --------- | --------------------------------------------- |
| `account` | `address` | Address of Farmer.                            |
| `token`   | `address` | Whitelisted token address to get Deposit for. |
| `season`  | `uint32`  | Season of the Deposit in legacy storage.      |

| Return Value | Description                                         |
| ------------ | --------------------------------------------------- |
| `uint128`    | Amount of `token` of the Deposit in legacy storage. |
| `uint128`    | BDV of the Deposit in legacy storage.               |

## Events

None.
