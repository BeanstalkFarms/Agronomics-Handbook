# Silo Facet

## Call Functions

### Deposit

```solidity
function deposit(
    address token,
    uint256 amount,
    LibTransfer.From mode
) external payable nonReentrant updateSilo;
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `token`   | `address` | WIP         |
| `amount`  | `uint256` | WIP         |
| `mode`    | `From`    | WIP         |

### Withdraw

```solidity
function withdrawDeposit(
    address token,
    uint32 season,
    uint256 amount
) external payable updateSilo;
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |
| `amount`  | `uint256` | WIP         |

```solidity
function withdrawDeposits(
    address token,
    uint32[] calldata seasons,
    uint256[] calldata amounts
) external payable updateSilo;
```

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `token`   | `address`   | WIP         |
| `seasons` | `uint32[]`  | WIP         |
| `amounts` | `uint256[]` | WIP         |

### Claim

```solidity
function claimWithdrawal(
    address token,
    uint32 season,
    LibTransfer.To mode
) external payable nonReentrant;
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |
| `mode`    | `To`      | WIP         |

```solidity
function claimWithdrawals(
    address token,
    uint32[] calldata seasons,
    LibTransfer.To mode
) external payable nonReentrant;
```

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `token`   | `address`  | WIP         |
| `seasons` | `uint32[]` | WIP         |
| `mode`    | `To`       | WIP         |

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

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `sender`    | `address` | WIP         |
| `recipient` | `address` | WIP         |
| `token`     | `address` | WIP         |
| `season`    | `uint32`  | WIP         |
| `amount`    | `uint256` | WIP         |

```solidity
function transferDeposits(
    address sender,
    address recipient,
    address token,
    uint32[] calldata seasons,
    uint256[] calldata amounts
) external payable nonReentrant returns (uint256[] memory bdvs);
```

| Parameter   | Type        | Description |
|-------------|-------------|-------------|
| `sender`    | `address`   | WIP         |
| `recipient` | `address`   | WIP         |
| `token`     | `address`   | WIP         |
| `seasons`   | `uint32[]`  | WIP         |
| `amounts`   | `uint256[]` | WIP         |

### Approvals

```solidity
function approveDeposit(
    address spender,
    address token,
    uint256 amount
) external payable nonReentrant;
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `sender`  | `address` | WIP         |
| `token`   | `address` | WIP         |
| `amount`  | `uint256` | WIP         |

```solidity
function increaseDepositAllowance(
    address spender, 
    address token, 
    uint256 addedValue
) public virtual nonReentrant returns (bool);
```

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `spender`    | `address` | WIP         |
| `token`      | `address` | WIP         |
| `addedValue` | `uint256` | WIP         |

```solidity
function decreaseDepositAllowance(
    address spender, 
    address token, 
    uint256 subtractedValue
) public virtual nonReentrant returns (bool);
```

| Parameter         | Type      | Description |
|-------------------|-----------|-------------|
| `spender`         | `address` | WIP         |
| `token`           | `address` | WIP         |
| `subtractedValue` | `uint256` | WIP         |

### Permit

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

| Parameter  | Type        | Description |
|------------|-------------|-------------|
| `owner`    | `address`   | WIP         |
| `spender`  | `address`   | WIP         |
| `tokens`   | `address[]` | WIP         |
| `values`   | `uint256[]` | WIP         |
| `deadline` | `uint256`   | WIP         |
| `v`        | `uint8`     | WIP         |
| `r`        | `bytes32`   | WIP         |
| `s`        | `bytes32`   | WIP         |

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

| Parameter  | Type      | Description |
|------------|-----------|-------------|
| `owner`    | `address` | WIP         |
| `spender`  | `address` | WIP         |
| `token`    | `address` | WIP         |
| `value`    | `uint256` | WIP         |
| `deadline` | `uint256` | WIP         |
| `v`        | `uint8`   | WIP         |
| `r`        | `bytes32` | WIP         |
| `s`        | `bytes32` | WIP         |

