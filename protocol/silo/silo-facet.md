# Silo Facet

SiloFacet handles depositing, withdrawing and claiming whitelisted Silo tokens.

## Call Functions

### Deposit

```solidity
function deposit(
    address token,
    uint256 amount,
    LibTransfer.From mode
) external payable nonReentrant updateSilo;
```

Deposits ERC20 token into internal Farmer balances.

| Parameter | Type      | Description                                                                 |
|-----------|-----------|-----------------------------------------------------------------------------|
| `token`   | `address` | Address of ERC20.                                                           |
| `amount`  | `uint256` | Amount of tokens to be transfered.                                          |
| `mode`    | `From`    | Source of funds (INTERNAL, EXTERNAL, EXTERNAL_INTERNAL, INTERNAL_TOLERANT). |

### Withdraw

```solidity
function withdrawDeposit(
    address token,
    uint32 season,
    uint256 amount
) external payable updateSilo;
```

Withdraws from a single Deposit.

| Parameter | Type      | Description                          |
|-----------|-----------|--------------------------------------|
| `token`   | `address` | Address of ERC20.                    |
| `season`  | `uint32`  | Season the Farmer wants to Withdraw. |
| `amount`  | `uint256` | Tokens to be Withdrawn.              |

```solidity
function withdrawDeposits(
    address token,
    uint32[] calldata seasons,
    uint256[] calldata amounts
) external payable updateSilo;
```

Withdraws from multiple Deposits.

| Parameter | Type        | Description                                                     |
|-----------|-------------|-----------------------------------------------------------------|
| `token`   | `address`   | Address of ERC20.                                               |
| `seasons` | `uint32[]`  | Array of Seasons to Withdraw from.                              |
| `amounts` | `uint256[]` | Array of amounts corresponding to each Season to Withdraw from. |

### Claim

```solidity
function claimWithdrawal(
    address token,
    uint32 season,
    LibTransfer.To mode
) external payable nonReentrant;
```

Claims tokens from a Withdrawal.

| Parameter | Type      | Description                                                                      |
|-----------|-----------|----------------------------------------------------------------------------------|
| `token`   | `address` | Address of ERC20.                                                                |
| `season`  | `uint32`  | Season to Claim.                                                                 |
| `mode`    | `To`      | Destination of funds (INTERNAL, EXTERNAL, EXTERNAL_INTERNAL, INTERNAL_TOLERANT). |

```solidity
function claimWithdrawals(
    address token,
    uint32[] calldata seasons,
    LibTransfer.To mode
) external payable nonReentrant;
```

Claims tokens from multiple Withdrawals.

| Parameter | Type       | Description                                                                      |
|-----------|------------|----------------------------------------------------------------------------------|
| `token`   | `address`  | Address of ERC20.                                                                |
| `seasons` | `uint32[]` | Array of Seasons to Claim.                                                       |
| `mode`    | `To`       | Destination of funds (INTERNAL, EXTERNAL, EXTERNAL_INTERNAL, INTERNAL_TOLERANT). |

### Transfer

```solidity
function transferDeposit(
    address sender,
    address recipient,
    address token,
    uint32 season,
    uint256 amount
) external payable nonReentrant returns (uint256 bdv);
```

Transfers single Farmer's Deposit.

| Parameter   | Type      | Description                    |
|-------------|-----------|--------------------------------|
| `sender`    | `address` | Source of Deposit.             |
| `recipient` | `address` | Destination of Deposit.        |
| `token`     | `address` | Address of ERC20.              |
| `season`    | `uint32`  | Season of Deposit to Transfer. |
| `amount`    | `uint256` | Tokens to transfer.            |

| Return Value | Type      | Description                         |
|--------------|-----------|-------------------------------------|
| `bdv`        | `uint256` | Bean Denominated Value of Transfer. |

```solidity
function transferDeposits(
    address sender,
    address recipient,
    address token,
    uint32[] calldata seasons,
    uint256[] calldata amounts
) external payable nonReentrant returns (uint256[] memory bdvs);
```

Transfers multiple Farmer Deposits.

| Parameter   | Type        | Description                                                     |
|-------------|-------------|-----------------------------------------------------------------|
| `sender`    | `address`   | Source of Deposit.                                              |
| `recipient` | `address`   | Destination of Deposit.                                         |
| `token`     | `address`   | Address of ERC20.                                               |
| `seasons`   | `uint32[]`  | Array of Seasons to Withdraw from.                              |
| `amounts`   | `uint256[]` | Array of amounts corresponding to each Season to Withdraw from. |

| Return Value | Type        | Description                                                                 |
|--------------|-------------|-----------------------------------------------------------------------------|
| `bdvs`       | `uint256[]` | Array of Bean Denominated Value of Transfer corresponding from each Season. |

### Approvals

```solidity
function approveDeposit(
    address spender,
    address token,
    uint256 amount
) external payable nonReentrant;
```

Approves an address to access a Farmer's Deposit.

