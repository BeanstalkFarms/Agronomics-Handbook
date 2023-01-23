# Whitelist Facet

Whitelist Facet handles the whitelisting/dewhitelisting of assets.

## Call Functions

### WhitelistFacet.sol

#### Dewhitelist Token

```solidity
function dewhitelistToken(address token) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/WhitelistFacet.sol#L26)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `token`   | `address` | WIP         |

#### Whitelist Token

```solidity
function whitelistToken(
    address token,
    bytes4 selector,
    uint32 stalk,
    uint32 seeds
) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/WhitelistFacet.sol#L31)

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `token`    | `address` | WIP         |
| `selector` | `bytes4`  | WIP         |
| `stalk`    | `uint32`  | WIP         |
| `seeds`    | `uint32`  | WIP         |

## View Functions

```solidity
None
```

## Events

### WhitelistFacet.sol

#### Whitelist Token

```solidity
event WhitelistToken(
    address indexed token,
    bytes4 selector,
    uint256 seeds,
    uint256 stalk
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/WhitelistFacet.sol#L17)

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `token`    | `address` | WIP         |
| `selector` | `bytes4`  | WIP         |
| `seeds`    | `uint256` | WIP         |
| `stalk`    | `uint256` | WIP         |

#### Dewhitelist Token

```solidity
event DewhitelistToken(address indexed token);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/WhitelistFacet.sol#L24)

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `token`    | `address` | WIP         |
