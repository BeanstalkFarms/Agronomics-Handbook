# Token Facet

{% hint style="warning" %}
Note that this page has not been updated to reflect the current state of Beanstalk, but is left here as a reference.
{% endhint %}

The Token Facet handles the transfers of assets outside the Silo.

## Call Functions

### Transfers

### [Transfer Token](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L56)

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

### [Transfer Internal Token From](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L77)

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

### Approvals

### [Approve Token](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L104)

```solidity
function approveToken(
    address spender,
    IERC20 token,
    uint256 amount
) external payable nonReentrant;
```

Wraps Ether into WETH.

| Parameter | Type      | Description                                                                                                |
| --------- | --------- | ---------------------------------------------------------------------------------------------------------- |
| `amount`  | `uint256` | The amount of Ether to wrap into WETH. Must be `<= msg.value`.                                             |
| `toMode`  | `To`      | Specifies what balance to send the WETH to (see [Internal Balances](../../overview/internal-balances.md)). |

### [Increase Token Allowance](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L115)

```solidity
function increaseTokenAllowance(
    address spender,
    IERC20 token,
    uint256 addedValue
) public virtual nonReentrant returns (bool);
```

Wraps Ether into WETH.

| Parameter | Type      | Description                                                                                                |
| --------- | --------- | ---------------------------------------------------------------------------------------------------------- |
| `amount`  | `uint256` | The amount of Ether to wrap into WETH. Must be `<= msg.value`.                                             |
| `toMode`  | `To`      | Specifies what balance to send the WETH to (see [Internal Balances](../../overview/internal-balances.md)). |

### [Decrease Token Allowance](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L133)

```solidity
function decreaseTokenAllowance(
    address spender,
    IERC20 token,
    uint256 subtractedValue
) public virtual nonReentrant returns (bool);
```

Wraps Ether into WETH.

| Parameter | Type      | Description                                                                                                |
| --------- | --------- | ---------------------------------------------------------------------------------------------------------- |
| `amount`  | `uint256` | The amount of Ether to wrap into WETH. Must be `<= msg.value`.                                             |
| `toMode`  | `To`      | Specifies what balance to send the WETH to (see [Internal Balances](../../overview/internal-balances.md)). |

### [Token Allowance](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L159)

```solidity
function tokenAllowance(
    address account,
    address spender,
    IERC20 token
) public view virtual returns (uint256);
```

Wraps Ether into WETH.

| Parameter | Type      | Description                                                                                                |
| --------- | --------- | ---------------------------------------------------------------------------------------------------------- |
| `amount`  | `uint256` | The amount of Ether to wrap into WETH. Must be `<= msg.value`.                                             |
| `toMode`  | `To`      | Specifies what balance to send the WETH to (see [Internal Balances](../../overview/internal-balances.md)). |

### Permits

### [Permit Token](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L172)

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

Wraps Ether into WETH.

| Parameter | Type      | Description                                                                                                |
| --------- | --------- | ---------------------------------------------------------------------------------------------------------- |
| `amount`  | `uint256` | The amount of Ether to wrap into WETH. Must be `<= msg.value`.                                             |
| `toMode`  | `To`      | Specifies what balance to send the WETH to (see [Internal Balances](../../overview/internal-balances.md)). |

### [Token Permit Nonces](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L189)

```solidity
function tokenPermitNonces(address owner)
    public
    view
    virtual
    returns (uint256);
```

Wraps Ether into WETH.

| Parameter | Type      | Description                                                                                                |
| --------- | --------- | ---------------------------------------------------------------------------------------------------------- |
| `amount`  | `uint256` | The amount of Ether to wrap into WETH. Must be `<= msg.value`.                                             |
| `toMode`  | `To`      | Specifies what balance to send the WETH to (see [Internal Balances](../../overview/internal-balances.md)). |

### [Token Permit Domain Separator](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L236)

```solidity
function tokenPermitDomainSeparator() external view returns (bytes32);
```

Wraps Ether into WETH.

| Parameter | Type      | Description                                                                                                |
| --------- | --------- | ---------------------------------------------------------------------------------------------------------- |
| `amount`  | `uint256` | The amount of Ether to wrap into WETH. Must be `<= msg.value`.                                             |
| `toMode`  | `To`      | Specifies what balance to send the WETH to (see [Internal Balances](../../overview/internal-balances.md)). |

### ERC-1155

### [On ERC-1155 Received](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L206)

```solidity
function onERC1155Received(
    address,
    address,
    uint256,
    uint256,
    bytes calldata
) external pure override returns (bytes4);
```

Wraps Ether into WETH.

| Parameter | Type      | Description                                                                                                |
| --------- | --------- | ---------------------------------------------------------------------------------------------------------- |
| `amount`  | `uint256` | The amount of Ether to wrap into WETH. Must be `<= msg.value`.                                             |
| `toMode`  | `To`      | Specifies what balance to send the WETH to (see [Internal Balances](../../overview/internal-balances.md)). |

### [On ERC-1155 Batch Received](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L222)

```solidity
function onERC1155BatchReceived(
    address,
    address,
    uint256[] calldata,
    uint256[] calldata,
    bytes calldata
) external pure override returns (bytes4);
```

