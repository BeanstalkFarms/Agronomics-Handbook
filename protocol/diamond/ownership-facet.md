# Ownership Facet

## Call Functions

### [Transfer Ownership](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/OwnershipFacet.sol#L15)

```solidity
function transferOwnership(address _newOwner) external;
```

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `_newOwner` | `address` | WIP         |

### [Claim Ownership](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/OwnershipFacet.sol#L20)

```solidity
function claimOwnership() external;
```

## View Functions

### [Owner](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/OwnershipFacet.sol#L26)

```solidity
function owner() external view returns (address owner_);
```

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `owner_`     | `address` | WIP         |

### [Owner Candidate](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/OwnershipFacet.sol#L30)

```solidity
function ownerCandidate() external view returns (address ownerCandidate_);
```

| Return Value      | Type      | Description |
|-------------------|-----------|-------------|
| `ownerCandidate_` | `address` | WIP         |

## Events

### [Ownership Transferred](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/OwnershipFacet.sol#L13) <a href="#event-ownership-transferred" id="event-ownership-transferred"></a>

```solidity
event OwnershipTransferred(
    address indexed previousOwner, 
    address indexed newOwner
);
```

| Parameter       | Type      | Description |
|-----------------|-----------|-------------|
| `previousOwner` | `address` | WIP         |
| `newOwner`      | `address` | WIP         |
