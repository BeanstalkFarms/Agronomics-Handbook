# Token Support Facet

Permit ERC-20 and ERC-721 tokens and transfer ERC-721 and ERC-1155 tokens.

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
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/TokenSupportFacet.sol#L30)

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

### Transfer ERC-721

```solidity
function transferERC721(
    IERC721 token,
    address to,
    uint256 id
) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/TokenSupportFacet.sol#L53)

Execute an ERC-721 token transfer.

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `token`   | `IERC721` | WIP         |
| `to`      | `address` | WIP         |
| `id`      | `uint256` | WIP         |

### Permit ERC-721

```solidity
function permitERC721(
    IERC4494 token,
    address spender,
    uint256 tokenId,
    uint256 deadline,
    bytes memory sig
) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/TokenSupportFacet.sol#L65)

Execute a permit for an ERC-721 token.

| Parameter  | Type       | Description |
|------------|------------|-------------|
| `token`    | `IERC4494` | WIP         |
| `spender`  | `address`  | WIP         |
| `tokenId`  | `uint256`  | WIP         |
| `deadline` | `uint256`  | WIP         |
| `sig`      | `bytes`    | WIP         |

### ERC-1155

### Transfer ERC-1155

```solidity
function transferERC1155(
    IERC1155 token,
    address to,
    uint256 id,
    uint256 value
) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/TokenSupportFacet.sol#L85)

Execute an ERC-1155 token transfer of a single Id.

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `token`   | `IERC1155` | WIP         |
| `to`      | `address`  | WIP         |
| `id`      | `uint256`  | WIP         |
| `value`   | `uint256`  | WIP         |

### Batch Transfer ERC-1155

```solidity
function batchTransferERC1155(
    IERC1155 token,
    address to,
    uint256[] calldata ids,
    uint256[] calldata values
) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/TokenSupportFacet.sol#L98)

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
