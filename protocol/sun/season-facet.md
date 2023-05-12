# Season Facet

{% hint style="info" %}
This page has not been updated yet for BIP-34
{% endhint %}

The Season Facet contains the `sunrise` function and handles all logic for Season changes.

## Call Functions

### [Sunrise](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/SeasonFacet.sol#L27)

```solidity
function sunrise() external payable;
```

Advances Beanstalk to the next Season.

## View Functions

### [Season](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/SeasonFacet.sol#L41)

```solidity
function season() public view returns (uint32);
```

Returns the current Season number.

| Return Value | Description                |
| ------------ | -------------------------- |
| `uint256`    | The current Season number. |

### [Paused](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/SeasonFacet.sol#L45)

```solidity
function paused() public view returns (bool);
```

Returns whether Beanstalk is Paused. When Paused, `sunrise` cannot be called.

| Return Value | Description                  |
| ------------ | ---------------------------- |
| `bool`       | Whether Beanstalk is Paused. |

### [Time](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/SeasonFacet.sol#L49)

```solidity
function time() external view returns (Storage.Season memory);
```

Returns the Season struct.

| Return Value | Description                                                        |
| ------------ | ------------------------------------------------------------------ |
| `Season`     | The Season struct in [App Storage](../../overview/app-storage.md). |

### [Season Time](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/SeasonFacet.sol#L53)

```solidity
function seasonTime() public view virtual returns (uint32);
```

Returns the expected Season number given the current block timestamp. The `sunrise` function can be called when `seasonTime() > season()`.

| Return Value | Description                                                   |
| ------------ | ------------------------------------------------------------- |
| `uint32`     | The expected Season number given the current block timestamp. |

### [Weather](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Weather.sol#L32)

```solidity
function weather() public view returns (Storage.Weather memory);
```

Returns the Weather struct.

| Return Value | Description                                                                 |
| ------------ | --------------------------------------------------------------------------- |
| `Weather`    | Returns the Weather struct in [App Storage](../../overview/app-storage.md). |

### [Rain](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Weather.sol#L36)

```solidity
function rain() public view returns (Storage.Rain memory);
```

Returns the Rain struct.

| Return Value | Description                                                              |
| ------------ | ------------------------------------------------------------------------ |
| `Rain`       | Returns the Rain struct in [App Storage](../../overview/app-storage.md). |

### [Yield](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Weather.sol#L40)

```solidity
function yield() public view returns (uint32);
```

Returns the current Weather.

| Return Value | Description          |
| ------------ | -------------------- |
| `uint32`     | The current Weather. |

### [Plenty Per Root](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Weather.sol#L44)

```solidity
function plentyPerRoot(uint32 season) external view returns (uint256);
```

Returns the Season of Plenty (SOP) rewards per Root for the given Season.

| Parameter | Type     | Description                                   |
| --------- | -------- | --------------------------------------------- |
| `season`  | `uint32` | The Season to fetch SOP rewards per Root for. |

| Return Value | Description                           |
| ------------ | ------------------------------------- |
| `uint256`    | The SOP rewards for the given Season. |

### [Total deltaB](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Oracle.sol#L22)

```solidity
function totalDeltaB() external view returns (int256 deltaB);
```

Returns the cumulative deltaB across pools.

| Return Value | Type     | Description            |
| ------------ | -------- | ---------------------- |
| `deltaB`     | `int256` | The cumulative deltaB. |

### [Pool deltaB](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Oracle.sol#L26)

```solidity
function poolDeltaB(address pool) external view returns (int256 deltaB);
```

Returns the deltaB for a given pool.

| Parameter | Type      | Description               |
| --------- | --------- | ------------------------- |
| `pool`    | `address` | The address of the pool . |

| Return Value | Type     | Description                    |
| ------------ | -------- | ------------------------------ |
| `deltaB`     | `int256` | The deltaB for the given pool. |

## Events

