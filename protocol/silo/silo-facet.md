# Silo Facet

The Silo Facet handles Depositing, Withdrawing, and transferring Deposits (whitelisted assets in the Silo).

Stems keep track of when the Deposit was created. When the Deposit was created determines how much Grown Stalk per BDV the Deposit has.

## Call Functions

### [Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloFacet.sol#L48)

```solidity
function deposit(
    address token,
    uint256 _amount,
    LibTransfer.From mode
) 
    external 
    payable 
    nonReentrant 
    mowSender(token)
    returns (uint256 amount, uint256 bdv, int96 stem);
```

Deposits ERC20 token into internal Farmer balances.

| Parameter | Type      | Description                                                                                            |
| --------- | --------- | ------------------------------------------------------------------------------------------------------ |
| `token`   | `address` | Address of the token to Deposit.                                                                       |
| `_amount` | `uint256` | Amount of the token to be Deposited.                                                                   |
| `mode`    | `From`    | The balance to transfer the token from; see [`LibTransfer.From`](../../overview/internal-balances.md). |

| Return value | Type      | Description                    |
| ------------ | --------- | ------------------------------ |
| `amount`     | `address` | Amount of the token Deposited. |
| `bdv`        | `uint256` | BDV of the Deposit.            |
| `stem`       | `int96`   | Stem of the Deposit.           |

### [Withdraw Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloFacet.sol#L90)

```solidity
function withdrawDeposit(
    address token,
    int96 stem,
    uint256 amount
    LibTransfer.To mode
) external payable mowSender(token) nonReentrant;
```

Withdraws a single Deposit.

| Parameter | Type      | Description                                                                                        |
| --------- | --------- | -------------------------------------------------------------------------------------------------- |
| `token`   | `address` | Address of ERC20 being Withdrawn.                                                                  |
| `stem`    | `int96`   | Stem of the Deposit to Withdraw.                                                                   |
| `amount`  | `uint256` | Tokens to be Withdrawn.                                                                            |
| `mode`    | `To`      | The balance to transfer the token to; see [`LibTransfer.To`](../../overview/internal-balances.md). |

### [Withdraw Deposits](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloFacet.sol#L114)

```solidity
function withdrawDeposits(
    address token,
    int96[] calldata stems,
    uint256[] calldata amounts,
    LibTransfer.To mode
) external payable mowSender(token) nonReentrant;
```

Withdraws multiple Deposits.

| Parameter | Type        | Description                                                                                        |
| --------- | ----------- | -------------------------------------------------------------------------------------------------- |
| `token`   | `address`   | Address of ERC20 being Withdrawn.                                                                  |
| `stems`   | `int96[]`   | Stems of the Deposits to Withdraw.                                                                 |
| `amounts` | `uint256[]` | Array of token amounts to Withdraw from corresponding `stems`.                                     |
| `mode`    | `To`        | The balance to transfer the token to; see [`LibTransfer.To`](../../overview/internal-balances.md). |

### [Transfer Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloFacet.sol#L142)

```solidity
function transferDeposit(
    address sender,
    address recipient,
    address token,
    int96 stem,
    uint256 amount
) public payable nonReentrant returns (uint256 bdv);
```

Transfers single Farmer's Deposit.

| Parameter   | Type      | Description                                   |
| ----------- | --------- | --------------------------------------------- |
| `sender`    | `address` | Source of Deposit.                            |
| `recipient` | `address` | Destination of Deposit.                       |
| `token`     | `address` | Address of Deposited ERC20 being transferred. |
| `stem`      | `int96`   | Stem of Deposit to Transfer.                  |
| `amount`    | `uint256` | Amount of tokens to transfer.                 |

| Return Value | Type      | Description                   |
| ------------ | --------- | ----------------------------- |
| `bdv`        | `uint256` | BDV now owned by `recipient`. |

### [Transfer Deposits](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloFacet.sol#L174)

```solidity
function transferDeposits(
    address sender,
    address recipient,
    address token,
    int96[] calldata stem,
    uint256[] calldata amounts
) public payable nonReentrant returns (uint256[] memory bdvs);
```

Transfers multiple Farmer Deposits.

