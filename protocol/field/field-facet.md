# Field Facet

Field sows Beans.

## Call Functions

### [Sow](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L33)

```solidity
function sow(uint256 amount, LibTransfer.From mode)
    external
    payable
    returns (uint256);
```

Sow Beans in exchange for Pods.

| Parameter | Type      | Description                                                 |
|-----------|-----------|-------------------------------------------------------------|
| `amount`  | `uint256` | The number of Beans to Sow.                                 |
| `mode`    | `From`    | The balance to transfer Beans from; see `LibTransfer.From`. |

| Return Value | Description                  |
|--------------|------------------------------|
| `uint256`    | The number of Pods received. |

### [Sow With Min](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L41)

```solidity
function sowWithMin(
    uint256 amount,
    uint256 minAmount,
    LibTransfer.From mode
) public payable;
```

Sow Beans in exchange for Pods. Use at least `minSoil`.

| Parameter   | Type      | Description                                                                                               |
|-------------|-----------|-----------------------------------------------------------------------------------------------------------|
| `amount`    | `uint256` | The number of Beans to Sow.                                                                               |
| `minAmount` | `uint256` | The minimum amount of Soil to use; reverts if there is less than this much Soil available upon execution. |
| `mode`      | `From`    | The balance to transfer Beans from; see `LibTrasfer.From`.                                                |

### [Harvest](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L67)

```solidity
function harvest(uint256[] calldata plots, LibTransfer.To mode)
    external
    payable;
```

Harvest Pods from the Field.

| Parameter | Type        | Description                                            |
|-----------|-------------|--------------------------------------------------------|
| `plots`   | `uint256[]` | List of plot IDs to Harvest.                           |
| `mode`    | `To`        | The balance to transfer Beans to; see `LibTrasfer.To`. |

## View Functions

### [Pod Index](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L110)

```solidity
function podIndex() public view returns (uint256);
```

Returns the total number of Pods ever minted.

| Return Value | Description                           |
|--------------|---------------------------------------|
| `uint256`    | The total number of Pods ever minted. |

### [Harvestable Index](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L114)

```solidity
function harvestableIndex() public view returns (uint256);
```

Returns the index below which Pods are Harvestable.

| Return Value | Description                                 |
|--------------|---------------------------------------------|
| `uint256`    | The index below which Pods are Harvestable. |

### [Total Pods](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L118)

```solidity
function totalPods() public view returns (uint256);
```

Returns the number of outstanding Pods.

| Return Value | Description                     |
|--------------|---------------------------------|
| `uint256`    | The number of outstanding Pods. |

### [Total Harvested](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L122)

```solidity
function totalHarvested() public view returns (uint256);
```

Returns the number of Pods that have ever been Harvested.

| Return Value | Description                                       |
|--------------|---------------------------------------------------|
| `uint256`    | The number of Pods that have ever been Harvested. |

### [Total Harvestable](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L126)

```solidity
function totalHarvestable() public view returns (uint256);
```

Returns the number of Pods that are currently Harvestable but have not yet been Harvested.

| Return Value | Description                                                                        |
|--------------|------------------------------------------------------------------------------------|
| `uint256`    | The number of Pods that are currently Harvestable but have not yet been Harvested. |

### [Total Unharvestable](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L130)

```solidity
function totalUnharvestable() public view returns (uint256);
```

Returns the number of Pods that are not yet Harvestable.

| Return Value | Description                                      |
|--------------|--------------------------------------------------|
| `uint256`    | The number of Pods that are not yet Harvestable. |

### [Plot](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L134)

```solidity
function plot(address account, uint256 plotId)
    public
    view
    returns (uint256);
```

Returns the number of Pods remaining in a Plot.

| Parameter | Type      | Description                   |
|-----------|-----------|-------------------------------|
| `account` | `address` | The account that owns a Plot. |
| `plotId`  | `uint256` | The ID of a Plot.             |

| Return Value | Description                             |
|--------------|-----------------------------------------|
| `uint256`    | The number of Pods remaining in a Plot. |

### [Total Soil](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L142)

```solidity    
function totalSoil() public view returns (uint256);
```

Returns the total available Soil.

| Return Value | Description               |
|--------------|---------------------------|
| `uint256`    | The total available Soil. |

## Events

### [Sow](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L20) <a href="#event-sow" id="event-sow"></a>

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

### [Harvest](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L26) <a href="#event-harvest" id="event-harvest"></a>

```solidity
event Harvest(address indexed account, uint256[] plots, uint256 beans);
```

Emitted when `account` claims the Beans associated with Harvestable Pods.

| Parameter | Type        | Description                                   |
|-----------|-------------|-----------------------------------------------|
| `account` | `address`   | The account that owns the `plots`.            |
| `plots`   | `uint256[]` | The indices of Plots that were harvested.     |
| `beans`   | `uint256`   | The amount of Beans transferred to `account`. |

### [Pod Listing Cancelled](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FieldFacet.sol#L27) <a href="#event-pod-listing-cancelled" id="event-pod-listing-cancelled"></a>

```solidity
event PodListingCancelled(address indexed account, uint256 index);
```

Emitted when a Pod Listing is cancelled.

| Parameter | Type      | Description                               |
|-----------|-----------|-------------------------------------------|
| `account` | `address` | The account that created the Pod Listing. |
| `index`   | `uint256` | The index of the Plot listed.             |
