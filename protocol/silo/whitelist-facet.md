# Whitelist Facet

## Call Functions

```solidity
function dewhitelistToken(address token) external payable;
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `token`   | `address` | WIP         |

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

```solidity
event WhitelistToken(
    address indexed token,
    bytes4 selector,
    uint256 seeds,
    uint256 stalk
);

event DewhitelistToken(address indexed token);
```