| Parameter   | Type        | Description                                                        |
| ----------- | ----------- | ------------------------------------------------------------------ |
| `sender`    | `address`   | Source of Deposit.                                                 |
| `recipient` | `address`   | Destination of Deposit.                                            |
| `token`     | `address`   | Address of ERC20 being transferred.                                |
| `stem`      | `int96[]`   | Stems of Deposits to transfer.                                     |
| `amounts`   | `uint256[]` | Array of token amounts to transfer based on corresponding `stems`. |

| Return Value | Type        | Description                                |
| ------------ | ----------- | ------------------------------------------ |
| `bdvs`       | `uint256[]` | Array of BDVs of each Deposit transferred. |

### [Safe Transfer From](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloFacet.sol#L208)

```solidity
function safeTransferFrom(
    address sender, 
    address recipient, 
    uint256 depositId, 
    uint256 amount,
    bytes calldata
) external;
```

Transfer a single Deposit, conforming to the ERC1155 standard.

| Parameter   | Type      | Description                     |
| ----------- | --------- | ------------------------------- |
| `sender`    | `address` | Source of Deposit.              |
| `recipient` | `address` | Destination of Deposit.         |
| `depositId` | `uint256` | ID of Deposit to transfer.      |
| `amount`    | `uint256` | Amount of ERC1155 to transfer.  |

### [Safe Batch Transfer From](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloFacet.sol#L239)

```solidity
function safeBatchTransferFrom(
    address sender, 
    address recipient, 
    uint256[] calldata depositIds, 
    uint256[] calldata amounts, 
    bytes calldata
) external;
```

Transfer a single Deposit, conforming to the ERC1155 standard.

| Parameter    | Type        | Description                                                             |
| ------------ | ----------- | ----------------------------------------------------------------------- |
| `sender`     | `address`   | Source of Deposit.                                                      |
| `recipient`  | `address`   | Destination of Deposit.                                                 |
| `depositIds` | `uint256[]` | Array of IDs of Deposits to transfer.                                   |
| `amounts`    | `uint256[]` | Array of amounts of ERC1155 to transfer, corresponding to `depositIds`. |

### Yield Distribution

### [Mow](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloFacet.sol#L270)

```solidity
function mow(address account, address token) external payable;
```

Claim Grown Stalk for an account for a particular whitelisted asset.

| Parameter | Type      | Description                          |
| --------- | --------- | ------------------------------------ |
| `account` | `address` | Address to Mow for.                  |
| `token`   | `address` | Address of ERC20 Deposit to Mow for. |

### [Mow Multiple](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloFacet.sol#L275)

```solidity
function mowMultiple(address account, address[] calldata tokens) external payable;
```

Mow for multiple whitelisted assets for an account.

| Parameter | Type        | Description                                      |
| --------- | ----------- | ------------------------------------------------ |
| `account` | `address`   | Address to Mow for.                              |
| `tokens`  | `address[]` | Array of addresses of ERC20 Deposits to Mow for. |

### [Plant](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloFacet.sol#L297)

```solidity
function plant() 
    external payable returns (uint256 beans, int96 stem);
```

Claim Earned Beans and their associated Stalk and Plantable Seeds for `msg.sender`.

| Return Value | Type      | Description                   |
| ------------ | --------- | ----------------------------- |
| `beans`      | `uint256` | Amount of Earned Beans given. |
| `stem`       | `int96`   | Stem of the new Deposit.      |

### [Claim Plenty](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloFacet.sol#L304)

```solidity
function claimPlenty() external payable;
```

Claims rewards from a Flood (Season of Plenty) for `msg.sender`.

## View Functions

### Utilities

### [Last Update](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L58)

```solidity
function lastUpdate(address account) public view returns (uint32);
```

Get the last Season in which `account` updated their Silo.

| Return Type | Description                               |
| ----------- | ----------------------------------------- |
| `uint32`    | Last Season `account` updated their Silo. |

### Silo Totals

### [Total Stalk](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L67)

```solidity
function totalStalk() public view returns (uint256);
```

Returns the total supply of Stalk. Does NOT include Grown Stalk.

| Return Type | Description            |
| ----------- | ---------------------- |
| `uint256`   | Total supply of Stalk. |

