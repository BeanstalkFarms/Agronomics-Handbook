# Season Facet

{% hint style="warning" %}
Note that this page has not been updated to reflect the current state of Beanstalk, but is left here as a reference.
{% endhint %}

The Season Facet contains the `gm` function and handles all logic for Season changes.

## Call Functions

### [Sunrise](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/SeasonFacet.sol#L37)

```solidity
function sunrise() external payable returns (uint256);
```

Advances Beanstalk to the next Season, sending reward Beans to the caller's Circulating balance.

| Return Type | Description                               |
| ----------- | ----------------------------------------- |
| `uint256`   | The number of Beans minted to the caller. |

### [GM](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/SeasonFacet.sol#L47)

```solidity
function gm(
    address account,
    LibTransfer.To mode
) public payable returns (uint256);
```

Advances Beanstalk to the next Season, sending reward Beans to a specified address and balance.

| Parameter | Type      | Description                                                                                    |
| --------- | --------- | ---------------------------------------------------------------------------------------------- |
| `account` | `address` | Indicates to which address reward Beans should be sent.                                        |
| `mode`    | `To`      | The balance to transfer Beans to; see [`LibTransfer.To`](../../overview/internal-balances.md). |

| Return Type | Description                               |
| ----------- | ----------------------------------------- |
| `uint256`   | The number of Beans minted to the caller. |

## View Functions

### [Season](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/SeasonFacet.sol#L69)

```solidity
function season() public view returns (uint32);
```

Returns the current Season number.

| Return Type | Description                |
| ----------- | -------------------------- |
| `uint32`    | The current Season number. |

### [Paused](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/SeasonFacet.sol#L76)

```solidity
function paused() public view returns (bool);
```

Returns whether Beanstalk is Paused. When Paused, `sunrise` cannot be called.

| Return Type | Description                  |
| ----------- | ---------------------------- |
| `bool`      | Whether Beanstalk is Paused. |

### [Time](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/SeasonFacet.sol#L83)

```solidity
function time() external view returns (Storage.Season memory);
```

Returns the Season struct.

| Return Type | Description                                                        |
| ----------- | ------------------------------------------------------------------ |
| `Season`    | The Season struct in [App Storage](../../overview/app-storage.md). |

### [Above Peg](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/SeasonFacet.sol#L90)

```solidity
function abovePeg() external view returns (bool);
```

Returns whether Beanstalk started this Season above or below peg.

| Return Type | Description                                               |
| ----------- | --------------------------------------------------------- |
| `bool`      | Whether Beanstalk started this Season above or below peg. |

### [Sunrise Block](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/SeasonFacet.sol#L97)

```solidity
function sunriseBlock() external view returns (uint32);
```

Returns the block during which the current Season started.

| Return Type | Description                                        |
| ----------- | -------------------------------------------------- |
| `uint32`    | The block during which the current Season started. |

### [Season Time](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/SeasonFacet.sol#L105)

```solidity
function seasonTime() public view virtual returns (uint32);
```

Returns the expected Season number given the current block timestamp. The `sunrise` function can be called when `seasonTime() > season()`.

| Return Type | Description                                                   |
| ----------- | ------------------------------------------------------------- |
| `uint32`    | The expected Season number given the current block timestamp. |

### [Weather](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/Weather.sol#L75)

```solidity
function weather() public view returns (Storage.Weather memory);
```

Returns the Weather struct.

| Return Type | Description                                                                 |
| ----------- | --------------------------------------------------------------------------- |
| `Weather`   | Returns the Weather struct in [App Storage](../../overview/app-storage.md). |

### [Rain](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/Weather.sol#L82)

```solidity
function rain() public view returns (Storage.Rain memory);
```

Returns the Rain struct.

| Return Type | Description                                                              |
| ----------- | ------------------------------------------------------------------------ |
| `Rain`      | Returns the Rain struct in [App Storage](../../overview/app-storage.md). |

### [Plenty Per Root](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/Weather.sol#L89)

```solidity
function plentyPerRoot(uint32 season) external view returns (uint256);
```

Returns the Season of Plenty (SOP) rewards per Root for the given Season.

| Parameter | Type     | Description                                   |
| --------- | -------- | --------------------------------------------- |
| `season`  | `uint32` | The Season to fetch SOP rewards per Root for. |

| Return Type | Description                           |
| ----------- | ------------------------------------- |
| `uint256`   | The SOP rewards for the given Season. |

