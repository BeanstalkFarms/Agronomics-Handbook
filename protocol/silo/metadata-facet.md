# Metadata Facet

The Metadata Facet provides metadata for the ERC-1155 Silo Deposits. Deposit IDs are a `uint256` that is the concatenation of the token address and the Stem.

## Call Functions

None.

## View Functions

### [URI](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/metadata/MetadataFacet.sol#L30)

```solidity
function uri(uint256 depositId) external view returns (string memory);
```

Returns the URI for a given Deposit ID.

| Parameter   | Type      | Description                    |
| ----------- | --------- | ------------------------------ |
| `depositId` | `uint256` | Deposit ID to get the URI for. |

| Return Value | Description                      |
| ------------ | -------------------------------- |
| `string`     | URI of Deposit with `depositId`. |

### [Image URI](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/metadata/MetadataImage.sol#L31)

```solidity
function imageURI(uint256 depositId) public view returns (string memory);
```

Returns the image URI for a given Deposit ID.

| Parameter   | Type      | Description                          |
| ----------- | --------- | ------------------------------------ |
| `depositId` | `uint256` | Deposit ID to get the image URI for. |

| Return Value | Description                            |
| ------------ | -------------------------------------- |
| `string`     | Image URI of Deposit with `depositId`. |

## Events

None.
