# Pause Facet

Pause Facet handles the pausing/unpausing of Beanstalk.

## Call Functions

### PauseFacet.sol

#### Pause

```solidity
function pause() external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/PauseFacet.sol#L28)

#### Unpause

```solidity
function unpause() external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/PauseFacet.sol#L37)

## View Functions

```
None
```

## Events

### PauseFacet.sol

#### Pause

```solidity
event Pause(uint256 timestamp);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/PauseFacet.sol#L21)

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `timestamp` | `uint256` | WIP         |

#### Unpause

```solidity
event Unpause(uint256 timestamp, uint256 timePassed);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/PauseFacet.sol#L22)

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `timestamp`  | `uint256` | WIP         |
| `timePassed` | `uint256` | WIP         |