### [Total Roots](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L74)

```solidity
function totalRoots() public view returns (uint256);
```

Returns the total supply of Roots.

| Return Type | Description                |
| ----------- | -------------------------- |
| `uint256`   | The total supply of Roots. |

### [Total Earned Beans](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L84)

```solidity
function totalEarnedBeans() public view returns (uint256);
```

Returns the total supply of Earned Beans.

| Return Type | Description                   |
| ----------- | ----------------------------- |
| `uint256`   | Total supply of Earned Beans. |

### Silo Account Balances

### [Balance Of Stalk](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L97)

```solidity
function balanceOfStalk(address account) public view returns (uint256);
```

Returns the balance of Stalk for a particular Farmer. Does NOT include Grown Stalk; does include Earned Stalk.

| Parameter | Type      | Description                          |
| --------- | --------- | ------------------------------------ |
| `account` | `address` | Farmer to get the Stalk balance for. |

| Return Type | Description                 |
| ----------- | --------------------------- |
| `uint256`   | Stalk balance of `account`. |

### [Balance Of Roots](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L115)

```solidity
function balanceOfRoots(address account) public view returns (uint256);
```

Returns the balance of Roots for a particular Farmer.

| Parameter | Type      | Description                          |
| --------- | --------- | ------------------------------------ |
| `account` | `address` | Farmer to get the Roots balance for. |

| Return Type | Description                 |
| ----------- | --------------------------- |
| `uint256`   | Roots balance of `account`. |

### [Balance Of Grown Stalk](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L126)

```solidity
function balanceOfGrownStalk(address account, address token)
    public
    view
    returns (uint256);
```

Returns the balance of Grown Stalk for `account`. Grown Stalk is earned each Season from BDV and must be Mown to add it to a user's Stalk balance.

| Parameter | Type      | Description                                |
| --------- | --------- | ------------------------------------------ |
| `account` | `address` | Farmer to get the Grown Stalk balance for. |

| Return Type | Description                       |
| ----------- | --------------------------------- |
| `uint256`   | Grown Stalk balance of `account`. |

### [Grown Stalk for Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L146)

```solidity
function grownStalkForDeposit(
    address account,
    address token,
    int96 stem
)
    public
    view
    returns (uint grownStalk);
```

Returns the balance of Grown Stalk for a single deposit of `token` in `stem` for `account`.

| Parameter | Type      | Description                                                      |
| --------- | --------- | ---------------------------------------------------------------- |
| `account` | `address` | Farmer that owns the Deposit to get the Grown Stalk balance for. |
| `token`   | `address` | ERC20 token address of the Deposit.                              |
| `stem`    | `int96`   | Stem of the Deposit.                                             |

| Return Value | Type   | Description              |
| ------------ | ------ | ------------------------ |
| `grownStalk` | `uint` | Grown Stalk for Deposit. |

### [Balance Of Earned Beans](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L162)

```solidity
function balanceOfEarnedBeans(address account)
    public
    view
    returns (uint256 beans);
```

Returns the balance of Earned Beans for a Farmer.

| Parameter | Type      | Description                                |
| --------- | --------- | ------------------------------------------ |
| `account` | `address` | Farmer to get the Earned Bean balance for. |

| Return Value | Type      | Description                       |
| ------------ | --------- | --------------------------------- |
| `beans`      | `uint256` | Earned Bean balance of `account`. |

### [Balance Of Earned Stalk](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L217)

```solidity
function balanceOfEarnedStalk(address account)
    public
    view
    returns (uint256)
```

Return the `account` balance of Earned Stalk, the Stalk associated with Earned Beans.

| Parameter | Type      | Description                                 |
| --------- | --------- | ------------------------------------------- |
| `account` | `address` | Farmer to get the Earned Stalk balance for. |

| Return Type | Description                        |
| ----------- | ---------------------------------- |
| `uint256`   | Earned Stalk balance of `account`. |

### Season of Plenty (Flood)

### [Last Season Of Plenty](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L231)

```solidity
function lastSeasonOfPlenty() public view returns (uint32);
```

Returns the last Season that a Season of Plenty started.

| Return Value | Description                          |
| ------------ | ------------------------------------ |
| `uint32`     | The last Season it started Flooding. |

