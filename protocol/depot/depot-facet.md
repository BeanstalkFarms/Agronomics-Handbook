# Depot Facet

The Depot Facet wraps Pipeline's `pipe` functions to facilitate the loading of non-Ether assets in [Pipeline](https://evmpipeline.org/).

## Call Functions

### [Pipe](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/DepotFacet.sol#L30)

```solidity
function pipe(PipeCall calldata p)
    external
    payable
    returns (bytes memory result);
```

Pipe a `PipeCall` through Pipeline.

| Parameter | Type       | Description                          |
| --------- | ---------- | ------------------------------------ |
| `p`       | `PipeCall` | `PipeCall` to pipe through Pipeline. |

| Return Value | Type    | Description              |
| ------------ | ------- | ------------------------ |
| `result`     | `bytes` | `PipeCall` return value. |

### [Multi Pipe](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/DepotFacet.sol#L44)

```solidity
function multiPipe(PipeCall[] calldata pipes)
    external
    payable
    returns (bytes[] memory results);
```

Pipe multiple `PipeCalls` through Pipeline. Does not support sending Ether in the call.

| Parameter | Type         | Description                                   |
| --------- | ------------ | --------------------------------------------- |
| `pipes`   | `PipeCall[]` | List of `PipeCalls` to pipe through Pipeline. |

| Return Value | Type      | Description                                 |
| ------------ | --------- | ------------------------------------------- |
| `results`    | `bytes[]` | List of return values from each `PipeCall`. |

### [Advanced Pipe](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/DepotFacet.sol#L57)

```solidity
function advancedPipe(AdvancedPipeCall[] calldata pipes, uint256 value)
    external
    payable
    returns (bytes[] memory results);
```

Pipe multiple `AdvancedPipeCalls` through Pipeline.

| Parameter | Type                 | Description                                           |
| --------- | -------------------- | ----------------------------------------------------- |
| `pipes`   | `AdvancedPipeCall[]` | List of `AdvancedPipeCalls` to pipe through Pipeline. |
| `value`   | `uint256`            |                                                       |

| Return Value | Type      | Description                                         |
| ------------ | --------- | --------------------------------------------------- |
| `results`    | `bytes[]` | List of return values from each `AdvancedPipeCall`. |

### [Ether Pipe](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/DepotFacet.sol#L72)

```solidity
function etherPipe(PipeCall calldata p, uint256 value)
    external
    payable
    returns (bytes memory result);
```

Pipe a `PipeCall` through Pipeline with an Ether value.

| Parameter | Type       | Description                          |
| --------- | ---------- | ------------------------------------ |
| `p`       | `PipeCall` | `PipeCall` to pipe through Pipeline. |
| `value`   | `uint256`  | Ether value to send in `Pipecall`.   |

| Return Value | Type    | Description              |
| ------------ | ------- | ------------------------ |
| `result`     | `bytes` | `PipeCall` return value. |

## View Functions

### [Read Pipe](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/DepotFacet.sol#L86)

```solidity
function readPipe(PipeCall calldata p)
    external
    view
    returns (bytes memory result);
```

Return the return value of a `PipeCall` without executing it.

| Parameter | Type       | Description                              |
| --------- | ---------- | ---------------------------------------- |
| `p`       | `PipeCall` | `PipeCall` to execute with a staticcall. |

| Return Value | Type    | Description              |
| ------------ | ------- | ------------------------ |
| `result`     | `bytes` | `PipeCall` return value. |

## Events

None.
