# Pause Facet

{% hint style="warning" %}
Note that this page has not been updated to reflect the current state of Beanstalk, but is left here as a reference.
{% endhint %}

The Pause Facet handles the Pausing and Unpausing of Beanstalk.

## Call Functions

### [Pause](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/PauseFacet.sol#L28)

```solidity
function pause() external payable;
```

Pause Beanstalk, which makes it such that the `gm` function cannot be successfully called. Only callable by the owner of Beanstalk.

### [Unpause](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/PauseFacet.sol#L37)

```solidity
function unpause() external payable;
```

Unpause Beanstalk, which allows the `gm` function to be successfully called at the top of the 2nd hour. The TWAP oracle and Season timer are reset as well.

## View Functions

None.

## Events

### [Pause](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/PauseFacet.sol#L21) <a href="#event-pause" id="event-pause"></a>

```solidity
event Pause(uint256 timestamp);
```

Emitted when Beanstalk is Paused.

| Parameter   | Type      | Description                                              |
| ----------- | --------- | -------------------------------------------------------- |
| `timestamp` | `uint256` | Timestamp of the current block when Beanstalk is Paused. |

### [Unpause](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/PauseFacet.sol#L22) <a href="#event-unpause" id="event-unpause"></a>

```solidity
event Unpause(uint256 timestamp, uint256 timePassed);
```

Emitted when Beanstalk is Unpaused.

| Parameter    | Type      | Description                                                |
| ------------ | --------- | ---------------------------------------------------------- |
| `timestamp`  | `uint256` | Timestamp of the current block when Beanstalk is Unpaused. |
| `timePassed` | `uint256` | How much time passed while Beanstalk was Paused.           |
