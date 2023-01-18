# Unripe Facet

Manage the logic of the vesting process for the Barnraised Funds.

## Call Functions

### Chop

```solidity
function chop(
    address unripeToken,
    uint256 amount,
    LibTransfer.From fromMode,
    LibTransfer.To toMode
) external payable nonReentrant returns (uint256 underlyingAmount);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L51)

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |
| `amount`      | `uint256` | WIP         |
| `fromMode`    | `From`    | WIP         |
| `toMode`      | `To`      | WIP         |

| Return Value       | Type      | Description |
|--------------------|-----------|-------------|
| `underlyingAmount` | `uint256` | WIP         |

### Pick

```solidity
function pick(
    address token,
    uint256 amount,
    bytes32[] memory proof,
    LibTransfer.To mode
) external payable nonReentrant;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L72)

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `token`   | `address`   | WIP         |
| `amount`  | `uint256`   | WIP         |
| `proof`   | `bytes32[]` | WIP         |
| `mode`    | `To`        | WIP         |

### Add Unripe Token

```solidity
function addUnripeToken(
    address unripeToken,
    address underlyingToken,
    bytes32 root
) external payable nonReentrant;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L227)

| Parameter         | Type      | Description |
|-------------------|-----------|-------------|
| `unripeToken`     | `address` | WIP         |
| `underlyingToken` | `address` | WIP         |
| `root`            | `bytes32` | WIP         |

## View Functions

```solidity
function picked(address account, address token)
    public
    view
    returns (bool);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L97)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `bool`       | WIP         |

```solidity
function getUnderlying(address unripeToken, uint256 amount)
    public
    view
    returns (uint256 redeem);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L105)

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |
| `amount`      | `uint256` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `redeem`     | `uint256` | WIP         |

```solidity
function getPenalty(address unripeToken)
    external
    view
    returns (uint256 penalty);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L123)

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `penalty`    | `uint256` | WIP         |

```solidity
function getPenalizedUnderlying(address unripeToken, uint256 amount)
    public
    view
    returns (uint256 redeem);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L131)

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |
| `amount`      | `uint256` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `redeem`     | `uint256` | WIP         |

```solidity
function _getPenalizedUnderlying(address unripeToken, uint256 amount, uint256 supply)
    public
    view
    returns (uint256 redeem);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L139)

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |
| `amount`      | `uint256` | WIP         |
| `supply`      | `uint256` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `redeem`     | `uint256` | WIP         |

```solidity
function isUnripe(address unripeToken) public view returns (bool unripe);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L149)

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |

| Return Value | Type   | Description |
|--------------|--------|-------------|
| `unripe`     | `bool` | WIP         |

```solidity
function balanceOfUnderlying(address unripeToken, address account)
    external
    view
    returns (uint256 underlying);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L153)

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |
| `account`     | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `underlying` | `uint256` | WIP         |

```solidity
function balanceOfPenalizedUnderlying(address unripeToken, address account)
    external
    view
    returns (uint256 underlying);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L162)

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |
| `account`     | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `underlying` | `uint256` | WIP         |

```solidity
function getRecapFundedPercent(address unripeToken)
    public
    view
    returns (uint256 percent);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L174)

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `percent`    | `uint256` | WIP         |

```solidity
function getPercentPenalty(address unripeToken)
    external
    view
    returns (uint256 penalty);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L187)

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `penalty`    | `uint256` | WIP         |

```solidity
function getRecapPaidPercent() external view returns (uint256 penalty);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L195)

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `penalty`    | `uint256` | WIP         |

```solidity
function getRecapPaidPercentAmount(uint256 amount)
    private
    view
    returns (uint256 penalty);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L199)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `amount`  | `uint256` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `penalty`    | `uint256` | WIP         |

```solidity
function getUnderlyingPerUnripeToken(address unripeToken)
    external
    view
    returns (uint256 underlyingPerToken);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L207)

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |

| Return Value         | Type      | Description |
|----------------------|-----------|-------------|
| `underlyingPerToken` | `uint256` | WIP         |

```solidity
function getTotalUnderlying(address unripeToken)
    external
    view
    returns (uint256 underlying);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L219)

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `underlying` | `uint256` | WIP         |

```solidity
function getUnderlyingToken(address unripeToken)
    external
    view
    returns (address underlyingToken)
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L238)

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `unripeToken` | `address` | WIP         |

| Return Value      | Type      | Description |
|-------------------|-----------|-------------|
| `underlyingToken` | `address` | WIP         |

## Events

```solidity
event AddUnripeToken(
    address indexed unripeToken,
    address indexed underlyingToken,
    bytes32 merkleRoot
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L30)

| Parameter         | Type      | Description |
|-------------------|-----------|-------------|
| `unripeToken`     | `address` | WIP         |
| `underlyingToken` | `address` | WIP         |
| `merkleRoot`      | `bytes32` | WIP         |

```solidity
event ChangeUnderlying(address indexed token, int256 underlying);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L36)

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `token`      | `address` | WIP         |
| `underlying` | `int256`  | WIP         |

```solidity
event Chop(
    address indexed account,
    address indexed token,
    uint256 amount,
    uint256 underlying
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L38)

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `account`    | `address` | WIP         |
| `token`      | `address` | WIP         |
| `amount`     | `uint256` | WIP         |
| `underlying` | `uint256` | WIP         |

```solidity
event Pick(
    address indexed account,
    address indexed token,
    uint256 amount
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/9ca85613d40a3883377de0d9377623d49fff5b9c/protocol/contracts/farm/facets/UnripeFacet.sol#L45)

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `account`    | `address` | WIP         |
| `token`      | `address` | WIP         |
| `amount`     | `uint256` | WIP         |
