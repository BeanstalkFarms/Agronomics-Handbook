# Unripe Facet

Manage the logic of the vesting process for the Barnraised Funds.

## Call Functions

### [Chop](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L51)

```solidity
function chop(
    address unripeToken,
    uint256 amount,
    LibTransfer.From fromMode,
    LibTransfer.To toMode
) external payable nonReentrant returns (uint256 underlyingAmount);
```

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |
| `amount`      | `uint256` | WIP         |
| `fromMode`    | `From`    | WIP         |
| `toMode`      | `To`      | WIP         |

| Return Value       | Type      | Description |
|--------------------|-----------|-------------|
| `underlyingAmount` | `uint256` | WIP         |

### [Pick](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L72)

```solidity
function pick(
    address token,
    uint256 amount,
    bytes32[] memory proof,
    LibTransfer.To mode
) external payable nonReentrant;
```

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `token`   | `address`   | WIP         |
| `amount`  | `uint256`   | WIP         |
| `proof`   | `bytes32[]` | WIP         |
| `mode`    | `To`        | WIP         |

### [Add Unripe Token](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L227)

```solidity
function addUnripeToken(
    address unripeToken,
    address underlyingToken,
    bytes32 root
) external payable nonReentrant;
```

| Parameter         | Type      | Description |
|-------------------|-----------|-------------|
| `unripeToken`     | `address` | WIP         |
| `underlyingToken` | `address` | WIP         |
| `root`            | `bytes32` | WIP         |

## View Functions

### [Picked](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L97)

```solidity
function picked(address account, address token)
    public
    view
    returns (bool);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `bool`       | WIP         |

### [Get Underlying](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L105)

```solidity
function getUnderlying(address unripeToken, uint256 amount)
    public
    view
    returns (uint256 redeem);
```

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |
| `amount`      | `uint256` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `redeem`     | `uint256` | WIP         |

### [Get Penalty](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L123)

```solidity
function getPenalty(address unripeToken)
    external
    view
    returns (uint256 penalty);
```

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `penalty`    | `uint256` | WIP         |

### [Get Penalized Underlying](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L131)

```solidity
function getPenalizedUnderlying(address unripeToken, uint256 amount)
    public
    view
    returns (uint256 redeem);
```

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |
| `amount`      | `uint256` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `redeem`     | `uint256` | WIP         |

### [_Get Penalized Underlying](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L139)

```solidity
function _getPenalizedUnderlying(address unripeToken, uint256 amount, uint256 supply)
    public
    view
    returns (uint256 redeem);
```

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |
| `amount`      | `uint256` | WIP         |
| `supply`      | `uint256` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `redeem`     | `uint256` | WIP         |

### [Is Unripe](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L149)

```solidity
function isUnripe(address unripeToken) public view returns (bool unripe);
```

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |

| Return Value | Type   | Description |
|--------------|--------|-------------|
| `unripe`     | `bool` | WIP         |

### [Balance Of Underlying](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L153)

```solidity
function balanceOfUnderlying(address unripeToken, address account)
    external
    view
    returns (uint256 underlying);
```

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |
| `account`     | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `underlying` | `uint256` | WIP         |

### [Balance Of Penalized Underlying](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L162)

```solidity
function balanceOfPenalizedUnderlying(address unripeToken, address account)
    external
    view
    returns (uint256 underlying);
```

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |
| `account`     | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `underlying` | `uint256` | WIP         |

### [Get Recap Funded Percent](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L174)

```solidity
function getRecapFundedPercent(address unripeToken)
    public
    view
    returns (uint256 percent);
```

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `percent`    | `uint256` | WIP         |

### [Get Percent Penalty](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L187)

```solidity
function getPercentPenalty(address unripeToken)
    external
    view
    returns (uint256 penalty);
```

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `penalty`    | `uint256` | WIP         |

### [Get Recap Paid Percent](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L195)

```solidity
function getRecapPaidPercent() external view returns (uint256 penalty);
```

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `penalty`    | `uint256` | WIP         |

### [Get Recap Paid Percent Amount](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L199)

```solidity
function getRecapPaidPercentAmount(uint256 amount)
    private
    view
    returns (uint256 penalty);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `amount`  | `uint256` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `penalty`    | `uint256` | WIP         |

### [Get Underlying Per Unripe Token](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L207)

```solidity
function getUnderlyingPerUnripeToken(address unripeToken)
    external
    view
    returns (uint256 underlyingPerToken);
```

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |

| Return Value         | Type      | Description |
|----------------------|-----------|-------------|
| `underlyingPerToken` | `uint256` | WIP         |

### [Get Total Underlying](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L219)

```solidity
function getTotalUnderlying(address unripeToken)
    external
    view
    returns (uint256 underlying);
```

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `underlying` | `uint256` | WIP         |

### [Get Underlying Token](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L238)

```solidity
function getUnderlyingToken(address unripeToken)
    external
    view
    returns (address underlyingToken)
```

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |

| Return Value      | Type      | Description |
|-------------------|-----------|-------------|
| `underlyingToken` | `address` | WIP         |

## Events

### [Add Unripe Token](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L30) <a href="#event-add-unripe-token" id="event-add-unripe-token"></a>

```solidity
event AddUnripeToken(
    address indexed unripeToken,
    address indexed underlyingToken,
    bytes32 merkleRoot
);
```

| Parameter         | Type      | Description |
|-------------------|-----------|-------------|
| `unripeToken`     | `address` | WIP         |
| `underlyingToken` | `address` | WIP         |
| `merkleRoot`      | `bytes32` | WIP         |

### [Change Underlying](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L36) <a href="#event-change-underlying" id="event-change-underlying"></a>

```solidity
event ChangeUnderlying(address indexed token, int256 underlying);
```

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `token`      | `address` | WIP         |
| `underlying` | `int256`  | WIP         |

### [Chop](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L38) <a href="#event-chop" id="event-chop"></a>

```solidity
event Chop(
    address indexed account,
    address indexed token,
    uint256 amount,
    uint256 underlying
);
```

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `account`    | `address` | WIP         |
| `token`      | `address` | WIP         |
| `amount`     | `uint256` | WIP         |
| `underlying` | `uint256` | WIP         |

### [Pick](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L45) <a href="#event-pick" id="event-pick"></a>

```solidity
event Pick(
    address indexed account,
    address indexed token,
    uint256 amount
);
```

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `account`    | `address` | WIP         |
| `token`      | `address` | WIP         |
| `amount`     | `uint256` | WIP         |
