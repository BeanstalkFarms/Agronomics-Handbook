# Approval Facet

The Approval Facet handles all approval and permit related functions for the Silo.

## Call Functions

### Approvals

### [Approve Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ApprovalFacet.sol#L46)

```solidity
function approveDeposit(
    address spender,
    address token,
    uint256 amount
) external payable nonReentrant;
```

Approves an address to access a Farmer's Deposit.

| Parameter | Type      | Description                   |
| --------- | --------- | ----------------------------- |
| `spender` | `address` | Address to be given approval. |
| `token`   | `address` | Address of ERC20.             |
| `amount`  | `uint256` | Amount to be approved.        |

### [Increase Deposit Allowance](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ApprovalFacet.sol#L63)

```solidity
function increaseDepositAllowance(
    address spender, 
    address token, 
    uint256 addedValue
) public virtual nonReentrant returns (bool);
```

Increases transfer allowance of a Deposit.

| Parameter    | Type      | Description                            |
| ------------ | --------- | -------------------------------------- |
| `spender`    | `address` | Address to increase approval for.      |
| `token`      | `address` | Address of ERC20.                      |
| `addedValue` | `uint256` | Additional approval value to be given. |

| Return Value | Description                               |
| ------------ | ----------------------------------------- |
| `bool`       | If the allowance increase was successful. |

### [Decrease Deposit Allowance](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ApprovalFacet.sol#L84)

```solidity
function decreaseDepositAllowance(
    address spender, 
    address token, 
    uint256 subtractedValue
) public virtual nonReentrant returns (bool);
```

Decreases transfer allowance of a Deposit.

| Parameter         | Type      | Description                             |
| ----------------- | --------- | --------------------------------------- |
| `spender`         | `address` | Address to decrease approval for.       |
| `token`           | `address` | Address of ERC20.                       |
| `subtractedValue` | `uint256` | Amount of approval value to be removed. |

| Return Value | Description |
| ------------ | ----------- |
| `bool`       | Success.    |

### Permits

