# Silo Facet

SiloFacet handles depositing, withdrawing and claiming whitelisted Silo tokens.

## Call Functions

### SiloFacet.sol

#### Deposit

```solidity
function deposit(
    address token,
    uint256 amount,
    LibTransfer.From mode
) external payable nonReentrant updateSilo;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L25)

Deposits ERC20 token into internal Farmer balances.

| Parameter | Type      | Description                                                                 |
|-----------|-----------|-----------------------------------------------------------------------------|
| `token`   | `address` | Address of ERC20.                                                           |
| `amount`  | `uint256` | Amount of tokens to be transfered.                                          |
| `mode`    | `From`    | Source of funds (INTERNAL, EXTERNAL, EXTERNAL_INTERNAL, INTERNAL_TOLERANT). |

#### Withdraw Deposit

```solidity
function withdrawDeposit(
    address token,
    uint32 season,
    uint256 amount
) external payable updateSilo;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L43)

Withdraws from a single Deposit.

| Parameter | Type      | Description                          |
|-----------|-----------|--------------------------------------|
| `token`   | `address` | Address of ERC20.                    |
| `season`  | `uint32`  | Season the Farmer wants to Withdraw. |
| `amount`  | `uint256` | Tokens to be Withdrawn.              |

#### Withdraw Deposits

```solidity
function withdrawDeposits(
    address token,
    uint32[] calldata seasons,
    uint256[] calldata amounts
) external payable updateSilo;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L51)

Withdraws from multiple Deposits.

| Parameter | Type        | Description                                                     |
|-----------|-------------|-----------------------------------------------------------------|
| `token`   | `address`   | Address of ERC20.                                               |
| `seasons` | `uint32[]`  | Array of Seasons to Withdraw from.                              |
| `amounts` | `uint256[]` | Array of amounts corresponding to each Season to Withdraw from. |

#### Claim Withdrawal

```solidity
function claimWithdrawal(
    address token,
    uint32 season,
    LibTransfer.To mode
) external payable nonReentrant;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L63)

Claims tokens from a Withdrawal.

| Parameter | Type      | Description                                                                      |
|-----------|-----------|----------------------------------------------------------------------------------|
| `token`   | `address` | Address of ERC20.                                                                |
| `season`  | `uint32`  | Season to Claim.                                                                 |
| `mode`    | `To`      | Destination of funds (INTERNAL, EXTERNAL, EXTERNAL_INTERNAL, INTERNAL_TOLERANT). |

#### Claim Withdrawals

```solidity
function claimWithdrawals(
    address token,
    uint32[] calldata seasons,
    LibTransfer.To mode
) external payable nonReentrant;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L72)

Claims tokens from multiple Withdrawals.

| Parameter | Type       | Description                                                                      |
|-----------|------------|----------------------------------------------------------------------------------|
| `token`   | `address`  | Address of ERC20.                                                                |
| `seasons` | `uint32[]` | Array of Seasons to Claim.                                                       |
| `mode`    | `To`       | Destination of funds (INTERNAL, EXTERNAL, EXTERNAL_INTERNAL, INTERNAL_TOLERANT). |

#### Transfer Deposit

```solidity
function transferDeposit(
    address sender,
    address recipient,
    address token,
    uint32 season,
    uint256 amount
) external payable nonReentrant returns (uint256 bdv);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L85)

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

#### Transfer Deposits

```solidity
function transferDeposits(
    address sender,
    address recipient,
    address token,
    uint32[] calldata seasons,
    uint256[] calldata amounts
) external payable nonReentrant returns (uint256[] memory bdvs);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L101)

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

#### Approve Deposit

```solidity
function approveDeposit(
    address spender,
    address token,
    uint256 amount
) external payable nonReentrant;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L126)

Approves an address to access a Farmer's Deposit.

| Parameter | Type      | Description                   |
|-----------|-----------|-------------------------------|
| `sender`  | `address` | Address to be given approval. |
| `token`   | `address` | Address of ERC20.             |
| `amount`  | `uint256` | Amount to be approved.        |

#### Increase Deposit Allowance

```solidity
function increaseDepositAllowance(
    address spender, 
    address token, 
    uint256 addedValue
) public virtual nonReentrant returns (bool);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L136)

Increases allowance of Deposit.

| Parameter    | Type      | Description                   |
|--------------|-----------|-------------------------------|
| `spender`    | `address` | Address to increase approval. |
| `token`      | `address` | Address of ERC20.             |
| `addedValue` | `uint256` | Additional value to be given. |

| Return Value | Description |
|--------------|-------------|
| `bool`       | Success.    |

#### Decrease Deposit Allowance

```solidity
function decreaseDepositAllowance(
    address spender, 
    address token, 
    uint256 subtractedValue
) public virtual nonReentrant returns (bool);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L141)

