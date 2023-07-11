# Fundraiser Facet

The Fundraiser Facet dandles the creation, funding, and completion of [Fundraisers](https://docs.bean.money/almanac/protocol/fundraiser).

## Call Functions

### [Fund](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FundraiserFacet.sol#L105)

```solidity
function fund(
    uint32 id,
    uint256 amount,
    LibTransfer.From mode
) external payable nonReentrant returns (uint256);
```

Fund a Fundraiser in exchange for Pods.

| Parameter | Type      | Description                                                                                  |
| --------- | --------- | -------------------------------------------------------------------------------------------- |
| `id`      | `uint32`  | The Fundraiser ID.                                                                           |
| `amount`  | `uint256` | Amount of `fundraisers[id].token` to provide.                                                |
| `mode`    | `From`    | Balance to spend tokens from; see [`LibTransfer.From`](../../overview/internal-balances.md). |

| Return Type | Description                  |
| ----------- | ---------------------------- |
| `uint256`   | The number of Pods received. |

### [Create Fundraiser](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FundraiserFacet.sol#L66)

```solidity
function createFundraiser(
    address payee,
    address token,
    uint256 amount
) external payable;
```

Creates a Fundraiser. Can only be called by the owner of Beanstalk.

| Parameter | Type      | Description                                                                       |
| --------- | --------- | --------------------------------------------------------------------------------- |
| `payee`   | `address` | The address to which funds are delivered at the end of the Fundraiser.            |
| `token`   | `address` | The address of the token that can be sent to the Fundraiser in exchange for Pods. |
| `amount`  | `uint256` | The amount of `token` that is being raised.                                       |

## View Functions

### [Remaining Funding](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FundraiserFacet.sol#L169)

```solidity
function remainingFunding(uint32 id) public view returns (uint256);
```

Returns the remaining number of tokens to raise.

| Parameter | Type     | Description        |
| --------- | -------- | ------------------ |
| `id`      | `uint32` | The Fundraiser ID. |

| Return Type | Description                              |
| ----------- | ---------------------------------------- |
| `uint256`   | The remaining number of tokens to raise. |

### [Total Funding](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FundraiserFacet.sol#L173)

```solidity
function totalFunding(uint32 id) public view returns (uint256);
```

Returns the total amount of tokens raised so far.

| Parameter | Type     | Description        |
| --------- | -------- | ------------------ |
| `id`      | `uint32` | The Fundraiser ID. |

| Return Type | Description                               |
| ----------- | ----------------------------------------- |
| `uint256`   | The total amount of tokens raised so far. |

### [Funding Token](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FundraiserFacet.sol#L177)

```solidity
function fundingToken(uint32 id) public view returns (address);
```

Returns the address of the token that can be sent to the Fundraiser.

| Parameter | Type     | Description        |
| --------- | -------- | ------------------ |
| `id`      | `uint32` | The Fundraiser ID. |

| Return Type | Description                                                  |
| ----------- | ------------------------------------------------------------ |
| `address`   | The address of the token that can be sent to the Fundraiser. |

### [Fundraiser](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FundraiserFacet.sol#L181)

```solidity
function fundraiser(uint32 id)
    public
    view
    returns (Storage.Fundraiser memory);
```

Returns the Fundraiser struct.

| Parameter | Type     | Description        |
| --------- | -------- | ------------------ |
| `id`      | `uint32` | The Fundraiser ID. |

| Return Type  | Description                                                                    |
| ------------ | ------------------------------------------------------------------------------ |
| `Fundraiser` | Returns the Fundraiser struct in [App Storage](../../overview/app-storage.md). |

### [Number Of Fundraisers](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FundraiserFacet.sol#L189)

```solidity
function numberOfFundraisers() public view returns (uint32);
```

Returns the number of Fundraisers.

| Return Type | Description                |
| ----------- | -------------------------- |
| `uint32`    | The number of Fundraisers. |

## Events

### [Create Fundraiser](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FundraiserFacet.sol#L33) <a href="#event-create-fundraiser" id="event-create-fundraiser"></a>

```solidity
event CreateFundraiser(
    uint32 indexed id,
    address fundraiser,
    address token,
    uint256 amount
);
```

Emitted when a Fundraiser is created.

| Parameter    | Type      | Description                                                                       |
| ------------ | --------- | --------------------------------------------------------------------------------- |
| `id`         | `uint32`  | The Fundraiser ID.                                                                |
| `fundraiser` | `address` | The address to which funds are delivered.                                         |
| `token`      | `address` | The address of the token that can be sent to the Fundraiser in exchange for Pods. |
| `amount`     | `uint256` | The amount of `token` that is being raised.                                       |

### [Fund Fundraiser](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FundraiserFacet.sol#L46) <a href="#event-fund-fundraiser" id="event-fund-fundraiser"></a>

```solidity
event FundFundraiser(
    address indexed account,
    uint32 indexed id,
    uint256 amount
);
```

Emitted when a Farmer calls `fund`.

| Parameter | Type      | Description                                    |
| --------- | --------- | ---------------------------------------------- |
| `account` | `address` | The address of the Farmer.                     |
| `id`      | `uint32`  | The Fundraiser ID.                             |
| `amount`  | `uint256` | The amount of `token` that `account` provided. |

### [Complete Fundraiser](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FundraiserFacet.sol#L56) <a href="#event-complete-fundraiser" id="event-complete-fundraiser"></a>

```solidity
event CompleteFundraiser(uint32 indexed id);
```

Emitted when a Fundraiser is fully funded.

| Parameter | Type     | Description        |
| --------- | -------- | ------------------ |
| `id`      | `uint32` | The Fundraiser ID. |
