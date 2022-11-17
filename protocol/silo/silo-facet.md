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

### Withdraw

```solidity
function withdrawDeposit(
    address token,
    uint32 season,
    uint256 amount
) external payable updateSilo;

function withdrawDeposits(
    address token,
    uint32[] calldata seasons,
    uint256[] calldata amounts
) external payable updateSilo;
```

### Claim

```solidity
function claimWithdrawal(
    address token,
    uint32 season,
    LibTransfer.To mode
) external payable nonReentrant;

function claimWithdrawals(
    address token,
    uint32[] calldata seasons,
    LibTransfer.To mode
) external payable nonReentrant;
```

### Transfer

```solidity
function transferDeposit(
    address sender,
    address recipient,
    address token,
    uint32 season,
    uint256 amount
) external payable nonReentrant returns (uint256 bdv);

function transferDeposits(
    address sender,
    address recipient,
    address token,
    uint32[] calldata seasons,
    uint256[] calldata amounts
) external payable nonReentrant returns (uint256[] memory bdvs);
```

### Approvals

```solidity
function approveDeposit(
    address spender,
    address token,
    uint256 amount
) external payable nonReentrant;

function increaseDepositAllowance(
    address spender, 
    address token, 
    uint256 addedValue
) public virtual nonReentrant returns (bool);

function decreaseDepositAllowance(
    address spender, 
    address token, 
    uint256 subtractedValue
) public virtual nonReentrant returns (bool);
```

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

function depositPermitNonces(address owner) public view virtual returns (uint256);

function depositPermitDomainSeparator() external view returns (bytes32);
```

### Update

```solidity
function update(address account) external payable;
```

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

function enrootDeposit(
    address token,
    uint32 _season,
    uint256 amount
) external nonReentrant updateSilo;
```

## View Functions

```solidity
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
