# Depot Facet

## Call Functions

### Depot

```solidity
function pipe(PipeCall calldata p)
    external
    payable
    returns (bytes memory result);
```

Pipe a PipeCall through Pipeline.

| Parameter | Type       | Description                        |
|-----------|------------|------------------------------------|
| `p`       | `PipeCall` | PipeCall to pipe through Pipeline. |

| Return Value | Type    | Description            |
|--------------|---------|------------------------|
| `result`     | `bytes` | PipeCall return value. |

```solidity
function multiPipe(PipeCall[] calldata pipes)
    external
    payable
    returns (bytes[] memory results);
```

Pipe multiple PipeCalls through Pipeline. Does not support sending Ether in the call.

| Parameter | Type         | Description                                 |
|-----------|--------------|---------------------------------------------|
| `pipes`   | `PipeCall[]` | List of PipeCalls to pipe through Pipeline. |

| Return Value | Type      | Description                               |
|--------------|-----------|-------------------------------------------|
| `results`    | `bytes[]` | List of return values from each PipeCall. |

```solidity
function advancedPipe(AdvancedPipeCall[] calldata pipes, uint256 value)
    external
    payable
    returns (bytes[] memory results);
```

Pipe multiple AdvancedPipeCalls through Pipeline.

| Parameter | Type                 | Description                                         |
|-----------|----------------------|-----------------------------------------------------|
| `pipes`   | `AdvancedPipeCall[]` | List of AdvancedPipeCalls to pipe through Pipeline. |
| `value`   | `uint256`            |                                                     |

| Return Value | Type      | Description                                       |
|--------------|-----------|---------------------------------------------------|
| `results`    | `bytes[]` | List of return values from each AdvancedPipeCall. |

```solidity
function etherPipe(PipeCall calldata p, uint256 value)
    external
    payable
    returns (bytes memory result);
```

Pipe a PipeCall through Pipeline with an Ether value.

| Parameter | Type       | Description                        |
|-----------|------------|------------------------------------|
| `p`       | `PipeCall` | PipeCall to pipe through Pipeline. |
| `value`   | `uint256`  | Ether value to send in Pipecall.   |

| Return Value | Type    | Description            |
|--------------|---------|------------------------|
| `result`     | `bytes` | PipeCall return value. |

```solidity
function readPipe(PipeCall calldata p)
    external
    view
    returns (bytes memory result);
```

Return the return value of a PipeCall without executing it.

| Parameter | Type       | Description                            |
|-----------|------------|----------------------------------------|
| `p`       | `PipeCall` | PipeCall to execute with a staticcall. |

| Return Value | Type    | Description            |
|--------------|---------|------------------------|
| `result`     | `bytes` | PipeCall return value. |

## View Functions

```
None
```

## Events

```
None
```

