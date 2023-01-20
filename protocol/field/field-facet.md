# Field Facet

Field sows Beans.

## Call Functions

### Sow

```solidity
function sow(uint256 amount, LibTransfer.From mode)
    external
    payable
    returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L33)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `amount`  | `uint256` | WIP         |
| `mode`    | `From`    | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

### Sow With Min

```solidity
function sowWithMin(
    uint256 amount,
    uint256 minAmount,
    LibTransfer.From mode
) public payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L41)

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `amount`    | `uint256` | WIP         |
| `minAmount` | `uint256` | WIP         |
| `mode`      | `From`    | WIP         |

### Harvest

```solidity
function harvest(uint256[] calldata plots, LibTransfer.To mode)
    external
    payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L67)

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `plots`   | `uint256[]` | WIP         |
| `mode`    | `To`        | WIP         |

## View Functions

### Pod Index

```solidity
function podIndex() public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L110)

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

### Harvestable Index

```solidity
function harvestableIndex() public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L114)

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

### Total Pods

```solidity
function totalPods() public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L118)

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

### Total Harvested

```solidity
function totalHarvested() public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L122)

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

### Total Harvestable

```solidity
function totalHarvestable() public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L126)

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

### Total Unharvestable

```solidity
function totalUnharvestable() public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L130)

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

### Plot

```solidity
function plot(address account, uint256 plotId)
    public
    view
    returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L134)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `plotId`  | `uint256` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

### Total Soil

```solidity    
function totalSoil() public view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L142)

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

## Events

### Sow

```solidity
event Sow(
    address indexed account,
    uint256 index,
    uint256 beans,
    uint256 pods
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L20)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `index`   | `uint256` | WIP         |
| `beans`   | `uint256` | WIP         |
| `pods`    | `uint256` | WIP         |

### Harvest

```solidity
event Harvest(address indexed account, uint256[] plots, uint256 beans);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L26)

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `account` | `address`   | WIP         |
| `plots`   | `uint256[]` | WIP         |
| `beans`   | `uint256`   | WIP         |

### Pod Listing Cancelled

```solidity
event PodListingCancelled(address indexed account, uint256 index);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L27)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `index`   | `uint256` | WIP         |
