# Enroot Facet

{% hint style="warning" %}
Note that this page has not been updated to reflect the current state of Beanstalk, but is left here as a reference.
{% endhint %}

The Enroot Facet handles logic for Enrooting Unripe Deposits.

## Call Functions

### [Enroot Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/EnrootFacet.sol#L57)

```solidity
function enrootDeposit(
    address token,
    int96 stem,
    uint256 amount
) external payable nonReentrant mowSender(token);
```

Claims outstanding Revitalized Stalk and Seeds and updates BDV of a single Unripe Deposit.

| Parameter | Type      | Description                        |
| --------- | --------- | ---------------------------------- |
| `token`   | `address` | Address of whitelist Unripe ERC20. |
| `stem`    | `int96`   | Stem of Deposit to Enroot.         |
| `amount`  | `uint256` | Amount to Enroot.                  |

### [Enroot Deposits](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/EnrootFacet.sol#L116)

```solidity
function enrootDeposits(
    address token,
    int96[] calldata stems,
    uint256[] calldata amounts
) external payable nonReentrant mowSender(token);
```

Claims outstanding Revitalized Stalk and Seeds and updates BDV of multiple Unripe Deposits.

| Parameter | Type        | Description                                          |
| --------- | ----------- | ---------------------------------------------------- |
| `token`   | `address`   | Address of whitelist Unripe ERC20.                   |
| `stems`   | `int96[]`   | Array of Stems of Deposits to Enroot.                |
| `amounts` | `uint256[]` | Array of amounts (corresponding to Stems) to Enroot. |

## View Functions

None.

## Events

### [Remove Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/EnrootFacet.sol#L22) <a href="#event-remove-deposits" id="event-remove-deposits"></a>

```solidity
event RemoveDeposit(
    address indexed account,
    address indexed token,
    int96 stem,
    uint256 amount,
    uint256 bdv
);
```

Emitted when `account` removes a single Deposit from the Silo. Occurs during Withdraw and Convert.

| Parameter | Type      | Description                           |
| --------- | --------- | ------------------------------------- |
| `account` | `address` | The Farmer whose Deposit was removed. |
| `token`   | `address` | Whitelisted token address.            |
| `stem`    | `int96`   | The Stem of the Deposit.              |
| `amount`  | `uint256` | The token amount of the Deposit.      |
| `bdv`     | `uint256` | The BDV associated with the Deposit.  |

### [Remove Deposits](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/EnrootFacet.sol#L30) <a href="#event-remove-deposits" id="event-remove-deposits"></a>

```solidity
event RemoveDeposits(
    address indexed account,
    address indexed token,
    int96[] stems,
    uint256[] amounts,
    uint256 amount,
    uint256[] bdvs
);
```

Emitted when `account` removes multiple Deposits from the Silo. Occurs during Withdraw and Convert.

| Parameter | Type        | Description                                                      |
| --------- | ----------- | ---------------------------------------------------------------- |
| `account` | `address`   | The Farmer whose Deposits were removed.                          |
| `token`   | `address`   | Whitelisted token address.                                       |
| `stems`   | `int96[]`   | Stems of the Deposits.                                           |
| `amounts` | `uint256[]` | The token amounts of the Deposits, corresponding to `stems`.     |
| `amount`  | `uint256`   | Sum of `amounts`.                                                |
| `bdvs`    | `uint256[]` | The BDVs associated with the Deposits, corresponding to `stems`. |