Farm balances and Silo Deposits support [EIP-2612 permits](https://eips.ethereum.org/EIPS/eip-2612), which allows Farmers to delegate use of their Farm balances and Silo Deposits through permits without the need for a separate transaction.

### [Permit Deposits](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ApprovalFacet.sol#L115)

```solidity
function permitDeposits(
    address owner,
    address spender,
    address[] calldata tokens,
    uint256[] calldata values,
    uint256 deadline,
    uint8 v,
    bytes32 r,
    bytes32 s
) external payable nonReentrant;
```

Permits multiple Deposits.

| Parameter  | Type        | Description                                            |
| ---------- | ----------- | ------------------------------------------------------ |
| `owner`    | `address`   | Owner of the Deposit.                                  |
| `spender`  | `address`   | Address to permit.                                     |
| `tokens`   | `address[]` | Array of ERC20s to permit.                             |
| `values`   | `uint256[]` | Array of amount (corresponding to `tokens`) to permit. |
| `deadline` | `uint256`   | Expiration of signature (Unix time).                   |
| `v`        | `uint8`     | Recovery ID.                                           |
| `r`        | `bytes32`   | ECDSA signature output.                                |
| `s`        | `bytes32`   | ECDSA signature output.                                |

### [Permit Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ApprovalFacet.sol#L143)

```solidity
function permitDeposit(
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

Permits a single Deposit.

| Parameter  | Type      | Description                          |
| ---------- | --------- | ------------------------------------ |
| `owner`    | `address` | Owner of the Deposit.                |
| `spender`  | `address` | Address to permit.                   |
| `token`    | `address` | ERC20 to permit.                     |
| `value`    | `uint256` | Amount of `token` to permit.         |
| `deadline` | `uint256` | Expiration of signature (Unix time). |
| `v`        | `uint8`   | Recovery ID.                         |
| `r`        | `bytes32` | ECDSA signature output.              |
| `s`        | `bytes32` | ECDSA signature output.              |

### [Set Approval for All](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ApprovalFacet.sol#L187)

```solidity
function setApprovalForAll(
    address spender, 
    bool approved
) external;
```

Set ERC-1155 approvals. Grants or revokes permission to `operator` to transfer the caller’s tokens, according to `approved`.

| Parameter  | Type      | Description                      |
| ---------- | --------- | -------------------------------- |
| `spender`  | `address` | Address to approve spending for. |
| `approved` | `bool`    | Whether or not to approve.       |

## View Functions

### [Deposit Permit Nonces](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ApprovalFacet.sol#L160)

```solidity
function depositPermitNonces(address owner) public view virtual returns (uint256);
```

Returns the current nonce for Deposit permits.

| Parameter | Type      | Description           |
| --------- | --------- | --------------------- |
| `owner`   | `address` | Owner of the Deposit. |

| Return Value | Description                        |
| ------------ | ---------------------------------- |
| `uint256`    | Current nonce for Deposit permits. |

### [Deposit Permit Domain Separator](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ApprovalFacet.sol#L167)

```solidity
function depositPermitDomainSeparator() external view returns (bytes32);
```

Returns the domain separator for the current chain ([link](https://docs.openzeppelin.com/contracts/3.x/api/drafts#EIP712-\_domainSeparatorV4--)).

| Return Value | Description                                 |
| ------------ | ------------------------------------------- |
| `bytes32`    | The domain separator for the current chain. |

### [Deposit Allowance](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ApprovalFacet.sol#L178)

```solidity
function depositAllowance(
    address owner,
    address spender,
    address token
) public view virtual returns (uint256);
```

Returns how much of a `token` Deposit that `spender` can transfer on behalf of `owner`.

| Parameter | Type      | Description                                    |
| --------- | --------- | ---------------------------------------------- |
| `owner`   | `address` | Owner of the Deposit.                          |
| `spender` | `address` | The address that can spend the Deposit.        |
| `token`   | `address` | The token Deposit that `spender` can transfer. |

| Return Value | Description                                                                  |
| ------------ | ---------------------------------------------------------------------------- |
| `uint256`    | The `token` Deposit amount that `spender` can transfer on behalf of `owner`. |

### [Is Approved for All](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ApprovalFacet.sol#L195)

```solidity
function isApprovedForAll(
    address _owner, 
    address _operator
) external view returns (bool);
```

Returns true if `_operator` is approved to transfer `_owner`'s Deposit.

| Parameter   | Type      | Description             |
| ----------- | --------- | ----------------------- |
| `_owner`    | `address` | Owner of the Deposit.   |
| `_operator` | `address` | Spender of the Deposit. |

| Return Value | Description                                                    |
| ------------ | -------------------------------------------------------------- |
| `bool`       | True if `_operator` is approved to transfer `_owner`'s tokens. |

## Events

### [Deposit Approval](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ApprovalFacet.sol#L26) <a href="#event-deposit-approval" id="event-deposit-approval"></a>

```solidity
event DepositApproval(
    address indexed owner,
    address indexed spender,
    address token,
    uint256 amount
);
```

Emitted when a Deposit is approved to spend by another account.

| Parameter | Type      | Description                                    |
| --------- | --------- | ---------------------------------------------- |
| `owner`   | `address` | Owner of the Deposit.                          |
| `spender` | `address` | Spender of the Deposit.                        |
| `token`   | `address` | Deposit token that can be spent.               |
| `amount`  | `uint256` | Amount of the Deposit token that can be spent. |

### [Approval for All](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ApprovalFacet.sol#L32) <a href="#event-deposit-approval" id="event-deposit-approval"></a>

```solidity
event ApprovalForAll(address indexed account, address indexed operator, bool approved);
```

Emitted when `account` grants or revokes permission to `operator` to transfer their tokens, according to `approved` ([link](https://docs.openzeppelin.com/contracts/3.x/api/token/erc1155#IERC1155-ApprovalForAll-address-address-bool-)).

| Parameter  | Type      | Description                              |
| ---------- | --------- | ---------------------------------------- |
| `account`  | `address` | Owner of the Deposit.                    |
| `operator` | `address` | Spender of the Deposit.                  |
| `approved` | `address` | Whether or not the Deposit was approved. |
