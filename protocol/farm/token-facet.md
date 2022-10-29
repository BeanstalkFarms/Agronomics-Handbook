# Token Facet

## Call Functions

### Transfer Tokens

```solidity
function transferToken(
    IERC20 token,
    address recipient,
    uint256 amount,
    LibTransfer.From fromMode,
    LibTransfer.To toMode
) external payable;
```

`transferToken()` transfers an asset from a Farmer's Internal and/or External Balance to a Farmer's Internal or External Balance.

| Parameter   | Type      | Description                                                                                                       |
| ----------- | --------- | ----------------------------------------------------------------------------------------------------------------- |
| `token`     | `IERC20`  | The token to be transferred.                                                                                      |
| `recipient` | `address` | The recipient of the transferred tokens (can be `msg.sender`).                                                    |
| `amount`    | `uint256` | The amount of tokens to be transferred.                                                                           |
| `fromMode`  | `From`    | Specifies what balance to receive the tokens from (see [Internal Balances](../../overview/internal-balances.md)). |
| `toMode`    | `To`      | Specifies what balance to send the tokens to (see [Internal Balances](../../overview/internal-balances.md)).      |

### Wrap Ether

`wrapEth()` wraps Ether into WETH.

```solidity
function wrapEth(uint256 amount, LibTransfer.To mode) external payable;
```

| Parameter | Type      | Description                                                                                                |
| --------- | --------- | ---------------------------------------------------------------------------------------------------------- |
| `amount`  | `uint256` | The amount of Ether to wrap into WETH. Must be `<= msg.value`.                                             |
| `toMode`  | `To`      | Specifies what balance to send the WETH to (see [Internal Balances](../../overview/internal-balances.md)). |

### Unwrap Ether

`unwrapEth()` unwraps WETH into Ether.

```solidity
function unwrapEth(uint256 amount, LibTransfer.From mode) external payable;
```

| Parameter  | Type      | Description                                                                                                      |
| ---------- | --------- | ---------------------------------------------------------------------------------------------------------------- |
| `amount`   | `uint256` | The amount of WETH to unwrap into Ether.                                                                         |
| `fromMode` | `From`    | Specifies what balance to receive  the WETH from (see [Internal Balances](../../overview/internal-balances.md)). |

## View Functions

```solidity
function getInternalBalance(address account, IERC20 token)
    public
    view
    returns (uint256 balance);

function getInternalBalances(address account, IERC20[] memory tokens)
    external
    view
    returns (uint256[] memory balances);
        
function getExternalBalance(address account, IERC20 token)
    public
    view
    returns (uint256 balance);
        
function getExternalBalances(address account, IERC20[] memory tokens)
    external
    view
    returns (uint256[] memory balances);

function getBalance(address account, IERC20 token)
    public
    view
    returns (uint256 balance);
        
function getBalances(address account, IERC20[] memory tokens)
    external
    view
    returns (uint256[] memory balances);
        
function getAllBalance(address account, IERC20 token)
    public
    view
    returns (Balance memory b);
        
function getAllBalances(address account, IERC20[] memory tokens)
    external
    view
    returns (Balance[] memory balance;
```

## Events

```solidity
event InternalBalanceChanged(
    address indexed account,
    IERC20 indexed token,
    int256 delta
);
```
