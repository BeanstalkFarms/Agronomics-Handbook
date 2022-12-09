# Season Facet

## Call Functions <a href="#call-functions" id="call-functions"></a>

### Sunrise <a href="#sunrise" id="sunrise"></a>

```solidity
function sunrise() external;
```

`sunrise` advances Beanstalk to the next Season. It can only be called if:

* Beanstalk is not Paused; and
* The number of Seasons that have occurred is less than the number of hours that have elapsed since Beanstalk was deployed (excluding time spent Paused).

## View Functions <a href="#view-functions" id="view-functions"></a>

```solidity
/**
 * SeasonFacet
 **/

function season() public view returns (uint32);

function paused() public view returns (bool);

function time() external view returns (Storage.Season memory);

function seasonTime() public view virtual returns (uint32);

/**
 * Weather
 **/
 
function weather() public view returns (Storage.Weather memory);

function rain() public view returns (Storage.Rain memory);

function yield() public view returns (uint32);

function plentyPerRoot(uint32 season) external view returns (uint256);

/**
 * Oracle
 **/
 
function totalDeltaB() external view returns (int256 deltaB);

function poolDeltaB(address pool) external view returns (int256 deltaB);
```

## Events <a href="#events" id="events"></a>

```solidity
/**
 * SeasonFacet
 **/

event Sunrise(uint256 indexed season);

event Incentivization(address indexed account, uint256 beans);

/**
 * Sun
 **/

event Reward(uint32 indexed season, uint256 toField, uint256 toSilo, uint256 toFertilizer);

event Soil(uint32 indexed season, uint256 soil);

/**
 * Weather
 **/

event WeatherChange(uint256 indexed season, uint256 caseId, int8 change);

event SeasonOfPlenty(
    uint256 indexed season,
    uint256 amount,
    uint256 toField
);

/**
 * Oracle
 **/
 
event MetapoolOracle(uint32 indexed season, int256 deltaB, uint256[2] balances);
```
