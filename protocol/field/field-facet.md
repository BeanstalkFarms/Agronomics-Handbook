# Field Facet

Field sows Beans.

## Call Functions

### [Sow](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L82)

```solidity
function sow(
    uint256 beans,
    uint256 minTemperature,
    LibTransfer.From mode
)
    external
    payable
    returns (uint256 pods)
```

Sow Beans in exchange for Pods.

| Parameter        | Type      | Description                                                                                        |
|------------------|-----------|----------------------------------------------------------------------------------------------------|
| `beans`          | `uint256` | The number of Beans to Sow.                                                                        |
| `minTemperature` | `uint256` | The minimum Temperature at which to Sow.                                                           |
| `mode`           | `From`    | The balance to transfer Beans from; see [`LibTransfer.From`](../../overview/internal-balances.md). |

| Return Value | Type      | Description                  |
|--------------|-----------|------------------------------|
| `pods`       | `uint256` | The number of Pods received. |

### [Sow With Min](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L103)

```solidity
    function sowWithMin(
        uint256 beans,
        uint256 minTemperature,
        uint256 minSoil,
        LibTransfer.From mode
    ) public payable returns (uint256 pods)
```

Sow Beans in exchange for Pods. Use at least `minSoil`.

| Parameter        | Type      | Description                                                                                               |
|------------------|-----------|-----------------------------------------------------------------------------------------------------------|
| `beans`          | `uint256` | The number of Beans to Sow.                                                                               |
| `minTemperature` | `uint256` | The minimum Temperature at which to Sow.                                                                  |
| `minSoil`        | `uint256` | The minimum amount of Soil to use; reverts if there is less than this much Soil available upon execution. |
| `mode`           | `From`    | The balance to transfer Beans from; see [`LibTransfer.From`](../../overview/internal-balances.md).        |

| Return Value | Type      | Description                  |
|--------------|-----------|------------------------------|
| `pods`       | `uint256` | The number of Pods received. |

### [Harvest](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L163)

```solidity
function harvest(uint256[] calldata plots, LibTransfer.To mode)
    external
    payable;
```

Harvest Pods from the Field.

| Parameter | Type        | Description                                                                                    |
|-----------|-------------|------------------------------------------------------------------------------------------------|
| `plots`   | `uint256[]` | List of plot IDs to Harvest.                                                                   |
| `mode`    | `To`        | The balance to transfer Beans to; see [`LibTransfer.To`](../../overview/internal-balances.md). |

## View Functions

### [Pod Index](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L232)

```solidity
function podIndex() public view returns (uint256);
```

Returns the total number of Pods ever minted.

| Return Value | Description                           |
|--------------|---------------------------------------|
| `uint256`    | The total number of Pods ever minted. |

### [Harvestable Index](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L239)

```solidity
function harvestableIndex() public view returns (uint256);
```

Returns the index below which Pods are Harvestable.

| Return Value | Description                                 |
|--------------|---------------------------------------------|
| `uint256`    | The index below which Pods are Harvestable. |

### [Total Pods](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L247)

```solidity
function totalPods() public view returns (uint256);
```

Returns the number of outstanding Pods. Includes Pods that are currently Harvestable but have not yet been Harvested.

| Return Value | Description                     |
|--------------|---------------------------------|
| `uint256`    | The number of outstanding Pods. |

### [Total Harvested](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L254)

```solidity
function totalHarvested() public view returns (uint256);
```

Returns the number of Pods that have ever been Harvested.

| Return Value | Description                                       |
|--------------|---------------------------------------------------|
| `uint256`    | The number of Pods that have ever been Harvested. |

### [Total Harvestable](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L264)

```solidity
function totalHarvestable() public view returns (uint256);
```

Returns the number of Pods that are currently Harvestable but have not yet been Harvested.

| Return Value | Description                                                                        |
|--------------|------------------------------------------------------------------------------------|
| `uint256`    | The number of Pods that are currently Harvestable but have not yet been Harvested. |

### [Total Unharvestable](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L271)

```solidity
function totalUnharvestable() public view returns (uint256);
```