### [Balance Of Plenty](https://github.com/BeanstalkFarms/Beanstalk/blob/9f286e1f1b1e67bc40d35aaf4b16e5c6d83ebdd9/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L239)

```solidity
function balanceOfPlenty(address account)
    public
    view
    returns (uint256 plenty);
```

Returns the Farmer's balance of unclaimed 3CRV earned from the Season of Plenty.

| Parameter | Type      | Description                                   |
| --------- | --------- | --------------------------------------------- |
| `account` | `address` | Farmer to get the unclaimed 3CRV balance for. |

| Return Value | Type      | Description                          |
| ------------ | --------- | ------------------------------------ |
| `plenty`     | `uint256` | Unclaimed 3CRV balance of `account`. |

### [Balance Of Rain Roots](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L251)

```solidity
function balanceOfRainRoots(address account) public view returns (uint256);
```

Returns the `account` balance of Roots the last time it was Raining during a Silo update.

| Parameter | Type      | Description                             |
| --------- | --------- | --------------------------------------- |
| `account` | `address` | Farmer to get "Rain Roots" balance for. |

| Return Value | Description                                          |
| ------------ | ---------------------------------------------------- |
| `uint256`    | Root balance last time it was Raining for `account`. |

### [Balance of SOP](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L259)

```solidity
function balanceOfSop(address account)
    external
    view
    returns (AccountSeasonOfPlenty memory sop);
```

Returns the `account` Season of Plenty related state variables.

| Parameter | Type      | Description                                    |
| --------- | --------- | ---------------------------------------------- |
| `account` | `address` | Farmer to get SOP related state variables for. |

| Return Value | Type                    | Description                                    |
| ------------ | ----------------------- | ---------------------------------------------- |
| `sop`        | `AccountSeasonOfPlenty` | Struct containing SOP related state variables. |

### Stems

### [Stem Tip for Token](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L285)

```solidity
function stemTipForToken(address token)
    public
    view
    returns (int96 _stemTip);
```

Returns the "stemTip", or cumulative Grown Stalk Per BDV of a given Deposited asset since whitelist, for a given whitelisted token.

| Parameter | Type      | Description                          |
| --------- | --------- | ------------------------------------ |
| `token`   | `address` | ERC20 token to get the Stem tip for. |

| Return Value | Type    | Description                       |
| ------------ | ------- | --------------------------------- |
| `_stemTip`   | `int96` | Returns the Stem tip for `token`. |

### [Season to Stem](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L299)

```solidity
function seasonToStem(address token, uint32 season)
    public
    view
    returns (int96 stem);
```

Get the Stem associated with a particular Deposit (via its token and Season). Kept for legacy reasons.

| Parameter | Type      | Description                 |
| --------- | --------- | --------------------------- |
| `token`   | `address` | ERC20 token of the Deposit. |
| `season`  | `uint32`  | Season of the Deposit.      |

| Return Value | Type    | Description          |
| ------------ | ------- | -------------------- |
| `stem`       | `int96` | Stem of the Deposit. |

### [Get Seeds per Token](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L314)

```solidity
function getSeedsPerToken(address token) public view virtual returns (uint256);
```

Gets the Seeds per token for legacy whitelisted assets. Calling with an non-legacy token will return 0, even after the token is whitelisted. Kept for legacy reasons.

| Parameter | Type      | Description                        |
| --------- | --------- | ---------------------------------- |
| `token`   | `address` | Legacy token to get the Seeds for. |

| Return Type | Description                 |
| ----------- | --------------------------- |
| `uint256`   | Seeds for the legacy token. |

### [Stem Start Season](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L321)

```solidity
function stemStartSeason() public view virtual returns (uint16);
```