Decreases allowance of Deposit.

| Parameter         | Type      | Description                   |
|-------------------|-----------|-------------------------------|
| `spender`         | `address` | Address to decrease approval. |
| `token`           | `address` | Address of ERC20.             |
| `subtractedValue` | `uint256` | Amount to be removed.         |

| Return Value | Description |
|--------------|-------------|
| `bool`       | Success.    |

#### Permit

Farm balances and Silo Deposits support [EIP-2612 permits](https://eips.ethereum.org/EIPS/eip-2612), which allows Farmers to delegate use of their Farm balances through permits without the need for a separate transaction.

#### Permit Deposits

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
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L148)

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

#### Permit Deposit

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
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L164)

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

#### Update

```solidity
function update(address account) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L193)

Updates Farmer state.

| Parameter | Type      | Description        |
|-----------|-----------|--------------------|
| `account` | `address` | Address to update. |

#### Plant

```solidity
function plant() external payable returns (uint256 beans);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L197)

Accredits Earned Beans and Stalk to Farmer.

| Return Value | Type      | Description                   |
|--------------|-----------|-------------------------------|
| `beans`      | `uint256` | Amount of Earned Beans given. |

#### Claim Plenty

```solidity
function claimPlenty() external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L201)

Claims rewards from a Season Of Plenty (SOP).

#### Enroot Deposits

```solidity
function enrootDeposits(
    address token,
    uint32[] calldata seasons,
    uint256[] calldata amounts
) external nonReentrant updateSilo;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L209)

Adds Revitalized Stalk and Seeds to Stalk and Seed balances.

| Parameter | Type        | Description                                           |
|-----------|-------------|-------------------------------------------------------|
| `token`   | `address`   | Address of ERC20.                                     |
| `seasons` | `uint32[]`  | Array of Seasons to Enroot.                           |
| `amounts` | `uint256[]` | Array of amount (corresponding to Seasons) to Enroot. |

#### Enroot Deposit

```solidity
function enrootDeposit(
    address token,
    uint32 _season,
    uint256 amount
) external nonReentrant updateSilo;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L252)

Updates Unripe Deposit.

| Parameter | Type      | Description       |
|-----------|-----------|-------------------|
| `token`   | `address` | Address of ERC20. |
| `_season` | `uint32`  | Season to Enroot. |
| `amount`  | `uint256` | Amount to Enroot. |

## View Functions

### SiloFacet.sol

#### Deposit Permit Nonces

```solidity 
function depositPermitNonces(address owner) public view virtual returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L178)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `owner`   | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Deposit Permit Domain Separator

```solidity
function depositPermitDomainSeparator() external view returns (bytes32);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L186)

| Return Value | Description |
|--------------|-------------|
| `bytes32`    | WIP         |

### SiloExit.sol

#### Total Stalk

```solidity
function totalStalk() public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L34)

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Total Roots

```solidity
function totalRoots() public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L38)

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Total Seeds

```solidity
function totalSeeds() public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L42)

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Total Earned Beans

```solidity
function totalEarnedBeans() public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L46)

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Balance Of Seeds

```solidity
function balanceOfSeeds(address account) public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L50)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Balance Of Stalk

```solidity
function balanceOfStalk(address account) public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L54)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Balance Of Roots

```solidity
function balanceOfRoots(address account) public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L58)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Balance Of Grown Stalk

```solidity
function balanceOfGrownStalk(
    address account
) public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L62)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Balance Of Earned Beans

```solidity        
function balanceOfEarnedBeans(
    address account
) public view returns (uint256 beans);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L74)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `beans`      | `uint256` | WIP         |

#### Balance Of Earned Stalk

```solidity
function balanceOfEarnedStalk(
    address account
) public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L103)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Balance Of Earned Seeds

```solidity
function balanceOfEarnedSeeds(
    address account
) public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L111)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Last Update

```solidity
function lastUpdate(address account) public view returns (uint32);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L119)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint32`     | WIP         |

#### Last Season Of Plenty

```solidity
function lastSeasonOfPlenty() public view returns (uint32);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L127)

| Return Value | Description |
|--------------|-------------|
| `uint32`     | WIP         |

#### Balance Of Plenty

```solidity
function balanceOfPlenty(
    address account
) public view returns (uint256 plenty);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L131)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `plenty`     | `uint256` | WIP         |

