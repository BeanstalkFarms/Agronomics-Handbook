# Convert Facet

## Call Functions

### Convert

```solidity
function convert(
    bytes calldata convertData,
    uint32[] memory crates,
    uint256[] memory amounts
) external payable nonReentrant returns (
    uint32 toSeason, 
    uint256 fromAmount, 
    uint256 toAmount, 
    uint256 fromBdv, 
    uint256 toBdv
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/ConvertFacet.sol#L46)

| Parameter     | Type        | Description |
|---------------|-------------|-------------|
| `convertData` | `bytes`     | WIP         |
| `crates`      | `uint32[]`  | WIP         |
| `amounts`     | `uint256[]` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `toSeason`   | `uint32`  | WIP         |
| `fromAmount` | `uint256` | WIP         |
| `toAmount`   | `uint256` | WIP         |
| `fromBdv`    | `uint256` | WIP         |
| `toBdv`      | `uint256` | WIP         |

## View Functions

### Get Max Amount In

```solidity
function getMaxAmountIn(
    address tokenIn,
    address tokenOut
) external view returns (uint256 amountIn);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/ConvertFacet.sol#L161)

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `tokenIn`  | `address` | WIP         |
| `tokenOut` | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `amountIn`   | `uint256` | WIP         |

### Get Amount Out

```solidity
function getAmountOut(
    address tokenIn,
    address tokenOut,
    uint256 amountIn
) external view returns (uint256 amountOut);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/ConvertFacet.sol#L169)

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `tokenIn`  | `address` | WIP         |
| `tokenOut` | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `amountIn`   | `uint256` | WIP         |

## Events

### Convert

```solidity
event Convert(
    address indexed account,
    address fromToken,
    address toToken,
    uint256 fromAmount,
    uint256 toAmount
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/ConvertFacet.sol#L24)

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `account`    | `address` | WIP         |
| `fromToken`  | `address` | WIP         |
| `toToken`    | `address` | WIP         |
| `fromAmount` | `uint256` | WIP         |
| `toAmount`   | `uint256` | WIP         |

### Remove Deposits

```solidity
event RemoveDeposits(
    address indexed account,
    address indexed token,
    uint32[] seasons,
    uint256[] amounts,
    uint256 amount
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/ConvertFacet.sol#L32)

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `account` | `address`   | WIP         |
| `token`   | `address`   | WIP         |
| `seasons` | `uint32[]`  | WIP         |
| `amounts` | `uint256[]` | WIP         |
| `amount`  | `uint256`   | WIP         |
