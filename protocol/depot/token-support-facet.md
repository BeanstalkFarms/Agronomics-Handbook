# Token Support Facet

## Call Functions

### ERC-20

```solidity
function permitERC20(
    IERC20Permit token,
    address owner,
    address spender,
    uint256 value,
    uint256 deadline,
    uint8 v,
    bytes32 r,
    bytes32 s
) public payable;
```

permitERC20 is wrapper function for permit of ERC20Permit token.

| Parameter  | Type           | Description |
|------------|----------------|-------------|
| `token`    | `IERC20Permit` | WIP         |
| `owner`    | `address`      | WIP         |
| `spender`  | `address`      | WIP         |
| `value`    | `uint256`      | WIP         |
| `deadline` | `uint256`      | WIP         |
| `v`        | `uint8`        | WIP         |
| `r`        | `bytes32`      | WIP         |
| `s`        | `bytes32`      | WIP         |

### ERC-721

```solidity
function transferERC721(
    IERC721 token,
    address to,
    uint256 id
) external payable;
```

Execute an ERC-721 token transfer.

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `token`   | `IERC721` | WIP         |
| `to`      | `address` | WIP         |
| `id`      | `uint256` | WIP         |

```solidity
function permitERC721(
    IERC4494 token,
    address spender,
    uint256 tokenId,
    uint256 deadline,
    bytes memory sig
) external payable;
```

Execute a permit for an ERC-721 token.

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `token`    | `IERC4494` | WIP         |
| `spender`  | `address`  | WIP         |
| `tokenId`  | `uint256`  | WIP         |
| `deadline` | `uint256`  | WIP         |
| `sig`      | `bytes`    | WIP         |

### ERC-1155

```solidity
function transferERC1155(
    IERC1155 token,
    address to,
    uint256 id,
    uint256 value
) external payable;
```

Execute an ERC-1155 token transfer of a single Id.

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `token`   | `IERC1155` | WIP         |
| `to`      | `address`  | WIP         |
| `id`      | `uint256`  | WIP         |
| `value`   | `uint256`  | WIP         |

```solidity
function batchTransferERC1155(
    IERC1155 token,
    address to,
    uint256[] calldata ids,
    uint256[] calldata values
) external payable;
```

Execute an ERC-1155 token transfer of multiple Ids.

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `token`   | `IERC1155`  | WIP         |
| `to`      | `address`   | WIP         |
| `ids`     | `uint256[]` | WIP         |
| `values`  | `uint256[]` | WIP         |

## View Functions

```
None
```

## Events

```
None
```
