# Convert Facet

The Convert Facet handles Conversions between assets in the Silo and Enrooting Unripe Deposits.

## Call Functions

### [Convert](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ConvertFacet.sol#L73)

```solidity
function convert(
    bytes calldata convertData,
    int96[] memory stems,
    uint256[] memory amounts
)
    external
    payable
    nonReentrant
    returns (int96 toStem, uint256 fromAmount, uint256 toAmount, uint256 fromBdv, uint256 toBdv);
```

Convert allows a user to Convert from one Deposited asset to another, given that the Conversion is on the Convert Whitelist. For example, a Farmer can Convert LP into Bean only when the Bean price is below peg, and vice versa. Read more about [Convert in the Farmers' Almanac](https://docs.bean.money/almanac/peg-maintenance/convert).

| Parameter     | Type        | Description                                        |
| ------------- | ----------- | -------------------------------------------------- |
| `convertData` | `bytes`     | Input parameters to determine the Conversion type. |
| `stems`       | `int98[]`   | The Stems of the Deposits to Convert.              |
| `amounts`     | `uint256[]` | The amounts within each Deposit to Convert.        |

| Return Value | Type      | Description                             |
| ------------ | --------- | --------------------------------------- |
| `toStem`     | `int96`   | The new Stems of the Converted Deposit. |
| `fromAmount` | `uint256` | The amount of tokens Converted from.    |
| `toAmount`   | `uint256` | The amount of tokens Converted to.      |
| `fromBdv`    | `uint256` | The BDV of the Deposits Converted from. |
| `toBdv`      | `uint256` | The BDV of the Deposits Converted to.   |

### [Enroot Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ConvertFacet.sol#L124)

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

### [Enroot Deposits](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ConvertFacet.sol#L183)

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

### [Get Max Amount In](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ConvertFacet.sol#L377)

```solidity
function getMaxAmountIn(address tokenIn, address tokenOut)
    external
    view
    returns (uint256 amountIn);
```

Estimate the maximum number of tokens that can currently be Converted from `tokenIn` to `tokenOut`.&#x20;

| Parameter  | Type      | Description                                        |
| ---------- | --------- | -------------------------------------------------- |
| `tokenIn`  | `address` | The whitelisted token to estimate Converting from. |
| `tokenOut` | `address` | The whitelisted token to estimate Converting to.   |

| Return Value | Type      | Description                                                                                 |
| ------------ | --------- | ------------------------------------------------------------------------------------------- |
| `amountIn`   | `uint256` | The maximum number of tokens that can currently be Converted from `tokenIn` to `tokenOut`.  |

### [Get Amount Out](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ConvertFacet.sol#L385)

```solidity
function getAmountOut(
    address tokenIn,
    address tokenOut,
    uint256 amountIn
) external view returns (uint256 amountOut);
```

Estimate the amount of tokens received from Converting `tokenIn` to `tokenOut` given an amount of `tokenIn`.

| Parameter  | Type      | Description                                        |
| ---------- | --------- | -------------------------------------------------- |
| `tokenIn`  | `address` | The whitelisted token to estimate Converting from. |
| `tokenOut` | `address` | The whitelisted token to estimate Converting to.   |

| Return Value | Type      | Description                                                                       |
| ------------ | --------- | --------------------------------------------------------------------------------- |
| `amountOut`  | `uint256` | The amount of `tokenOut` received from a Conversion from `tokenIn` to `tokenOut`. |

## Events

### [Convert](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ConvertFacet.sol#L28) <a href="#event-convert" id="event-convert"></a>

```solidity
event Convert(
    address indexed account,
    address fromToken,
    address toToken,
    uint256 fromAmount,
    uint256 toAmount
);
```

Emitted upon each Conversion.

| Parameter    | Type      | Description                                |
| ------------ | --------- | ------------------------------------------ |
| `account`    | `address` | Address of Farmer that Converted.          |
| `fromToken`  | `address` | Whitelisted token that was Converted from. |
| `toToken`    | `address` | Whitelisted token that was Converted to.   |
| `fromAmount` | `uint256` | Amount of `fromToken` Converted.           |
| `toAmount`   | `uint256` | Amount of `toAmount` Converted to.         |

### [Remove Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master9f286e1f1b1e67bc40d35aaf4b16e5c6d83ebdd9/protocol/contracts/beanstalk/silo/ConvertFacet.sol#L36) <a href="#event-remove-deposits" id="event-remove-deposits"></a>

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

### [Remove Deposits](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ConvertFacet.sol#L44) <a href="#event-remove-deposits" id="event-remove-deposits"></a>

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