#### Balance Of Rain Roots

```solidity
function balanceOfRainRoots(address account) public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L173)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Balance Of Sop

```solidity
function balanceOfSop(
    address account
) external view returns (AccountSeasonOfPlenty memory sop);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L177)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |

| Return Value | Type                    | Description |
|--------------|-------------------------|-------------|
| `sop`        | `AccountSeasonOfPlenty` | WIP         |

### TokenSilo.sol

#### Get Deposit

```solidity
function getDeposit(
    address account,
    address token,
    uint32 season
) external view returns (uint256, uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L78)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |
| `uint256`    | WIP         |

#### Get Withdrawal

```solidity
function getWithdrawal(
    address account,
    address token,
    uint32 season
) external view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L86)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Get Total Deposited

```solidity
function getTotalDeposited(address token) external view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L94)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `token`   | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Get Total Withdrawn

```solidity
function getTotalWithdrawn(address token) external view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L98)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `token`   | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Token Settings

```solidity
function tokenSettings(
    address token
) external view returns (Storage.SiloSettings memory);
````
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L102)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `token`   | `address` | WIP         |

| Return Value           | Description |
|------------------------|-------------|
| `Storage.SiloSettings` | WIP         |

#### Withdraw Freeze

```solidity
function withdrawFreeze() public view returns (uint8);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L110)

| Return Value | Description |
|--------------|-------------|
| `uint8`      | WIP         |

#### Deposit Allowance

```solidity
function depositAllowance(
    address account,
    address spender,
    address token
) public view virtual returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L390)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `spender` | `address` | WIP         |
| `token`   | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

## Events

### Silo.sol

#### Plant
 
```solidity
event Plant(
    address indexed account,
    uint256 beans
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/Silo.sol#L21)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `beans`   | `uint256` | WIP         |

#### Claim Plenty

```solidity
event ClaimPlenty(
    address indexed account,
    uint256 plenty
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/Silo.sol#L26)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `plenty`  | `uint256` | WIP         |

#### Seeds Balance Changed

```solidity
event SeedsBalanceChanged(
    address indexed account,
    int256 delta
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/Silo.sol#L31)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `delta`   | `int256`  | WIP         |

#### Stalk Balance Changed

```solidity
event StalkBalanceChanged(
    address indexed account,
    int256 delta,
    int256 deltaRoots
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/Silo.sol#L36)

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `account`    | `address` | WIP         |
| `delta`      | `int256`  | WIP         |
| `deltaRoots` | `int256`  | WIP         |

### TokenSilo.sol

#### Add Deposit

```solidity
event AddDeposit(
    address indexed account,
    address indexed token,
    uint32 season,
    uint256 amount,
    uint256 bdv
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L20)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |
| `amount`  | `uint256` | WIP         |
| `bdv`     | `uint256` | WIP         |

#### Remove Deposits

```solidity
event RemoveDeposits(
    address indexed account,
    address indexed token,
    uint32[] seasons,
    uint256[] amounts,
    uint256 amount
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L27)

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `account` | `address`   | WIP         |
| `token`   | `address`   | WIP         |
| `seasons` | `uint32[]`  | WIP         |
| `amounts` | `uint256[]` | WIP         |
| `amount`  | `uint256`   | WIP         |

#### Remove Deposit

```solidity
event RemoveDeposit(
    address indexed account,
    address indexed token,
    uint32 season,
    uint256 amount
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L34)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |
| `amount`  | `uint256` | WIP         |

#### Add Withdrawal

```solidity
event AddWithdrawal(
    address indexed account,
    address indexed token,
    uint32 season,
    uint256 amount
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L41)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |
| `amount`  | `uint256` | WIP         |

#### Remove Withdrawals

```solidity
event RemoveWithdrawals(
    address indexed account,
    address indexed token,
    uint32[] seasons,
    uint256 amount
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L47)

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `account` | `address`  | WIP         |
| `token`   | `address`  | WIP         |
| `seasons` | `uint32[]` | WIP         |
| `amount`  | `uint256`  | WIP         |

#### Remove Withdrawal

```solidity
event RemoveWithdrawal(
    address indexed account,
    address indexed token,
    uint32 season,
    uint256 amount
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L53)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |
| `amount`  | `uint256` | WIP         |

#### Deposit Approval

```solidity
event DepositApproval(
    address indexed owner,
    address indexed spender,
    address token,
    uint256 amount
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L60)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `owner`   | `address` | WIP         |
| `spender` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `amount`  | `uint256` | WIP         |