| Parameter | Type      | Description                   |
|-----------|-----------|-------------------------------|
| `sender`  | `address` | Address to be given approval. |
| `token`   | `address` | Address of ERC20.             |
| `amount`  | `uint256` | Amount to be approved.        |

```solidity
function increaseDepositAllowance(
    address spender, 
    address token, 
    uint256 addedValue
) public virtual nonReentrant returns (bool);
```

Increases allowance of Deposit.

| Parameter    | Type      | Description                   |
|--------------|-----------|-------------------------------|
| `spender`    | `address` | Address to increase approval. |
| `token`      | `address` | Address of ERC20.             |
| `addedValue` | `uint256` | Additional value to be given. |

| Return Value | Description |
|--------------|-------------|
| `bool`       | Success.    |

```solidity
function decreaseDepositAllowance(
    address spender, 
    address token, 
    uint256 subtractedValue
) public virtual nonReentrant returns (bool);
```

Decreases allowance of Deposit.

| Parameter         | Type      | Description                   |
|-------------------|-----------|-------------------------------|
| `spender`         | `address` | Address to decrease approval. |
| `token`           | `address` | Address of ERC20.             |
| `subtractedValue` | `uint256` | Amount to be removed.         |

| Return Value | Description |
|--------------|-------------|
| `bool`       | Success.    |

### Permit

