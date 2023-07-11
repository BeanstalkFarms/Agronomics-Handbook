# Token Support Facet

The Token Support Facet handles permits for ERC-20 and ERC-721 tokens and transfers for ERC-721 and ERC-1155 tokens.

## Call Functions

### [Permit ERC-20](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/TokenSupportFacet.sol#L30)

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

`permitERC20` is a wrapper function for permit of [ERC20Permit](https://docs.openzeppelin.com/contracts/4.x/api/token/erc20#ERC20Permit-permit-address-address-uint256-uint256-uint8-bytes32-bytes32-) token.

| Parameter  | Type           | Description                           |
| ---------- | -------------- | ------------------------------------- |
| `token`    | `IERC20Permit` | Token to permit.                      |
| `owner`    | `address`      | Owner of the token.                   |
| `spender`  | `address`      | Address to permit to spend the token. |
| `value`    | `uint256`      | Token amount to permit.               |
| `deadline` | `uint256`      | Expiration of signature (Unix time)   |
| `v`        | `uint8`        | Recovery ID.                          |
| `r`        | `bytes32`      | ECDSA signature output.               |
| `s`        | `bytes32`      | ECDSA signature output.               |

### [Transfer ERC-721](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/TokenSupportFacet.sol#L53)

```solidity
function transferERC721(
    IERC721 token,
    address to,
    uint256 id
) external payable;
```

Execute an ERC-721 token transfer.

| Parameter | Type      | Description                      |
| --------- | --------- | -------------------------------- |
| `token`   | `IERC721` | Token address of the ERC-721.    |
| `to`      | `address` | Address being transferred to.    |
| `id`      | `uint256` | ID of ERC-721 token to transfer. |

### [Permit ERC-721](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/TokenSupportFacet.sol#L65)

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

| Parameter  | Type       | Description                                                                                                       |
| ---------- | ---------- | ----------------------------------------------------------------------------------------------------------------- |
| `token`    | `IERC4494` | Token address to permit.                                                                                          |
| `spender`  | `address`  | Address to permit to spend the token.                                                                             |
| `tokenId`  | `uint256`  | ID of `token` to permit.                                                                                          |
| `deadline` | `uint256`  | Expiration of signature (Unix time).                                                                              |
| `sig`      | `bytes`    | A valid `secp256k1` or [EIP-2098](https://eips.ethereum.org/EIPS/eip-2098) signature from owner of the `tokenId`. |

### [Transfer ERC-1155](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/TokenSupportFacet.sol#L85)

```solidity
function transferERC1155(
    IERC1155 token,
    address to,
    uint256 id,
    uint256 value
) external payable;
```

Execute an ERC-1155 token transfer of a single ID.

| Parameter | Type       | Description                                        |
| --------- | ---------- | -------------------------------------------------- |
| `token`   | `IERC1155` | Token address of the ERC-1155.                     |
| `to`      | `address`  | Address being transferred to.                      |
| `id`      | `uint256`  | ID of the ERC-1155 token.                          |
| `value`   | `uint256`  | Number of the ERC-1155 tokens at `id` to transfer. |

### [Batch Transfer ERC-1155](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/TokenSupportFacet.sol#L98)

```solidity
function batchTransferERC1155(
    IERC1155 token,
    address to,
    uint256[] calldata ids,
    uint256[] calldata values
) external payable;
```

Execute an ERC-1155 token transfer of multiple IDs.

| Parameter | Type        | Description                                        |
| --------- | ----------- | -------------------------------------------------- |
| `token`   | `IERC1155`  | Token address of the ERC-1155.                     |
| `to`      | `address`   | Address being transferred to.                      |
| `ids`     | `uint256[]` | Array of IDs of the ERC-155 token.                 |
| `values`  | `uint256[]` | Array of amounts of ERC-1155s at `id` to transfer. |

## View Functions

None.

## Events

None.