Returns the number of Pods that are not yet Harvestable.

| Return Value | Description                                      |
|--------------|--------------------------------------------------|
| `uint256`    | The number of Pods that are not yet Harvestable. |

### [Plot](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L279)

```solidity
function plot(address account, uint256 index)
    public
    view
    returns (uint256);
```

Returns the number of Pods remaining in a Plot.

| Parameter | Type      | Description                   |
|-----------|-----------|-------------------------------|
| `account` | `address` | The account that owns a Plot. |
| `index`   | `uint256` | The ID of a Plot.             |

| Return Value | Description                             |
|--------------|-----------------------------------------|
| `uint256`    | The number of Pods remaining in a Plot. |

### [Total Soil](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L324)

```solidity    
function totalSoil() external view returns (uint256);
```

Returns the total available Soil.

| Return Value | Description               |
|--------------|---------------------------|
| `uint256`    | The total available Soil. |

### [Yield](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L346)

```solidity
function yield() external view returns (uint32);
```

Returns the current yield (aka "Temperature") offered by Beanstalk when burning Beans in exchange for Pods.

| Return Value | Description                                                                     |
|--------------|---------------------------------------------------------------------------------|
| `uint32`     | The current yield offered by Beanstalk when burning Beans in exchange for Pods. |

### [Temperature](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L356)

```solidity
function temperature() external view returns (uint256);
```

Returns the current Temperature, the interest rate offered by Beanstalk.

| Return Value | Description                                                      |
|--------------|------------------------------------------------------------------|
| `uint256`    | The current Temperature, the interest rate offered by Beanstalk. |

### [Max Temperature](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L366)

```solidity
function maxTemperature() external view returns (uint256);
```

Returns the max Temperature that Beanstalk is willing to offer this Season.

| Return Value | Description                                                         |
|--------------|---------------------------------------------------------------------|
| `uint256`    | The max Temperature that Beanstalk is willing to offer this Season. |

### [Remaining Pods](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L375)

```solidity
function remainingPods() external view returns (uint256);
```

Returns the remaining Pods that could be issued this Season.

| Return Value | Description                                          |
|--------------|------------------------------------------------------|
| `uint256`    | The remaining Pods that could be issued this Season. |

## Events

### [Sow](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L37) <a href="#event-sow" id="event-sow"></a>

```solidity
event Sow(
    address indexed account,
    uint256 index,
    uint256 beans,
    uint256 pods
);
```

Emitted from `LibDibbler.sowNoSoil` when an `account` creates a Plot. A Plot is a set of Pods created in from a single `sow` or `fund` call. 

| Parameter | Type      | Description                                         |
|-----------|-----------|-----------------------------------------------------|
| `account` | `address` | The account that sowed Beans for Pods.              |
| `index`   | `uint256` | The place in line of the Plot.                      |
| `beans`   | `uint256` | The amount of Beans burnt to create the Plot.       |
| `pods`    | `uint256` | The amount of Pods assocated with the created Plot. |

### [Harvest](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L50) <a href="#event-harvest" id="event-harvest"></a>

```solidity
event Harvest(address indexed account, uint256[] plots, uint256 beans);
```

Emitted when `account` claims the Beans associated with Harvestable Pods.

| Parameter | Type        | Description                                   |
|-----------|-------------|-----------------------------------------------|
| `account` | `address`   | The account that owns the `plots`.            |
| `plots`   | `uint256[]` | The indices of Plots that were Harvested.     |
| `beans`   | `uint256`   | The amount of Beans transferred to `account`. |

### [Pod Listing Cancelled](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/field/FieldFacet.sol#L57) <a href="#event-pod-listing-cancelled" id="event-pod-listing-cancelled"></a>

```solidity
event PodListingCancelled(address indexed account, uint256 index);
```

Emitted when a Pod Listing is cancelled.

| Parameter | Type      | Description                               |
|-----------|-----------|-------------------------------------------|
| `account` | `address` | The account that created the Pod Listing. |
| `index`   | `uint256` | The index of the Plot listed.             |