### Update

```solidity
function update(address account) external payable;
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

### Plant

```solidity
function plant() external payable returns (uint256 beans);
```

### Claim Season of Plenty

```solidity
function claimPlenty() external payable;
```

### Enroot

```solidity
function enrootDeposits(
    address token,
    uint32[] calldata seasons,
    uint256[] calldata amounts
) external nonReentrant updateSilo;
```

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `token`   | `address`   | WIP         |
| `seasons` | `uint32[]`  | WIP         |
| `amounts` | `uint256[]` | WIP         |

```solidity
function enrootDeposit(
    address token,
    uint32 _season,
    uint256 amount
) external nonReentrant updateSilo;
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `token`   | `address` | WIP         |
| `_season` | `uint32`  | WIP         |
| `amount`  | `uint256` | WIP         |

## View Functions

```solidity
/**
 * SiloFacet
 **/
 
function depositPermitNonces(address owner) public view virtual returns (uint256);

function depositPermitDomainSeparator() external view returns (bytes32);

/**
 * SiloExit
 **/
 
function totalStalk() public view returns (uint256);

function totalRoots() public view returns (uint256);

function totalSeeds() public view returns (uint256);

function totalEarnedBeans() public view returns (uint256);

function balanceOfSeeds(address account) public view returns (uint256);

function balanceOfStalk(address account) public view returns (uint256);

function balanceOfRoots(address account) public view returns (uint256);

function balanceOfGrownStalk(
    address account
) public view returns (uint256);
        
function balanceOfEarnedBeans(
    address account
) public view returns (uint256 beans);
       
function balanceOfEarnedStalk(
    address account
) public view returns (uint256);
        
function balanceOfEarnedSeeds(
    address account
) public view returns (uint256);

function lastUpdate(address account) public view returns (uint32);

function lastSeasonOfPlenty() public view returns (uint32);

function balanceOfPlenty(
    address account
) public view returns (uint256 plenty);
        
function balanceOfRainRoots(address account) public view returns (uint256);

function balanceOfSop(
    address account
) external view returns (AccountSeasonOfPlenty memory sop);

/**
 * TokenSilo
 **/
 
function getDeposit(
    address account,
    address token,
    uint32 season
) external view returns (uint256, uint256);
    
function getWithdrawal(
    address account,
    address token,
    uint32 season
) external view returns (uint256);
    
function getTotalDeposited(address token) external view returns (uint256);

function getTotalWithdrawn(address token) external view returns (uint256);

function tokenSettings(
    address token
) external view returns (Storage.SiloSettings memory);

function withdrawFreeze() public view returns (uint8);

function depositAllowance(
    address account,
    address spender,
    address token
) public view virtual returns (uint256);
```

## Events

```solidity
/**
 * TokenSilo
 **/

event AddDeposit(
    address indexed account,
    address indexed token,
    uint32 season,
    uint256 amount,
    uint256 bdv
);

event RemoveDeposits(
    address indexed account,
    address indexed token,
    uint32[] seasons,
    uint256[] amounts,
    uint256 amount
);

event RemoveDeposit(
    address indexed account,
    address indexed token,
    uint32 season,
    uint256 amount
);

event AddWithdrawal(
    address indexed account,
    address indexed token,
    uint32 season,
    uint256 amount
);

event RemoveWithdrawals(
    address indexed account,
    address indexed token,
    uint32[] seasons,
    uint256 amount
);

event RemoveWithdrawal(
    address indexed account,
    address indexed token,
    uint32 season,
    uint256 amount
);

event DepositApproval(
    address indexed owner,
    address indexed spender,
    address token,
    uint256 amount
);

/**
 * Silo
 **/
 
event Plant(
    address indexed account,
    uint256 beans
);

event ClaimPlenty(
    address indexed account,
    uint256 plenty
);

event SeedsBalanceChanged(
    address indexed account,
    int256 delta
);

event StalkBalanceChanged(
    address indexed account,
    int256 delta,
    int256 deltaRoots
);
```
