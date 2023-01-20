# Ownership Facet

## Call Functions

### Transfer Ownership

```solidity
function transferOwnership(address _newOwner) external;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/OwnershipFacet.sol#L15)

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `_newOwner` | `address` | WIP         |

### Claim Ownership

```solidity
function claimOwnership() external;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/OwnershipFacet.sol#L20)

## View Functions

### Owner

```solidity
function owner() external view returns (address owner_);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/OwnershipFacet.sol#L26)

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `owner_`     | `address` | WIP         |

### Owner Candidate

```solidity
function ownerCandidate() external view returns (address ownerCandidate_);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/OwnershipFacet.sol#L30)

| Return Value      | Type      | Description |
|-------------------|-----------|-------------|
| `ownerCandidate_` | `address` | WIP         |

## Events

### Ownership Transferred

```solidity
event OwnershipTransferred(
    address indexed previousOwner, 
    address indexed newOwner
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/OwnershipFacet.sol#L13)

| Parameter       | Type      | Description |
|-----------------|-----------|-------------|
| `previousOwner` | `address` | WIP         |
| `newOwner`      | `address` | WIP         |