Returns the Season in which Beanstalk initialized [Silo V3](https://bean.money/bip-36), i.e., the Season in which Stems were initialized.

| Return Type | Description                             |
| ----------- | --------------------------------------- |
| `uint16`    | Season in which Stems were initialized. |

### [Migration Needed](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L328)

```solidity
function migrationNeeded(address account) public view returns (bool);
```

Returns whether or not a Farmer needs to migrate to [Silo V3](https://bean.money/bip-36).

| Parameter | Type      | Description                                 |
| --------- | --------- | ------------------------------------------- |
| `account` | `address` | Farmer to check if migration is needed for. |

| Return Type | Description                                           |
| ----------- | ----------------------------------------------------- |
| `bool`      | Whether or not `account` needs to migrate to Silo V3. |

### [In Vesting Period](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/SiloExit.sol#L340)

```solidity
function inVestingPeriod() public view returns (bool);
```

Returns if Earned Beans from the previous `gm` call are still vesting. Vesting Earned Beans cannot be received via `plant` until the Vesting Period is over, and will be forfeited if a Farmer Withdraws during the Vesting Period.

| Return Type | Description                                                                         |
| ----------- | ----------------------------------------------------------------------------------- |
| `bool`      | Whether or not Earned Beans from the previous `gm` function call are still vesting. |

### Getters

### [Get Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/TokenSilo.sol#L408)

```solidity
function getDeposit(
    address account,
    address token,
    int96 stem
) external view returns (uint256, uint256)
```

Find the amount and BDV of `token` that a Farmer has Deposited in a given Stem.

| Parameter | Type      | Description                     |
| --------- | --------- | ------------------------------- |
| `account` | `address` | Farmer to get Deposit data for. |
| `token`   | `address` | ERC20 token of the Deposit.     |
| `stem`    | `int96`   | Stem of the Deposit.            |

| Return Value | Description                      |
| ------------ | -------------------------------- |
| `uint256`    | Number of tokens in the Deposit. |
| `uint256`    | BDV of the Deposit.              |

### [Get Total Deposited](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/TokenSilo.sol#L419)

```solidity
function getTotalDeposited(address token) external view returns (uint256);
```

Get the total amount of `token` currently Deposited in the Silo across all Farmers.

| Parameter | Type      | Description                |
| --------- | --------- | -------------------------- |
| `token`   | `address` | Whitelisted token address. |

| Return Type | Description                                    |
| ----------- | ---------------------------------------------- |
| `uint256`   | Total number of `token` Deposited in the Silo. |

### [Get Total Deposited BDV](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/TokenSilo.sol#L426)

```solidity
function getTotalDepositedBdv(address token) external view returns (uint256);
```

Get the total BDV of `token` currently Deposited in the Silo across all Farmers.

| Parameter | Type      | Description                |
| --------- | --------- | -------------------------- |
| `token`   | `address` | Whitelisted token address. |

| Return Type | Description                                 |
| ----------- | ------------------------------------------- |
| `uint256`   | Total BDV of `token` Deposited in the Silo. |

### [Token Settings](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/TokenSilo.sol#L440)

```solidity
function tokenSettings(address token)
    external
    view
    returns (Storage.SiloSettings memory);
```

Get the `Storage.SiloSettings` for a whitelisted token.

| Parameter | Type      | Description                |
| --------- | --------- | -------------------------- |
| `token`   | `address` | Whitelisted token address. |

| Return Type            | Description                             |
| ---------------------- | --------------------------------------- |
| `Storage.SiloSettings` | Struct with Silo variables for `token`. |

### ERC-1155

### [Balance Of](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/TokenSilo.sol#L455)

```solidity
function balanceOf(
    address account, 
    uint256 depositId
) external view returns (uint256 amount);
```

Gets the amount of tokens in a Deposit type for a given Farmer.

| Parameter   | Type      | Description                            |
| ----------- | --------- | -------------------------------------- |
| `account`   | `address` | Farmer to get Deposit amount for.      |
| `depositId` | `uint256` | Deposit ID corresponding to `account`. |

| Return Type | Description                                       |
| ----------- | ------------------------------------------------- |
| `amount`    | Amount of tokens in a Deposit type for `account`. |

### [Balance Of Batch](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/TokenSilo.sol#L465)

```solidity
function balanceOfBatch(
    address[] calldata accounts, 
    uint256[] calldata depositIds
) external view returns (uint256[] memory);
```

Gets an array of amounts corresponding to Deposits.

| Parameter    | Type        | Description                                      |
| ------------ | ----------- | ------------------------------------------------ |
| `accounts`   | `address[]` | List of Farmers.                                 |
| `depositIds` | `uint256[]` | List of Deposit IDs corresponding to `accounts`. |

| Return Type | Description                                             |
| ----------- | ------------------------------------------------------- |
| `uint256[]` | Array of amounts corresponding to the list of Deposits. |

### [Get Deposit ID](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/TokenSilo.sol#L483)

```solidity
function getDepositId(
    address token, 
    int96 stem
) external pure returns (uint256);
```

Gets the Deposit ID given an whitelisted token address and Stem.

| Parameter | Type      | Description                |
| --------- | --------- | -------------------------- |
| `token`   | `address` | Whitelisted token address. |
| `stem`    | `int96`   | Stem of the Deposit.       |

| Return Type | Description                        |
| ----------- | ---------------------------------- |
| `uint256`   | Deposit ID of `token` with `stem`. |

## Events

### [Plant](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/Silo.sol#L37) <a href="#event-plant" id="event-plant"></a>

```solidity
event Plant(
    address indexed account,
    uint256 beans
);
```

Emitted when the deposit associated with the Earned Beans of `account` are Planted.

| Parameter | Type      | Description                             |
| --------- | --------- | --------------------------------------- |
| `account` | `address` | Farmer that Planted their Earned Beans. |
| `beans`   | `uint256` | The amount of Earned Beans claimed.     |

### [Claim Plenty](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/Silo.sol#L52) <a href="#event-claim-plenty" id="event-claim-plenty"></a>

```solidity
event ClaimPlenty(
    address indexed account,
    uint256 plenty
);
```

Emitted when 3CRV paid to `account` during a Flood is claimed.

| Parameter | Type      | Description                              |
| --------- | --------- | ---------------------------------------- |
| `account` | `address` | Farmer that claimed the assets.          |
| `plenty`  | `uint256` | The amount of 3CRV claimed by `account`. |

### [Stalk Balance Changed](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/Silo.sol#L71) <a href="#event-stalk-balance-changed" id="event-stalk-balance-changed"></a>

```solidity
event StalkBalanceChanged(
    address indexed account,
    int256 delta,
    int256 deltaRoots
);
```

Emitted when `account` gains or loses Stalk.

| Parameter    | Type      | Description                             |
| ------------ | --------- | --------------------------------------- |
| `account`    | `address` | The Farmer whose Stalk balance changed. |
| `delta`      | `int256`  | The change in Stalk.                    |
| `deltaRoots` | `int256`  | The change in Roots.                    |

### [Add Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/TokenSilo.sol#L44) <a href="#event-add-deposit" id="event-add-deposit"></a>

```solidity
event AddDeposit(
    address indexed account,
    address indexed token,
    int96 stem,
    uint256 amount,
    uint256 bdv
);
```

Emitted when `account` adds a single Deposit to the Silo. There is no `AddDeposits` event because there is currently no operation in which Beanstalk creates multiple Deposits in different Stems.

| Parameter | Type      | Description                                                         |
| --------- | --------- | ------------------------------------------------------------------- |
| `account` | `address` | The Farmer that added a Deposit to Beanstalk.                       |
| `token`   | `address` | Whitelisted token address.                                          |
| `stem`    | `int96`   | The Stem of the Deposit.                                            |
| `amount`  | `uint256` | Token amount of the Deposit.                                        |
| `bdv`     | `uint256` | The BDV associated with `amount` of `token` at the time of Deposit. |

### [Remove Deposit](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/TokenSilo.sol#L62) <a href="#event-remove-deposit" id="event-remove-deposit"></a>

```solidity
event RemoveDeposit(
    address indexed account,
    address indexed token,
    int96 stem,
    uint256 amount,
    uint256 bdv
);
```

Emitted when `account` removes a single Deposit from the Silo. Occurs during Withdraw and Convert.

| Parameter | Type      | Description                           |
| --------- | --------- | ------------------------------------- |
| `account` | `address` | The Farmer whose Deposit was removed. |
| `token`   | `address` | Whitelisted token address.            |
| `stem`    | `int96`   | The Stem of the Deposit.              |
| `amount`  | `uint256` | The token amount of the Deposit.      |
| `bdv`     | `uint256` | The BDV associated with the Deposit.  |

### [Remove Deposits](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/TokenSilo.sol#L81) <a href="#event-remove-deposits" id="event-remove-deposits"></a>

```solidity
event RemoveDeposits(
    address indexed account,
    address indexed token,
    int96[] stems,
    uint256[] amounts,
    uint256 amount,
    uint256[] bdvs
);
```

Emitted when `account` removes multiple Deposits from the Silo. Occurs during Withdraw and Convert.

| Parameter | Type        | Description                                                                    |
| --------- | ----------- | ------------------------------------------------------------------------------ |
| `account` | `address`   | The Farmer whose Deposit was removed.                                          |
| `token`   | `address`   | Whitelisted token address.                                                     |
| `stems`   | `uint32[]`  | Stems of the Deposits.                                                         |
| `amounts` | `uint256[]` | The token amounts of the Deposits, corresponding to `stems`.                   |
| `amount`  | `uint256`   | Sum of `amounts`.                                                              |
| `bdvs`    | `uint256[]` | The BDVs associated with the Deposits, corresponding to `stems` and `amounts`. |

### [Transfer Single](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/TokenSilo.sol#L101) <a href="#event-remove-deposits" id="event-remove-deposits"></a>

```solidity
event TransferSingle(
    address indexed operator,
    address indexed from,
    address indexed to,
    uint256 id,
    uint256 value
);
```

ERC-1155 event. Emitted when a Deposit is created, removed, or transferred.

| Parameter  | Type      | Description                                        |
| ---------- | --------- | -------------------------------------------------- |
| `operator` | `address` | The address that performed the operation.          |
| `from`     | `address` | The address the Deposit is being transferred from. |
| `to`       | `address` | The address the Deposit is being transferred to.   |
| `id`       | `uint256` | The Deposit ID of the Deposit.                     |
| `value`    | `uint256` | The amount of the Deposit.                         |

### [Transfer Batch](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/TokenSilo.sol#L120) <a href="#event-remove-deposits" id="event-remove-deposits"></a>

```solidity
event TransferBatch(
    address indexed operator,
    address indexed from,
    address indexed to,
    uint256[] ids,
    uint256[] values
);
```

ERC-1155 event. Emitted when multiple deposits are withdrawn or transferred.

| Parameter  | Type        | Description                                        |
| ---------- | ----------- | -------------------------------------------------- |
| `operator` | `address`   | The address that performed the operation.          |
| `from`     | `address`   | The address the Deposit is being transferred from. |
| `to`       | `address`   | The address the Deposit is being transferred to.   |
| `ids`      | `uint256[]` | The Deposit IDs of the Deposits.                   |
| `values`   | `uint256[]` | The amounts of the Deposits.                       |

### [Remove Withdrawals](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/TokenSilo.sol#L47) <a href="#event-remove-withdrawals" id="event-remove-withdrawals"></a>

```solidity
event RemoveWithdrawals(
    address indexed account,
    address indexed token,
    uint32[] seasons,
    uint256 amount
);
```

Legacy event. This event is kept for backwards compatibility in order for the ABI to generate properly.

| Parameter | Type       | Description                          |
| --------- | ---------- | ------------------------------------ |
| `account` | `address`  | Farmer that claimed the Withdrawals. |
| `token`   | `address`  | Whitelisted token address.           |
| `seasons` | `uint32[]` | Seasons of claimed Withdrawn assets. |
| `amount`  | `uint256`  | Amount of claimed asset.             |

### [Remove Withdrawal](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/SiloFacet/TokenSilo.sol#L53) <a href="#event-remove-withdrawal" id="event-remove-withdrawal"></a>

```solidity
event RemoveWithdrawal(
    address indexed account,
    address indexed token,
    uint32 season,
    uint256 amount
);
```

Legacy event. This event is kept for backwards compatibility in order for the ABI to generate properly.

| Parameter | Type      | Description                         |
| --------- | --------- | ----------------------------------- |
| `account` | `address` | Farmer that claimed the Withdrawal. |
| `token`   | `address` | Whitelisted token address.          |
| `season`  | `uint32`  | Seasons of claimed Withdrawn asset. |
| `amount`  | `uint256` | Amount of claimed asset.            |
