# Metadata Facet

{% hint style="warning" %}
Note that this page has not been updated to reflect the current state of Beanstalk, but is left here as a reference.
{% endhint %}

The Metadata Facet provides metadata for the ERC-1155 Silo Deposits. Deposit IDs are a `uint256` that is the concatenation of the token address and the Stem.

## Call Functions

None.

## View Functions

### [URI](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/metadata/MetadataFacet.sol#L34)

```solidity
function uri(uint256 depositId) external view returns (string memory);
```

Returns the URI for a given Deposit ID.

| Parameter   | Type      | Description                    |
| ----------- | --------- | ------------------------------ |
| `depositId` | `uint256` | Deposit ID to get the URI for. |

| Return Type | Description                      |
| ----------- | -------------------------------- |
| `string`    | URI of Deposit with `depositId`. |

### [Name](https://github.com/BeanstalkFarms/Beanstalk/blob/893c99d21a2d87c96280f66601a6db8900e5b7d1/protocol/contracts/beanstalk/metadata/MetadataFacet.sol#L58)

```solidity
function name() external pure returns (string memory);
```

Returns the name of the collection for OpenSea compatibility.

| Return Type | Description                     |
| ----------- | ------------------------------- |
| `string`    | Name of the OpenSea collection. |

### [Symbol](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/metadata/MetadataFacet.sol#L62)

```solidity
function symbol() external pure returns (string memory);
```

Returns the ticker of the collection for OpenSea compatibility.

| Return Type | Description                       |
| ----------- | --------------------------------- |
| `string`    | Ticker of the OpenSea collection. |

### [Image URI](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/metadata/MetadataImage.sol#L30)

```solidity
function imageURI(uint256 depositId) public view returns (string memory);
```

Returns the image URI for a given Deposit ID.

| Parameter   | Type      | Description                          |
| ----------- | --------- | ------------------------------------ |
| `depositId` | `uint256` | Deposit ID to get the image URI for. |

| Return Type | Description                            |
| ----------- | -------------------------------------- |
| `string`    | Image URI of Deposit with `depositId`. |

## Events

### [URI](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/metadata/MetadataFacet.sol#L25C5-L25C49)

```solidity
event URI(string _uri, uint256 indexed _id);
```

Not currently emitted.

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `_uri`    | `string`  | URI.        |
| `_id`     | `uint256` | Deposit ID. |
