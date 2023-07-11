# Ownership Facet

The Ownership Facet handles the ownership of Beanstalk.

## Call Functions

### [Transfer Ownership](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/OwnershipFacet.sol#L15)

```solidity
function transferOwnership(address _newOwner) external;
```

Transfers ownership of Beanstalk to a new address. Can only be called by the owner of Beanstalk.

| Parameter   | Type      | Description                           |
| ----------- | --------- | ------------------------------------- |
| `_newOwner` | `address` | The address to transfer ownership to. |

### [Claim Ownership](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/OwnershipFacet.sol#L20)

```solidity
function claimOwnership() external;
```

Callable by candidate for ownership after a successful `transferOwnership` function call.

## View Functions

### [Owner](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/OwnershipFacet.sol#L26)

```solidity
function owner() external view returns (address owner_);
```

Returns the address of the owner of Beanstalk.

| Return Value | Type      | Description                            |
| ------------ | --------- | -------------------------------------- |
| `owner_`     | `address` | The address of the owner of Beanstalk. |

### [Owner Candidate](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/OwnershipFacet.sol#L30)

```solidity
function ownerCandidate() external view returns (address ownerCandidate_);
```

Returns the owner candidate of Beanstalk.

| Return Value      | Type      | Description                       |
| ----------------- | --------- | --------------------------------- |
| `ownerCandidate_` | `address` | The owner candidate of Beanstalk. |

## Events

### [Ownership Transferred](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/OwnershipFacet.sol#L13) <a href="#event-ownership-transferred" id="event-ownership-transferred"></a>

```solidity
event OwnershipTransferred(
    address indexed previousOwner, 
    address indexed newOwner
);
```

Emitted when ownership of Beanstalk is transferred.

| Parameter       | Type      | Description                      |
| --------------- | --------- | -------------------------------- |
| `previousOwner` | `address` | The previous owner of Beanstalk. |
| `newOwner`      | `address` | The new owner of Beanstalk.      |
