# Ownership Facet

## Call Functions

```solidity
function transferOwnership(address _newOwner) external;

function claimOwnership() external;
```

## View Functions

```solidity
function owner() external view returns (address owner_);

function ownerCandidate() external view returns (address ownerCandidate_);
```

## Events

```solidity
event OwnershipTransferred(
    address indexed previousOwner, 
    address indexed newOwner
);
```