### [Total deltaB](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/Oracle.sol#L28)

```solidity
function totalDeltaB() external view returns (int256 deltaB);
```

Returns the cumulative deltaB across all pools on the Oracle Whitelist.

| Return Value | Type     | Description            |
| ------------ | -------- | ---------------------- |
| `deltaB`     | `int256` | The cumulative deltaB. |

### [Pool deltaB](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/Oracle.sol#L35)

```solidity
function poolDeltaB(address pool) external view returns (int256);
```

Returns the deltaB for a given pool.

| Parameter | Type      | Description               |
| --------- | --------- | ------------------------- |
| `pool`    | `address` | The address of the pool . |

| Return Value | Description                    |
| ------------ | ------------------------------ |
| `int256`     | The deltaB for the given pool. |

### [Well Oracle Snapshot](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/Oracle.sol#L55)

```solidity
function wellOracleSnapshot(address well) external view returns (bytes memory snapshot);
```

Returns the last Well oracle snapshot for a given Well.

| Parameter | Type      | Description                                      |
| --------- | --------- | ------------------------------------------------ |
| `well`    | `address` | The address of the pool to get the snapshot for. |

<table><thead><tr><th>Type</th><th data-hidden>Description</th><th data-hidden>Return Value</th></tr></thead><tbody><tr><td><code>int256</code></td><td>The last Curve oracle snapshot for <code>well</code>.</td><td><code>snapshot</code></td></tr></tbody></table>

### [Curve Oracle](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/Oracle.sol#L63)

```solidity
function curveOracle() external view returns (Storage.CurveMetapoolOracle memory co);
```

Returns the last Curve oracle data snapshot for the BEAN:3CRV pool.

<table><thead><tr><th>Return Value</th><th>Type</th><th>Description</th><th data-hidden>Description</th><th data-hidden>Return Value</th></tr></thead><tbody><tr><td><code>co</code></td><td><code>Storage.CurveMetapoolOracle</code></td><td>Last Curve oracle data snapshot.</td><td>The deltaB for the given pool.</td><td><code>co</code></td></tr></tbody></table>

## Events

### [Sunrise](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/SeasonFacet.sol#L22) <a href="#event-sunrise" id="event-sunrise"></a>

```solidity
event Sunrise(uint256 indexed season);
```

Emitted when the Season changes.

| Parameter | Type      | Description            |
| --------- | --------- | ---------------------- |
| `season`  | `uint256` | The new Season number. |

### [Incentivization](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/SeasonFacet.sol#L29) <a href="#event-incentivization" id="event-incentivization"></a>

```solidity
event Incentivization(address indexed account, uint256 beans);
```

Emitted when Beanstalk pays Beans to the `sunrise` caller.

| Parameter | Type      | Description                                      |
| --------- | --------- | ------------------------------------------------ |
| `account` | `address` | The address to which the reward Beans were sent. |
| `beans`   | `uint256` | The amount of Beans paid as a reward.            |

### [Reward](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/Sun.sol#L43) <a href="#event-reward" id="event-reward"></a>

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

### [Soil](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/Sun.sol#L55) <a href="#event-soil" id="event-soil"></a>

```solidity
event Soil(uint32 indexed season, uint256 soil);
```

Emitted during Sunrise when Beanstalk adjusts the amount of available Soil.

| Parameter | Type      | Description                            |
| --------- | --------- | -------------------------------------- |
| `season`  | `uint32`  | The Season in which Soil was adjusted. |
| `soil`    | `uint256` | The new amount of Soil available.      |

### [Weather Change](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/Weather.sol#L51) <a href="#event-weather-change" id="event-weather-change"></a>

```solidity
event WeatherChange(uint256 indexed season, uint256 caseId, int8 change);
```

Emitted when the Weather (now [Temperature](../../misc/terminology-discrepancies.md)) changes.

| Parameter | Type      | Description                                                                                                                     |
| --------- | --------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `season`  | `uint256` | The current Season.                                                                                                             |
| `caseId`  | `uint256` | The "[Weather Case](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/init/InitDiamond.sol#L41)". |
| `change`  | `int8`    | The change in Temperature from the previous value.                                                                              |

### [Season of Plenty](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/sun/SeasonFacet/Weather.sol#L63) <a href="#event-season-of-plenty" id="event-season-of-plenty"></a>

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
