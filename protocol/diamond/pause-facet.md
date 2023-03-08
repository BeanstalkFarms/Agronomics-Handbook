# Pause Facet

Pause Facet handles the pausing/unpausing of Beanstalk.

## Call Functions

### [Pause](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/PauseFacet.sol#L28)

```solidity
function pause() external payable;
```

### [Unpause](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/PauseFacet.sol#L37)

```solidity
function unpause() external payable;
```

## View Functions

```
None
```

## Events

### [Pause](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/PauseFacet.sol#L21) <a href="#event-pause" id="event-pause"></a>

```solidity
event Pause(uint256 timestamp);
```

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `timestamp` | `uint256` | WIP         |

### [Unpause](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/PauseFacet.sol#L22) <a href="#event-unpause" id="event-unpause"></a>

```solidity
event Unpause(uint256 timestamp, uint256 timePassed);
```

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `timestamp`  | `uint256` | WIP         |
| `timePassed` | `uint256` | WIP         |
