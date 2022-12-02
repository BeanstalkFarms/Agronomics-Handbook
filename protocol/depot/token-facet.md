# Token Facet

## Call Functions

### Approve Token

```solidity
function approveToken(
    address spender,
    IERC20 token,
    uint256 amount
) external payable nonReentrant;
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `spender` | `address` | WIP         |
| `token`   | `IERC20`  | WIP         |
| `amount`  | `uint256` | WIP         |

### Increase Token Allowance

```solidity
function increaseTokenAllowance(
    address spender,
    IERC20 token,
    uint256 addedValue
) public virtual nonReentrant returns (bool);
```

WIP

| Parameter    | Type      | Description |
| ------------ | --------- | ----------- |
| `spender`    | `address` | WIP         |
| `token`      | `IERC20`  | WIP         |
| `addedValue` | `uint256` | WIP         |

### Token Allowance

```solidity
function tokenAllowance(
    address account,
    address spender,
    IERC20 token
) public view virtual returns (uint256);
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `spender` | `address` | WIP         |
| `token`   | `IERC20`  | WIP         |

### Decrease Token Allowance

```solidity
function decreaseTokenAllowance(
    address spender,
    IERC20 token,
    uint256 subtractedValue
) public virtual nonReentrant returns (bool);
```

WIP

| Parameter         | Type      | Description |
| ----------------- | --------- | ----------- |
| `spender`         | `address` | WIP         |
| `token`           | `IERC20`  | WIP         |
| `subtractedValue` | `uint256` | WIP         |

### Permit Token

```solidity
function permitToken(
    address owner,
    address spender,
    address token,
    uint256 value,
    uint256 deadline,
    uint8 v,
    bytes32 r,
    bytes32 s
) external payable nonReentrant;
```

WIP

| Parameter  | Type      | Description |
| ---------- | --------- | ----------- |
| `owner`    | `address` | WIP         |
| `spender`  | `address` | WIP         |
| `token`    | `address` | WIP         |
| `value`    | `uint256` | WIP         |
| `deadline` | `uint256` | WIP         |
| `v`        | `uint8`   | WIP         |
| `r`        | `bytes32` | WIP         |
| `s`        | `bytes32` | WIP         |

### Transfer Token

```solidity
function transferToken(
    IERC20 token,
    address recipient,
    uint256 amount,
    LibTransfer.From fromMode,
    LibTransfer.To toMode
) external payable;
```

Transfers an asset from a Farmer's Internal and/or External Balance to a Farmer's Internal or External Balance.

| Parameter   | Type      | Description                                                                                                       |
| ----------- | --------- | ----------------------------------------------------------------------------------------------------------------- |
| `token`     | `IERC20`  | The token to be transferred.                                                                                      |
| `recipient` | `address` | The recipient of the transferred tokens (can be `msg.sender`).                                                    |
| `amount`    | `uint256` | The amount of tokens to be transferred.                                                                           |
| `fromMode`  | `From`    | Specifies what balance to receive the tokens from (see [Internal Balances](../../overview/internal-balances.md)). |
| `toMode`    | `To`      | Specifies what balance to send the tokens to (see [Internal Balances](../../overview/internal-balances.md)).      |

### Transfer Internal Token From

```solidity
function transferInternalTokenFrom(
    IERC20 token,
    address sender,
    address recipient,
    uint256 amount,
    LibTransfer.To toMode
) external payable nonReentrant;
```

WIP

| Parameter   | Type      | Description |
| ----------- | --------- | ----------- |
| `token`     | `IERC20`  | WIP         |
| `sender`    | `address` | WIP         |
| `recipient` | `address` | WIP         |
| `amount`    | `uint256` | WIP         |
| `toMode`    | `To`      | WIP         |

### Wrap Ether

```solidity
function wrapEth(uint256 amount, LibTransfer.To mode) external payable;
```

Wraps Ether into WETH.

| Parameter | Type      | Description                                                                                                |
| --------- | --------- | ---------------------------------------------------------------------------------------------------------- |
| `amount`  | `uint256` | The amount of Ether to wrap into WETH. Must be `<= msg.value`.                                             |
| `toMode`  | `To`      | Specifies what balance to send the WETH to (see [Internal Balances](../../overview/internal-balances.md)). |

### Unwrap Ether

```solidity
function unwrapEth(uint256 amount, LibTransfer.From mode) external payable;
```

Unwraps WETH into Ether.

| Parameter  | Type      | Description                                                                                                     |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------------- |
| `amount`   | `uint256` | The amount of WETH to unwrap into Ether.                                                                        |
| `fromMode` | `From`    | Specifies what balance to receive the WETH from (see [Internal Balances](../../overview/internal-balances.md)). |

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
    returns (Balance[] memory balances);
    
function tokenPermitNonces(address owner)
    public
    view
    virtual
    returns (uint256);
    
function tokenPermitDomainSeparator() external view returns (bytes32);
```

## Events

```solidity
event InternalBalanceChanged(
    address indexed account,
    IERC20 indexed token,
    int256 delta
);

event TokenApproval(
    address indexed owner,
    address indexed spender,
    IERC20 token,
    uint256 amount
);
```
