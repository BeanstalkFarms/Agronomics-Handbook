# Silo Facet

The Silo Facet handles Depositing, Withdrawing, Transferring and Claiming whitelisted Silo assets.

## Call Functions

### [Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L25)

```solidity
function deposit(
    address token,
    uint256 amount,
    LibTransfer.From mode
) external payable nonReentrant updateSilo;
```

Deposits ERC20 token into internal Farmer balances.

| Parameter | Type      | Description                          |
| --------- | --------- | ------------------------------------ |
| `token`   | `address` | Address of the token to Deposit.     |
| `amount`  | `uint256` | Amount of the token to be Deposited. |
| `mode`    | `From`    | Source of funds ().                  |

### [Withdraw Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L43)

```solidity
function withdrawDeposit(
    address token,
    uint32 season,
    uint256 amount
) external payable updateSilo;
```

Withdraws from a single Deposit.

| Parameter | Type      | Description                          |
| --------- | --------- | ------------------------------------ |
| `token`   | `address` | Address of ERC20.                    |
| `season`  | `uint32`  | Season the Farmer wants to Withdraw. |
| `amount`  | `uint256` | Tokens to be Withdrawn.              |

### [Withdraw Deposits](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L51)

```solidity
function withdrawDeposits(
    address token,
    uint32[] calldata seasons,
    uint256[] calldata amounts
) external payable updateSilo;
```

Withdraws from multiple Deposits.

| Parameter | Type        | Description                                                     |
| --------- | ----------- | --------------------------------------------------------------- |
| `token`   | `address`   | Address of ERC20.                                               |
| `seasons` | `uint32[]`  | Array of Seasons to Withdraw from.                              |
| `amounts` | `uint256[]` | Array of amounts corresponding to each Season to Withdraw from. |

### [Claim Withdrawal](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L63)

```solidity
function claimWithdrawal(
    address token,
    uint32 season,
    LibTransfer.To mode
) external payable nonReentrant;
```

Claims tokens from a Withdrawal.

| Parameter | Type      | Description                                                                        |
| --------- | --------- | ---------------------------------------------------------------------------------- |
| `token`   | `address` | Address of ERC20.                                                                  |
| `season`  | `uint32`  | Season to Claim.                                                                   |
| `mode`    | `To`      | Destination of funds (INTERNAL, EXTERNAL, EXTERNAL\_INTERNAL, INTERNAL\_TOLERANT). |

### [Claim Withdrawals](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L72)

```solidity
function claimWithdrawals(
    address token,
    uint32[] calldata seasons,
    LibTransfer.To mode
) external payable nonReentrant;
```

Claims tokens from multiple Withdrawals.

| Parameter | Type       | Description                                                                        |
| --------- | ---------- | ---------------------------------------------------------------------------------- |
| `token`   | `address`  | Address of ERC20.                                                                  |
| `seasons` | `uint32[]` | Array of Seasons to Claim.                                                         |
| `mode`    | `To`       | Destination of funds (INTERNAL, EXTERNAL, EXTERNAL\_INTERNAL, INTERNAL\_TOLERANT). |

### [Transfer Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L85)

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
| ----------- | --------- | ------------------------------ |
| `sender`    | `address` | Source of Deposit.             |
| `recipient` | `address` | Destination of Deposit.        |
| `token`     | `address` | Address of ERC20.              |
| `season`    | `uint32`  | Season of Deposit to Transfer. |
| `amount`    | `uint256` | Tokens to transfer.            |

| Return Value | Type      | Description                         |
| ------------ | --------- | ----------------------------------- |
| `bdv`        | `uint256` | Bean Denominated Value of Transfer. |

### [Transfer Deposits](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L101)

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
| ----------- | ----------- | --------------------------------------------------------------- |
| `sender`    | `address`   | Source of Deposit.                                              |
| `recipient` | `address`   | Destination of Deposit.                                         |
| `token`     | `address`   | Address of ERC20.                                               |
| `seasons`   | `uint32[]`  | Array of Seasons to Withdraw from.                              |
| `amounts`   | `uint256[]` | Array of amounts corresponding to each Season to Withdraw from. |

