# Fertilizer Facet

Handles Sprouting Beans from Sprout Tokens.

## Call Functions

### Claim Fertilized Beans

```solidity
function claimFertilized(uint256[] calldata ids, LibTransfer.To mode)
    external
    payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L32)

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `ids`     | `uint256[]` | WIP         |
| `mode`    | `To`        | WIP         |

### Mint Fertilizer

```solidity
function mintFertilizer(
    uint128 amount,
    uint256 minLP,
    LibTransfer.From mode
) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L40)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `amount`  | `uint128` | WIP         |
| `minLP`   | `uint256` | WIP         |
| `mode`    | `From`    | WIP         |

### Add Fertilizer Owner

```solidity
function addFertilizerOwner(
    uint128 id,
    uint128 amount,
    uint256 minLP
) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L61)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `id`      | `uint128` | WIP         |
| `amount`  | `uint128` | WIP         |
| `minLP`   | `uint256` | WIP         |

### Pay Fertilizer

```solidity
function payFertilizer(address account, uint256 amount) external payable
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L75)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `amount`  | `uint256` | WIP         |

## View Functions

### Total Fertilized Beans

```solidity
function totalFertilizedBeans() external view returns (uint256 beans);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L85)

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `beans`      | `uint256` | WIP         |

### Total Unfertilized Beans

```solidity
function totalUnfertilizedBeans() external view returns (uint256 beans);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L89)

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `beans`      | `uint256` | WIP         |

### Total Fertilizer Beans

```solidity
function totalFertilizerBeans() external view returns (uint256 beans);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L93)

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `beans`      | `uint256` | WIP         |

### Get Fertilizer

```solidity
function getFertilizer(uint128 id) external view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L97)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `id`      | `uint128` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

### Get Next

```solidity
function getNext(uint128 id) external view returns (uint128);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L101)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `id`      | `uint128` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint128`    | WIP         |

### Get First

```solidity
function getFirst() external view returns (uint128);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L105)

| Return Value | Description |
|--------------|-------------|
| `uint128`    | WIP         |

### Get Last

```solidity
function getLast() external view returns (uint128);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L109)

| Return Value | Description |
|--------------|-------------|
| `uint128`    | WIP         |

### Get Active Fertilizer

```solidity
function getActiveFertilizer() external view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L113)

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

### Is Fertilizing

```solidity
function isFertilizing() external view returns (bool);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L117)

| Return Value | Description |
|--------------|-------------|
| `bool`       | WIP         |

### Beans Per Fertilizer

```solidity
function beansPerFertilizer() external view returns (uint128 bpf);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L121)

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `bpf`        | `uint128` | WIP         |

### Get Humidity

```solidity
function getHumidity(uint128 _s) external pure returns (uint128 humidity);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L125)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `_s`      | `uint128` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `humidity`   | `uint128` | WIP         |

### Get Current Humidity

```solidity
function getCurrentHumidity() external view returns (uint128 humidity);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L129)

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `humidity`   | `uint128` | WIP         |

### Get End Bpf

```solidity
function getEndBpf() external view returns (uint128 endBpf);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L133)

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `endBpf`     | `uint128` | WIP         |

### Remaining Recapitalization

```solidity
function remainingRecapitalization() external view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L137)

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

### Balance of Unfertilized

```solidity
function balanceOfUnfertilized(address account, uint256[] memory ids)
    external
    view
    returns (uint256 beans);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L141)

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `account` | `address`   | WIP         |
| `ids`     | `uint256[]` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `beans`      | `uint256` | WIP         |

### Balance of Fertilized

```solidity
function balanceOfFertilized(address account, uint256[] memory ids)
    external
    view
    returns (uint256 beans);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L149)

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `account` | `address`   | WIP         |
| `ids`     | `uint256[]` | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `beans`      | `uint256` | WIP         |

### Balance of Fertilizer

```solidity
function balanceOfFertilizer(address account, uint256 id)
    external
    view
    returns (IFertilizer.Balance memory);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L157)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `id`      | `uint256` | WIP         |

| Return Value          | Description |
|-----------------------|-------------|
| `IFertilizer.Balance` | WIP         |

### Balance of Batch Fertilizer

```solidity
function balanceOfBatchFertilizer(
    address[] memory accounts,
    uint256[] memory ids
) external view returns (IFertilizer.Balance[] memory);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L165)

| Parameter  | Type        | Description |
|------------|-------------|-------------|
| `accounts` | `address[]` | WIP         |
| `ids`      | `uint256[]` | WIP         |

| Return Value            | Description |
|-------------------------|-------------|
| `IFertilizer.Balance[]` | WIP         |

### Get Fertilizers

```solidity
function getFertilizers()
    external
    view
    returns (Supply[] memory fertilizers);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L172)

| Return Value  | Type       | Description |
|---------------|------------|-------------|
| `fertilizers` | `Supply[]` | WIP         |

## Events

### Set Fertilizer

```solidity
event SetFertilizer(uint128 id, uint128 bpf);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L23)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `id`      | `uint128` | WIP         |
| `bpf`     | `uint128` | WIP         |