Wraps Ether into WETH.

| Parameter | Type      | Description                                                                                                |
| --------- | --------- | ---------------------------------------------------------------------------------------------------------- |
| `amount`  | `uint256` | The amount of Ether to wrap into WETH. Must be `<= msg.value`.                                             |
| `toMode`  | `To`      | Specifies what balance to send the WETH to (see [Internal Balances](../../overview/internal-balances.md)). |

### WETH

### [Wrap Ether](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/TokenFacet.sol#L178)

```solidity
function wrapEth(uint256 amount, LibTransfer.To mode) external payable;
```

Wraps Ether into WETH.

| Parameter | Type      | Description                                                                                                |
| --------- | --------- | ---------------------------------------------------------------------------------------------------------- |
| `amount`  | `uint256` | The amount of Ether to wrap into WETH. Must be `<= msg.value`.                                             |
| `toMode`  | `To`      | Specifies what balance to send the WETH to (see [Internal Balances](../../overview/internal-balances.md)). |

### [Unwrap Ether](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/TokenFacet.sol#L183)

```solidity
function unwrapEth(uint256 amount, LibTransfer.From mode) external payable;
```

Unwraps WETH into Ether.

| Parameter  | Type      | Description                                                                                                     |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------------- |
| `amount`   | `uint256` | The amount of WETH to unwrap into Ether.                                                                        |
| `fromMode` | `From`    | Specifies what balance to receive the WETH from (see [Internal Balances](../../overview/internal-balances.md)). |

## View Functions

### [Get Internal Balance](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L262)

```solidity
function getInternalBalance(address account, IERC20 token)
    public
    view
    returns (uint256 balance);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `token`   | `IERC20`  | WIP         |

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `balance`    | `uint256` | WIP         |

### [Get Internal Balances](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L273)

```solidity
function getInternalBalances(address account, IERC20[] memory tokens)
    external
    view
    returns (uint256[] memory balances);
```

| Parameter | Type       | Description |
| --------- | ---------- | ----------- |
| `account` | `address`  | WIP         |
| `tokens`  | `IERC20[]` | WIP         |

| Return Value | Type        | Description |
| ------------ | ----------- | ----------- |
| `balances`   | `uint256[]` | WIP         |

### [Get External Balance](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L289)

```solidity
function getExternalBalance(address account, IERC20 token)
    public
    view
    returns (uint256 balance);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `token`   | `IERC20`  | WIP         |

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `balance`    | `uint256` | WIP         |

### [Get External Balances](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L300)

```solidity
function getExternalBalances(address account, IERC20[] memory tokens)
    external
    view
    returns (uint256[] memory balances);
```

| Parameter | Type       | Description |
| --------- | ---------- | ----------- |
| `account` | `address`  | WIP         |
| `tokens`  | `IERC20[]` | WIP         |

| Return Value | Type        | Description |
| ------------ | ----------- | ----------- |
| `balances`   | `uint256[]` | WIP         |

### [Get Balance](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L316)

```solidity
function getBalance(address account, IERC20 token)
    public
    view
    returns (uint256 balance);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `token`   | `IERC20`  | WIP         |

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `balance`    | `uint256` | WIP         |

### [Get Balances](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L328)

```solidity
function getBalances(address account, IERC20[] memory tokens)
    external
    view
    returns (uint256[] memory balances);
```

| Parameter | Type       | Description |
| --------- | ---------- | ----------- |
| `account` | `address`  | WIP         |
| `tokens`  | `IERC20[]` | WIP         |

| Return Value | Type        | Description |
| ------------ | ----------- | ----------- |
| `balances`   | `uint256[]` | WIP         |

### [Get All Balance](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L343)

```solidity
function getAllBalance(address account, IERC20 token)
    public
    view
    returns (Balance memory b);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `token`   | `IERC20`  | WIP         |

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `b`          | `Balance` | WIP         |

### [Get All Balances](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L357)

```solidity
function getAllBalances(address account, IERC20[] memory tokens)
    external
    view
    returns (Balance[] memory balances);
```

| Parameter | Type       | Description |
| --------- | ---------- | ----------- |
| `account` | `address`  | WIP         |
| `tokens`  | `IERC20[]` | WIP         |

| Return Value | Type        | Description |
| ------------ | ----------- | ----------- |
| `balances`   | `Balance[]` | WIP         |

## Events

### [Internal Balance Changed](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L31) <a href="#event-internal-balance-changed" id="event-internal-balance-changed"></a>

```solidity
event InternalBalanceChanged(
    address indexed account,
    IERC20 indexed token,
    int256 delta
);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `token`   | `IERC20`  | WIP         |
| `delta`   | `int256`  | WIP         |

### [Token Approval](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/farm/TokenFacet.sol#L37) <a href="#event-token-approval" id="event-token-approval"></a>

```solidity
event TokenApproval(
    address indexed owner,
    address indexed spender,
    IERC20 token,
    uint256 amount
);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `owner`   | `address` | WIP         |
| `spender` | `address` | WIP         |
| `token`   | `IERC20`  | WIP         |
| `amount`  | `uint256` | WIP         |