| Return Value | Type        | Description                                                                 |
| ------------ | ----------- | --------------------------------------------------------------------------- |
| `bdvs`       | `uint256[]` | Array of Bean Denominated Value of Transfer corresponding from each Season. |

### [Approve Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L126)

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
| `sender`  | `address` | Address to be given approval. |
| `token`   | `address` | Address of ERC20.             |
| `amount`  | `uint256` | Amount to be approved.        |

### [Increase Deposit Allowance](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L136)

```solidity
function increaseDepositAllowance(
    address spender, 
    address token, 
    uint256 addedValue
) public virtual nonReentrant returns (bool);
```

Increases allowance of Deposit.

| Parameter    | Type      | Description                   |
| ------------ | --------- | ----------------------------- |
| `spender`    | `address` | Address to increase approval. |
| `token`      | `address` | Address of ERC20.             |
| `addedValue` | `uint256` | Additional value to be given. |

| Return Value | Description |
| ------------ | ----------- |
| `bool`       | Success.    |

### [Decrease Deposit Allowance](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L141)

```solidity
function decreaseDepositAllowance(
    address spender, 
    address token, 
    uint256 subtractedValue
) public virtual nonReentrant returns (bool);
```

Decreases allowance of Deposit.

| Parameter         | Type      | Description                   |
| ----------------- | --------- | ----------------------------- |
| `spender`         | `address` | Address to decrease approval. |
| `token`           | `address` | Address of ERC20.             |
| `subtractedValue` | `uint256` | Amount to be removed.         |

| Return Value | Description |
| ------------ | ----------- |
| `bool`       | Success.    |

### Permit