Farm balances and Silo Deposits support [EIP-2612 permits](https://eips.ethereum.org/EIPS/eip-2612), which allows Farmers to delegate use of their Farm balances through permits without the need for a separate transaction.

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

Permits multiple deposits.

| Parameter  | Type        | Description                                          |
|------------|-------------|------------------------------------------------------|
| `owner`    | `address`   | Address to give permit.                              |
| `spender`  | `address`   | Address to permit.                                   |
| `tokens`   | `address[]` | Array of ERC20s to permit.                           |
| `values`   | `uint256[]` | Array of amount (corresponding to tokens) to permit. |
| `deadline` | `uint256`   | Expiration of signature (Unix time).                 |
| `v`        | `uint8`     | Recovery ID.                                         |
| `r`        | `bytes32`   | ECDSA signature output.                              |
| `s`        | `bytes32`   | ECDSA signature output.                              |

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

Permits deposit.

| Parameter  | Type      | Description                          |
|------------|-----------|--------------------------------------|
| `owner`    | `address` | Address to give permit.              |
| `spender`  | `address` | Address to permit.                   |
| `token`    | `address` | ERC20 to permit.                     |
| `value`    | `uint256` | Amount to permit.                    |
| `deadline` | `uint256` | Expiration of signature (Unix time). |
| `v`        | `uint8`   | Recovery ID.                         |
| `r`        | `bytes32` | ECDSA signature output.              |
| `s`        | `bytes32` | ECDSA signature output.              |

### Update

```solidity
function update(address account) external payable;
```

Updates Farmer state.

| Parameter | Type      | Description        |
|-----------|-----------|--------------------|
| `account` | `address` | Address to update. |

### Plant

```solidity
function plant() external payable returns (uint256 beans);
```

Accredits Earned Beans and Stalk to Farmer.

| Return Value | Type      | Description                   |
|--------------|-----------|-------------------------------|
| `beans`      | `uint256` | Amount of Earned Beans given. |

### Claim Season of Plenty

```solidity
function claimPlenty() external payable;
```

Claims rewards from a Season Of Plenty (SOP).

### Enroot

```solidity
function enrootDeposits(
    address token,
    uint32[] calldata seasons,
    uint256[] calldata amounts
) external nonReentrant updateSilo;
```

Adds Revitalized Stalk and Seeds to Stalk and Seed balances.

| Parameter | Type        | Description                                           |
|-----------|-------------|-------------------------------------------------------|
| `token`   | `address`   | Address of ERC20.                                     |
| `seasons` | `uint32[]`  | Array of Seasons to Enroot.                           |
| `amounts` | `uint256[]` | Array of amount (corresponding to Seasons) to Enroot. |

```solidity
function enrootDeposit(
    address token,
    uint32 _season,
    uint256 amount
) external nonReentrant updateSilo;
```

Updates Unripe Deposit.

| Parameter | Type      | Description       |
|-----------|-----------|-------------------|
| `token`   | `address` | Address of ERC20. |
| `_season` | `uint32`  | Season to Enroot. |
| `amount`  | `uint256` | Amount to Enroot. |

## View Functions

### SiloFacet

```solidity 
function depositPermitNonces(address owner) public view virtual returns (uint256);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `owner`   | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

```solidity
function depositPermitDomainSeparator() external view returns (bytes32);
```

| Return Value | Description |
|--------------|-------------|
| `bytes32`    | WIP         |

### SiloExit

```solidity
function totalStalk() public view returns (uint256);
```

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

```solidity
function totalRoots() public view returns (uint256);
```

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

```solidity
function totalSeeds() public view returns (uint256);
```

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

```solidity
function totalEarnedBeans() public view returns (uint256);
```

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

```solidity
function balanceOfSeeds(address account) public view returns (uint256);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

```solidity
function balanceOfStalk(address account) public view returns (uint256);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

```solidity
function balanceOfRoots(address account) public view returns (uint256);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

```solidity
function balanceOfGrownStalk(
    address account
) public view returns (uint256);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

```solidity        
function balanceOfEarnedBeans(
    address account
) public view returns (uint256 beans);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `beans`      | `uint256` | WIP         |

```solidity
function balanceOfEarnedStalk(
    address account
) public view returns (uint256);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

```solidity
function balanceOfEarnedSeeds(
    address account
) public view returns (uint256);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

```solidity
function lastUpdate(address account) public view returns (uint32);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint32`     | WIP         |

```solidity
function lastSeasonOfPlenty() public view returns (uint32);
```

| Return Value | Description |
|--------------|-------------|
| `uint32`     | WIP         |

```solidity
function balanceOfPlenty(
    address account
) public view returns (uint256 plenty);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `plenty`     | `uint256` | WIP         |

```solidity
function balanceOfRainRoots(address account) public view returns (uint256);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

```solidity
function balanceOfSop(
    address account
) external view returns (AccountSeasonOfPlenty memory sop);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Type                    | Description |
|--------------|-------------------------|-------------|
| `sop`        | `AccountSeasonOfPlenty` | WIP         |

### TokenSilo

```solidity
function getDeposit(
    address account,
    address token,
    uint32 season
) external view returns (uint256, uint256);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |
| `uint256`    | WIP         |

```solidity
function getWithdrawal(
    address account,
    address token,
    uint32 season
) external view returns (uint256);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

```solidity
function getTotalDeposited(address token) external view returns (uint256);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `token`   | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

```solidity
function getTotalWithdrawn(address token) external view returns (uint256);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `token`   | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

```solidity
function tokenSettings(
    address token
) external view returns (Storage.SiloSettings memory);
````

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `token`   | `address` | WIP         |

| Return Value           | Description |
|------------------------|-------------|
| `Storage.SiloSettings` | WIP         |

```solidity
function withdrawFreeze() public view returns (uint8);
```

| Return Value | Description |
|--------------|-------------|
| `uint8`      | WIP         |

```solidity
function depositAllowance(
    address account,
    address spender,
    address token
) public view virtual returns (uint256);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `spender` | `address` | WIP         |
| `token`   | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

## Events

### TokenSilo

```solidity
event AddDeposit(
    address indexed account,
    address indexed token,
    uint32 season,
    uint256 amount,
    uint256 bdv
);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |
| `amount`  | `uint256` | WIP         |
| `bdv`     | `uint256` | WIP         |

```solidity
event RemoveDeposits(
    address indexed account,
    address indexed token,
    uint32[] seasons,
    uint256[] amounts,
    uint256 amount
);
```

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `account` | `address`   | WIP         |
| `token`   | `address`   | WIP         |
| `seasons` | `uint32[]`  | WIP         |
| `amounts` | `uint256[]` | WIP         |
| `amount`  | `uint256`   | WIP         |

```solidity
event RemoveDeposit(
    address indexed account,
    address indexed token,
    uint32 season,
    uint256 amount
);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |
| `amount`  | `uint256` | WIP         |

```solidity
event AddWithdrawal(
    address indexed account,
    address indexed token,
    uint32 season,
    uint256 amount
);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |
| `amount`  | `uint256` | WIP         |

```solidity
event RemoveWithdrawals(
    address indexed account,
    address indexed token,
    uint32[] seasons,
    uint256 amount
);
```

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `account` | `address`  | WIP         |
| `token`   | `address`  | WIP         |
| `seasons` | `uint32[]` | WIP         |
| `amount`  | `uint256`  | WIP         |

```solidity
event RemoveWithdrawal(
    address indexed account,
    address indexed token,
    uint32 season,
    uint256 amount
);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |
| `amount`  | `uint256` | WIP         |

```solidity
event DepositApproval(
    address indexed owner,
    address indexed spender,
    address token,
    uint256 amount
);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `owner`   | `address` | WIP         |
| `spender` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `amount`  | `uint256` | WIP         |

### Silo
 
```solidity
event Plant(
    address indexed account,
    uint256 beans
);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `beans`   | `uint256` | WIP         |

```solidity
event ClaimPlenty(
    address indexed account,
    uint256 plenty
);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `plenty`  | `uint256` | WIP         |

```solidity
event SeedsBalanceChanged(
    address indexed account,
    int256 delta
);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `delta`   | `int256`  | WIP         |

```solidity
event StalkBalanceChanged(
    address indexed account,
    int256 delta,
    int256 deltaRoots
);
```

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `account`    | `address` | WIP         |
| `delta`      | `int256`  | WIP         |
| `deltaRoots` | `int256`  | WIP         |
