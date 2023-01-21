# Season Facet

Season Facet holds the Sunrise function and handles all logic for Season changes.

## Call Functions

### Sunrise

```solidity
function sunrise() external;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/SeasonFacet.sol#L27)

`sunrise` advances Beanstalk to the next Season. It can only be called if:

* Beanstalk is not Paused; and
* The number of Seasons that have occurred is less than the number of hours that have elapsed since Beanstalk was deployed (excluding time spent Paused).

## View Functions

### SeasonFacet.sol

### Season

```solidity
function season() public view returns (uint32);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/SeasonFacet.sol#L41)

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

### Paused

```solidity
function paused() public view returns (bool);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/SeasonFacet.sol#L45)

| Return Value | Description |
|--------------|-------------|
| `bool`       | WIP         |

### Time

```solidity
function time() external view returns (Storage.Season memory);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/SeasonFacet.sol#L49)

| Return Value | Description |
|--------------|-------------|
| `Season`     | WIP         |

### Season Time

```solidity
function seasonTime() public view virtual returns (uint32);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/SeasonFacet.sol#L53)

| Return Value | Description |
|--------------|-------------|
| `uint32`     | WIP         |

### Weather.sol

### Weather

```solidity 
function weather() public view returns (Storage.Weather memory);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Weather.sol#L32)

| Return Value | Description |
|--------------|-------------|
| `Weather`    | WIP         |

### Rain

```solidity
function rain() public view returns (Storage.Rain memory);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Weather.sol#L36)

| Return Value | Description |
|--------------|-------------|
| `Rain`       | WIP         |

### Yield

```solidity
function yield() public view returns (uint32);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Weather.sol#L40)

| Return Value | Description |
|--------------|-------------|
| `uint32`     | WIP         |

### Plenty Per Root

```solidity
function plentyPerRoot(uint32 season) external view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Weather.sol#L44)

| Parameter | Type     | Description |
|-----------|----------|-------------|
| `season`  | `uint32` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

### Oracle.sol

### Total DeltaB
 
```solidity
function totalDeltaB() external view returns (int256 deltaB);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Oracle.sol#L22)

| Return Value | Type     | Description |
|--------------|----------|-------------|
| `deltaB`     | `int256` | WIP         |

### Pool DeltaB

```solidity
function poolDeltaB(address pool) external view returns (int256 deltaB);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Oracle.sol#L26)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `pool`    | `address` | WIP         |

| Return Value | Type     | Description |
|--------------|----------|-------------|
| `deltaB`     | `int256` | WIP         |

## Events

### SeasonFacet.sol

### Sunrise

```solidity
event Sunrise(uint256 indexed season);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/SeasonFacet.sol#L19)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `season`  | `uint256` | WIP         |

### Incentivization

```solidity
event Incentivization(address indexed account, uint256 beans);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/SeasonFacet.sol#L20)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `beans`   | `uint256` | WIP         |

### Sun.sol

### Reward

```solidity
event Reward(uint32 indexed season, uint256 toField, uint256 toSilo, uint256 toFertilizer);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Sun.sol#L23)

| Parameter      | Type      | Description |
|----------------|-----------|-------------|
| `season`       | `uint32`  | WIP         |
| `toField`      | `uint256` | WIP         |
| `toSilo`       | `uint256` | WIP         |
| `toFertilizer` | `uint256` | WIP         |

### Soil

```solidity
event Soil(uint32 indexed season, uint256 soil);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Sun.sol#L24)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `season`  | `uint32`  | WIP         |
| `soil`    | `uint256` | WIP         |

### Weather.sol

### Weather Change

```solidity
event WeatherChange(uint256 indexed season, uint256 caseId, int8 change);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Weather.sol#L21)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `season`  | `uint256` | WIP         |
| `caseId`  | `uint256` | WIP         |
| `change`  | `int8`    | WIP         |

### Season Of Plenty

```solidity
event SeasonOfPlenty(
    uint256 indexed season,
    uint256 amount,
    uint256 toField
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Weather.sol#L22)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `season`  | `uint256` | WIP         |
| `amount`  | `uint256` | WIP         |
| `toField` | `uint256` | WIP         |

### Oracle.sol
 
### Metapool Oracle
 
```solidity
event MetapoolOracle(uint32 indexed season, int256 deltaB, uint256[2] balances);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Oracle.sol#L20)

| Parameter  | Type         | Description |
|------------|--------------|-------------|
| `season`   | `uint32`     | WIP         |
| `deltaB`   | `int256`     | WIP         |
| `balances` | `uint256[2]` | WIP         |