Farm balances and Silo Deposits support [EIP-2612 permits](https://eips.ethereum.org/EIPS/eip-2612), which allows Farmers to delegate use of their Farm balances through permits without the need for a separate transaction.

### [Permit Deposits](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L148)

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
| ---------- | ----------- | ---------------------------------------------------- |
| `owner`    | `address`   | Address to give permit.                              |
| `spender`  | `address`   | Address to permit.                                   |
| `tokens`   | `address[]` | Array of ERC20s to permit.                           |
| `values`   | `uint256[]` | Array of amount (corresponding to tokens) to permit. |
| `deadline` | `uint256`   | Expiration of signature (Unix time).                 |
| `v`        | `uint8`     | Recovery ID.                                         |
| `r`        | `bytes32`   | ECDSA signature output.                              |
| `s`        | `bytes32`   | ECDSA signature output.                              |

### [Permit Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L164)

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
| ---------- | --------- | ------------------------------------ |
| `owner`    | `address` | Address to give permit.              |
| `spender`  | `address` | Address to permit.                   |
| `token`    | `address` | ERC20 to permit.                     |
| `value`    | `uint256` | Amount to permit.                    |
| `deadline` | `uint256` | Expiration of signature (Unix time). |
| `v`        | `uint8`   | Recovery ID.                         |
| `r`        | `bytes32` | ECDSA signature output.              |
| `s`        | `bytes32` | ECDSA signature output.              |

### [Update](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L193)

```solidity
function update(address account) external payable;
```

Updates Farmer state.

| Parameter | Type      | Description        |
| --------- | --------- | ------------------ |
| `account` | `address` | Address to update. |

### [Plant](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L197)

```solidity
function plant() external payable returns (uint256 beans);
```

Accredits Earned Beans and Stalk to Farmer.

| Return Value | Type      | Description                   |
| ------------ | --------- | ----------------------------- |
| `beans`      | `uint256` | Amount of Earned Beans given. |

### [Claim Plenty](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L201)

```solidity
function claimPlenty() external payable;
```

Claims rewards from a Season Of Plenty (SOP).

### [Enroot Deposits](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L209)

```solidity
function enrootDeposits(
    address token,
    uint32[] calldata seasons,
    uint256[] calldata amounts
) external nonReentrant updateSilo;
```

Adds Revitalized Stalk and Seeds to Stalk and Seed balances.

| Parameter | Type        | Description                                           |
| --------- | ----------- | ----------------------------------------------------- |
| `token`   | `address`   | Address of ERC20.                                     |
| `seasons` | `uint32[]`  | Array of Seasons to Enroot.                           |
| `amounts` | `uint256[]` | Array of amount (corresponding to Seasons) to Enroot. |

### [Enroot Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L252)

```solidity
function enrootDeposit(
    address token,
    uint32 _season,
    uint256 amount
) external nonReentrant updateSilo;
```

Updates Unripe Deposit.

| Parameter | Type      | Description       |
| --------- | --------- | ----------------- |
| `token`   | `address` | Address of ERC20. |
| `_season` | `uint32`  | Season to Enroot. |
| `amount`  | `uint256` | Amount to Enroot. |

## View Functions

### [Deposit Permit Nonces](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L178)

```solidity
function depositPermitNonces(address owner) public view virtual returns (uint256);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `owner`   | `address` | WIP         |

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |

### [Deposit Permit Domain Separator](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloFacet.sol#L186)

```solidity
function depositPermitDomainSeparator() external view returns (bytes32);
```

| Return Value | Description |
| ------------ | ----------- |
| `bytes32`    | WIP         |

### [Total Stalk](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L34)

```solidity
function totalStalk() public view returns (uint256);
```

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |

### [Total Roots](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L38)

```solidity
function totalRoots() public view returns (uint256);
```

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |

### [Total Seeds](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L42)

```solidity
function totalSeeds() public view returns (uint256);
```

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |

### [Total Earned Beans](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L46)

```solidity
function totalEarnedBeans() public view returns (uint256);
```

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |

### [Balance Of Seeds](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L50)

```solidity
function balanceOfSeeds(address account) public view returns (uint256);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |

### [Balance Of Stalk](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L54)

```solidity
function balanceOfStalk(address account) public view returns (uint256);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |

### [Balance Of Roots](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L58)

```solidity
function balanceOfRoots(address account) public view returns (uint256);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |

### [Balance Of Grown Stalk](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L62)

```solidity
function balanceOfGrownStalk(
    address account
) public view returns (uint256);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |

### [Balance Of Earned Beans](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L74)

```solidity
function balanceOfEarnedBeans(
    address account
) public view returns (uint256 beans);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `beans`      | `uint256` | WIP         |

### [Balance Of Earned Stalk](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L103)

```solidity
function balanceOfEarnedStalk(
    address account
) public view returns (uint256);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |

### [Balance Of Earned Seeds](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L111)

```solidity
function balanceOfEarnedSeeds(
    address account
) public view returns (uint256);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |

### [Last Update](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L119)

```solidity
function lastUpdate(address account) public view returns (uint32);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |

| Return Value | Description |
| ------------ | ----------- |
| `uint32`     | WIP         |

### [Last Season Of Plenty](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L127)

```solidity
function lastSeasonOfPlenty() public view returns (uint32);
```

| Return Value | Description |
| ------------ | ----------- |
| `uint32`     | WIP         |

### [Balance Of Plenty](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L131)

```solidity
function balanceOfPlenty(
    address account
) public view returns (uint256 plenty);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `plenty`     | `uint256` | WIP         |

### [Balance Of Rain Roots](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L173)

```solidity
function balanceOfRainRoots(address account) public view returns (uint256);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |

### [Balance Of Sop](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/SiloExit.sol#L177)

```solidity
function balanceOfSop(
    address account
) external view returns (AccountSeasonOfPlenty memory sop);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |

| Return Value | Type                    | Description |
| ------------ | ----------------------- | ----------- |
| `sop`        | `AccountSeasonOfPlenty` | WIP         |

### [Get Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L78)

```solidity
function getDeposit(
    address account,
    address token,
    uint32 season
) external view returns (uint256, uint256);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |
| `uint256`    | WIP         |

### [Get Withdrawal](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L86)

```solidity
function getWithdrawal(
    address account,
    address token,
    uint32 season
) external view returns (uint256);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |

### [Get Total Deposited](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L94)

```solidity
function getTotalDeposited(address token) external view returns (uint256);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `token`   | `address` | WIP         |

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |

### [Get Total Withdrawn](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L98)

```solidity
function getTotalWithdrawn(address token) external view returns (uint256);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `token`   | `address` | WIP         |

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |

### [Token Settings](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L102)

```solidity
function tokenSettings(
    address token
) external view returns (Storage.SiloSettings memory);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `token`   | `address` | WIP         |

| Return Value           | Description |
| ---------------------- | ----------- |
| `Storage.SiloSettings` | WIP         |

### [Withdraw Freeze](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L110)

```solidity
function withdrawFreeze() public view returns (uint8);
```

| Return Value | Description |
| ------------ | ----------- |
| `uint8`      | WIP         |

### [Deposit Allowance](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L390)

```solidity
function depositAllowance(
    address account,
    address spender,
    address token
) public view virtual returns (uint256);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `spender` | `address` | WIP         |
| `token`   | `address` | WIP         |

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |

## Events

### [Plant](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/Silo.sol#L21) <a href="#event-plant" id="event-plant"></a>

```solidity
event Plant(
    address indexed account,
    uint256 beans
);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `beans`   | `uint256` | WIP         |

### [Claim Plenty](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/Silo.sol#L26) <a href="#event-claim-plenty" id="event-claim-plenty"></a>

```solidity
event ClaimPlenty(
    address indexed account,
    uint256 plenty
);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `plenty`  | `uint256` | WIP         |

### [Seeds Balance Changed](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/Silo.sol#L31) <a href="#event-seeds-balance-changed" id="event-seeds-balance-changed"></a>

```solidity
event SeedsBalanceChanged(
    address indexed account,
    int256 delta
);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `delta`   | `int256`  | WIP         |

### [Stalk Balance Changed](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/Silo.sol#L36) <a href="#event-stalk-balance-changed" id="event-stalk-balance-changed"></a>

```solidity
event StalkBalanceChanged(
    address indexed account,
    int256 delta,
    int256 deltaRoots
);
```

| Parameter    | Type      | Description |
| ------------ | --------- | ----------- |
| `account`    | `address` | WIP         |
| `delta`      | `int256`  | WIP         |
| `deltaRoots` | `int256`  | WIP         |

### [Add Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L20) <a href="#event-add-deposit" id="event-add-deposit"></a>

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
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |
| `amount`  | `uint256` | WIP         |
| `bdv`     | `uint256` | WIP         |

### [Remove Deposits](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L27) <a href="#event-remove-deposits" id="event-remove-deposits"></a>

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
| --------- | ----------- | ----------- |
| `account` | `address`   | WIP         |
| `token`   | `address`   | WIP         |
| `seasons` | `uint32[]`  | WIP         |
| `amounts` | `uint256[]` | WIP         |
| `amount`  | `uint256`   | WIP         |

### [Remove Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L34) <a href="#event-remove-deposit" id="event-remove-deposit"></a>

```solidity
event RemoveDeposit(
    address indexed account,
    address indexed token,
    uint32 season,
    uint256 amount
);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |
| `amount`  | `uint256` | WIP         |

### [Add Withdrawal](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L41) <a href="#event-add-withdrawal" id="event-add-withdrawal"></a>

```solidity
event AddWithdrawal(
    address indexed account,
    address indexed token,
    uint32 season,
    uint256 amount
);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |
| `amount`  | `uint256` | WIP         |

### [Remove Withdrawals](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L47) <a href="#event-remove-withdrawals" id="event-remove-withdrawals"></a>

```solidity
event RemoveWithdrawals(
    address indexed account,
    address indexed token,
    uint32[] seasons,
    uint256 amount
);
```

| Parameter | Type       | Description |
| --------- | ---------- | ----------- |
| `account` | `address`  | WIP         |
| `token`   | `address`  | WIP         |
| `seasons` | `uint32[]` | WIP         |
| `amount`  | `uint256`  | WIP         |

### [Remove Withdrawal](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L53) <a href="#event-remove-withdrawal" id="event-remove-withdrawal"></a>

```solidity
event RemoveWithdrawal(
    address indexed account,
    address indexed token,
    uint32 season,
    uint256 amount
);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `season`  | `uint32`  | WIP         |
| `amount`  | `uint256` | WIP         |

### [Deposit Approval](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SiloFacet/TokenSilo.sol#L60) <a href="#event-deposit-approval" id="event-deposit-approval"></a>

```solidity
event DepositApproval(
    address indexed owner,
    address indexed spender,
    address token,
    uint256 amount
);
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `owner`   | `address` | WIP         |
| `spender` | `address` | WIP         |
| `token`   | `address` | WIP         |
| `amount`  | `uint256` | WIP         |
