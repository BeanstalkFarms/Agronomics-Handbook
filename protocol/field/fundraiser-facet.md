# Fundraiser Facet

## Call Functions

### Fund

```solidity
function fund(
    uint32 id,
    uint256 amount,
    LibTransfer.From mode
) external payable nonReentrant returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FundraiserFacet.sol#L40)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `id`      | `uint32`  | WIP         |
| `amount`  | `uint256` | WIP         |
| `mode`    | `From`    | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

### Create Fundraiser

```solidity
function createFundraiser(
    address payee,
    address token,
    uint256 amount
) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FundraiserFacet.sol#L74)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `payee`   | `address` | WIP         |
| `token`   | `address` | WIP         |
| `amount`  | `uint256` | WIP         |

## View Functions

### Remaining Funding

```solidity
function remainingFunding(uint32 id) public view returns (uint256);
}
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FundraiserFacet.sol#L95)

| Parameter | Type     | Description |
|-----------|----------|-------------|
| `id`      | `uint32` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

### Total Funding

```solidity
function totalFunding(uint32 id) public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FundraiserFacet.sol#L99)

| Parameter | Type     | Description |
|-----------|----------|-------------|
| `id`      | `uint32` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

### Funding Token

```solidity
function fundingToken(uint32 id) public view returns (address);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FundraiserFacet.sol#L103)

| Parameter | Type     | Description |
|-----------|----------|-------------|
| `id`      | `uint32` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `address`    | WIP         |

### Fundraiser

```solidity
function fundraiser(uint32 id)
    public
    view
    returns (Storage.Fundraiser memory);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FundraiserFacet.sol#L107)

| Parameter | Type     | Description |
|-----------|----------|-------------|
| `id`      | `uint32` | WIP         |

| Return Value | Type                 | Description |
|--------------|----------------------|-------------|
| `memory`     | `Storage.Fundraiser` | WIP         |

### Number Of Fundraisers

```solidity
function numberOfFundraisers() public view returns (uint32);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FundraiserFacet.sol#L115)

| Return Value | Description |
|--------------|-------------|
| `uint32`     | WIP         |

## Events

### Create Fundraiser

```solidity
event CreateFundraiser(
    uint32 indexed id,
    address fundraiser,
    address token,
    uint256 amount
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FundraiserFacet.sol#L23)

| Parameter    | Type      | Description |
|--------------|-----------|-------------|
| `id`         | `uint32`  | WIP         |
| `fundraiser` | `address` | WIP         |
| `token`      | `address` | WIP         |
| `amount`     | `uint256` | WIP         |

### Fund Fundraiser

```solidity
event FundFundraiser(
    address indexed account,
    uint32 indexed id,
    uint256 amount
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FundraiserFacet.sol#L29)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `id`      | `uint32`  | WIP         |
| `amount`  | `uint256` | WIP         |

### Complete Fundraiser

```solidity
event CompleteFundraiser(uint32 indexed id);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FundraiserFacet.sol#L34)

| Parameter | Type     | Description |
|-----------|----------|-------------|
| `id`      | `uint32` | WIP         |