### [Sunrise](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/SeasonFacet.sol#L19) <a href="#event-sunrise" id="event-sunrise"></a>

```solidity
event Sunrise(uint256 indexed season);
```

Emitted when the Season changes.

| Parameter | Type      | Description            |
| --------- | --------- | ---------------------- |
| `season`  | `uint256` | The new Season number. |

### [Incentivization](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/SeasonFacet.sol#L20) <a href="#event-incentivization" id="event-incentivization"></a>

```solidity
event Incentivization(address indexed account, uint256 beans);
```

Emitted when Beanstalk pays Beans to the `sunrise` caller.

| Parameter | Type      | Description                                      |
| --------- | --------- | ------------------------------------------------ |
| `account` | `address` | The address to which the reward Beans were sent. |
| `beans`   | `uint256` | The amount of Beans paid as a reward.            |

### [Reward](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Sun.sol#L23) <a href="#event-reward" id="event-reward"></a>

```solidity
event Reward(uint32 indexed season, uint256 toField, uint256 toSilo, uint256 toFertilizer);
```

Emitted during Sunrise when Beans are distributed to the Field, the Silo, and Fertilizer.

| Parameter      | Type      | Description                                            |
| -------------- | --------- | ------------------------------------------------------ |
| `season`       | `uint32`  | The Season in which Beans were distributed.            |
| `toField`      | `uint256` | The number of Beans distributed to the Field.          |
| `toSilo`       | `uint256` | The number of Beans distributed to the Silo.           |
| `toFertilizer` | `uint256` | The number of Beans distributed to Fertilizer holders. |

### [Soil](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Sun.sol#L24) <a href="#event-soil" id="event-soil"></a>

```solidity
event Soil(uint32 indexed season, uint256 soil);
```

Emitted during Sunrise when Beanstalk adjusts the amount of available Soil.

| Parameter | Type      | Description                            |
| --------- | --------- | -------------------------------------- |
| `season`  | `uint32`  | The Season in which Soil was adjusted. |
| `soil`    | `uint256` | The new amount of Soil available.      |

### [Weather Change](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Weather.sol#L21) <a href="#event-weather-change" id="event-weather-change"></a>

```solidity
event WeatherChange(uint256 indexed season, uint256 caseId, int8 change);
```

Emitted when the Weather (now [Temperature](../../misc/terminology-discrepancies.md)) changes.

| Parameter | Type      | Description                                                                                                                     |
| --------- | --------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `season`  | `uint256` | The current Season.                                                                                                             |
| `caseId`  | `uint256` | The "[Weather Case](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/init/InitDiamond.sol#L41)". |
| `change`  | `int8`    | The change in Temperature from the previous value.                                                                              |

### [Season of Plenty](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Weather.sol#L22) <a href="#event-season-of-plenty" id="event-season-of-plenty"></a>

```solidity
event SeasonOfPlenty(
    uint256 indexed season,
    uint256 amount,
    uint256 toField
);
```

Emitted when Beans are minted during the Season of Plenty.

| Parameter | Type      | Description                                                                |
| --------- | --------- | -------------------------------------------------------------------------- |
| `season`  | `uint256` | The Season in which Beans were minted for distribution.                    |
| `amount`  | `uint256` | The amount of 3CRV which was received for swapping Beans.                  |
| `toField` | `uint256` | The amount of Beans which were distributed to remaining Pods in the Field. |

### [Metapool Oracle](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/SeasonFacet/Oracle.sol#L20) <a href="#event-metapool-oracle" id="event-metapool-oracle"></a>

```solidity
event MetapoolOracle(uint32 indexed season, int256 deltaB, uint256[2] balances);
```

Emitted when deltaB is calculated at `sunrise`.

| Parameter  | Type         | Description                             |
| ---------- | ------------ | --------------------------------------- |
| `season`   | `uint32`     | The current Season.                     |
| `deltaB`   | `int256`     | The cumulative deltaB.                  |
| `balances` | `uint256[2]` | An array of token balances in the pool. |
