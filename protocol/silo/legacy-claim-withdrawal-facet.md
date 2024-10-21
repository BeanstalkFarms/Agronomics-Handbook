# Legacy Claim Withdrawal Facet

{% hint style="warning" %}
Note that this page has not been updated to reflect the current state of Beanstalk, but is left here as a reference.
{% endhint %}

The Legacy Claim Withdrawal Facet allows anyone to Claim and read Withdrawals. [Silo V3](https://bean.money/bip-36) removed the Withdrawal Freeze from the Silo. Withdrawing now directly sends ERC-20 tokens to the Farmer's Farm or Circulating balances instead of creating a Withdrawal.

Although new Withdrawals cannot be created, the claim Withdrawal functionality has been preserved in this facet to allow pre-existing unclaimed Withdrawals to still be claimed.

## Call Functions

### [Claim Withdrawal](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/LegacyClaimWithdrawalFacet.sol#L35)

```solidity
function claimWithdrawal(
    address token,
    uint32 season,
    LibTransfer.To mode
) external payable nonReentrant;
```

Claims tokens from a Withdrawal.

| Parameter | Type      | Description                                                                                             |
| --------- | --------- | ------------------------------------------------------------------------------------------------------- |
| `token`   | `address` | Address of whitelisted token.                                                                           |
| `season`  | `uint32`  | Season of Withdrawal to claim.                                                                          |
| `mode`    | `To`      | The balance to transfer claimed assets to; see [`LibTransfer.To`](../../overview/internal-balances.md). |

### [Claim Withdrawals](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/LegacyClaimWithdrawalFacet.sol#L50)

```solidity
function claimWithdrawals(
    address token,
    uint32[] calldata seasons,
    LibTransfer.To mode
) external payable nonReentrant;
```

Claims tokens from multiple Withdrawals.

| Parameter | Type       | Description                                                                                             |
| --------- | ---------- | ------------------------------------------------------------------------------------------------------- |
| `token`   | `address`  | Address of whitelisted token.                                                                           |
| `seasons` | `uint32[]` | Array of Seasons to claim.                                                                              |
| `mode`    | `To`       | The balance to transfer claimed assets to; see [`LibTransfer.To`](../../overview/internal-balances.md). |

## View Functions

### [Get Withdrawal](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/LegacyClaimWithdrawalFacet.sol#L66)

```solidity
function getWithdrawal(
    address account,
    address token,
    uint32 season
) external view returns (uint256);
```

Get the amount of `token` in the Withdrawal `season` for `account`.

| Parameter | Type      | Description                       |
| --------- | --------- | --------------------------------- |
| `account` | `address` | Farmer to get the Withdrawal for. |
| `token`   | `address` | Token address of the Withdrawal.  |
| `season`  | `uint32`  | Season of the Withdrawal.         |

| Return Value | Description                                                     |
| ------------ | --------------------------------------------------------------- |
| `uint256`    | Amount of `token` Withdrawn for the Farmer in the given Season. |

### [Get Total Withdrawn](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/LegacyClaimWithdrawalFacet.sol#L78)

```solidity
function getTotalWithdrawn(address token) external view returns (uint256);
```

Get the total amount of `token` currently Withdrawn from the Silo across all Farmers.

| Parameter | Type      | Description                  |
| --------- | --------- | ---------------------------- |
| `token`   | `address` | The Withdrawn token address. |

| Return Value | Description                        |
| ------------ | ---------------------------------- |
| `uint256`    | Total amount of Withdrawn `token`. |

## Events

None.
