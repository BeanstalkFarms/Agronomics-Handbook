# Whitelist Facet

Whitelist Facet handles the whitelisting/dewhitelisting of assets.

## Call Functions

### [Dewhitelist Token](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/WhitelistFacet.sol#L26)

```solidity
function dewhitelistToken(address token) external payable;
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `token`   | `address` | WIP         |

### [Whitelist Token](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/WhitelistFacet.sol#L31)

```solidity
function whitelistToken(
    address token,
    bytes4 selector,
    uint32 stalk,
    uint32 seeds
) external payable;
```

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

### [Whitelist Token](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/WhitelistFacet.sol#L17) <a href="#event-whitelist-token" id="event-whitelist-token"></a>

```solidity
event WhitelistToken(
    address indexed token,
    bytes4 selector,
    uint256 seeds,
    uint256 stalk
);
```

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `token`    | `address` | WIP         |
| `selector` | `bytes4`  | WIP         |
| `seeds`    | `uint256` | WIP         |
| `stalk`    | `uint256` | WIP         |

### [Dewhitelist Token](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/WhitelistFacet.sol#L24) <a href="#event-dewhitelist-token" id="event-dewhitelist-token"></a>

```solidity
event DewhitelistToken(address indexed token);
```

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `token`    | `address` | WIP         |
