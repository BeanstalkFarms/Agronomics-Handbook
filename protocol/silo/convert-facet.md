# Convert Facet

## Call Functions

### Convert

```solidity
function convert(
    bytes calldata convertData,
    uint32[] memory crates,
    uint256[] memory amounts
) external payable nonReentrant returns (
    uint32 toSeason, 
    uint256 fromAmount, 
    uint256 toAmount, 
    uint256 fromBdv, 
    uint256 toBdv
);
```

| Parameter     | Type        | Description |
|---------------|-------------|-------------|
| `convertData` | `bytes`     | WIP         |
| `crates`      | `uint32[]`  | WIP         |
| `amounts`     | `uint256[]` | WIP         |

## View Functions

```solidity
function getMaxAmountIn(
    address tokenIn,
    address tokenOut
) external view returns (uint256 amountIn);
        
function getAmountOut(
    address tokenIn,
    address tokenOut,
    uint256 amountIn
) external view returns (uint256 amountOut);
```

## Events

```solidity
event Convert(
    address indexed account,
    address fromToken,
    address toToken,
    uint256 fromAmount,
    uint256 toAmount
);

event RemoveDeposits(
    address indexed account,
    address indexed token,
    uint32[] seasons,
    uint256[] amounts,
    uint256 amount
);
```
