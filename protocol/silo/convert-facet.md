# Convert Facet

## Call Functions

### [Convert](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ConvertFacet.sol#L46)

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

### [Get Max Amount In](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ConvertFacet.sol#L161)

```solidity
function getMaxAmountIn(
    address tokenIn,
    address tokenOut
) external view returns (uint256 amountIn);
```

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `tokenIn`  | `address` | WIP         |
| `tokenOut` | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `amountIn`   | `uint256` | WIP         |

### [Get Amount Out](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ConvertFacet.sol#L169)

```solidity
function getAmountOut(
    address tokenIn,
    address tokenOut,
    uint256 amountIn
) external view returns (uint256 amountOut);
```

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `tokenIn`  | `address` | WIP         |
| `tokenOut` | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `amountIn`   | `uint256` | WIP         |

## Events

### [Convert](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ConvertFacet.sol#L24) <a href="#event-convert" id="event-convert"></a>

```solidity
event Convert(
    address indexed account,
    address fromToken,
    address toToken,
    uint256 fromAmount,
    uint256 toAmount
);
```

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `account`    | `address` | WIP         |
| `fromToken`  | `address` | WIP         |
| `toToken`    | `address` | WIP         |
| `fromAmount` | `uint256` | WIP         |
| `toAmount`   | `uint256` | WIP         |

### [Remove Deposits](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ConvertFacet.sol#L32) <a href="#event-remove-deposits" id="event-remove-deposits"></a>

```solidity
event RemoveDeposits(
    address indexed account,
    address indexed token,
    uint32[] seasons,
    uint256[] amounts,
    uint256 amount
);
```

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `account` | `address`   | WIP         |
| `token`   | `address`   | WIP         |
| `seasons` | `uint32[]`  | WIP         |
| `amounts` | `uint256[]` | WIP         |
| `amount`  | `uint256`   | WIP         |
