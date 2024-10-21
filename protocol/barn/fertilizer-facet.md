# Fertilizer Facet

{% hint style="warning" %}
Note that this page has not been updated to reflect the current state of Beanstalk, but is left here as a reference.
{% endhint %}

The Fertilizer Facet handles the minting of Fertilizer and Beans paid to Fertilizer holders.

## Call Functions

### [Claim Fertilized Beans](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L32)

```solidity
function claimFertilized(uint256[] calldata ids, LibTransfer.To mode)
    external
    payable;
```

WIP

| Parameter | Type        | Description |
| --------- | ----------- | ----------- |
| `ids`     | `uint256[]` | WIP         |
| `mode`    | `To`        | WIP         |

### [Mint Fertilizer](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L40)

```solidity
function mintFertilizer(
    uint128 amount,
    uint256 minLP,
    LibTransfer.From mode
) external payable;
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `amount`  | `uint128` | WIP         |
| `minLP`   | `uint256` | WIP         |
| `mode`    | `From`    | WIP         |

### [Add Fertilizer Owner](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L61)

```solidity
function addFertilizerOwner(
    uint128 id,
    uint128 amount,
    uint256 minLP
) external payable;
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `id`      | `uint128` | WIP         |
| `amount`  | `uint128` | WIP         |
| `minLP`   | `uint256` | WIP         |

### [Pay Fertilizer](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L75)

```solidity
function payFertilizer(address account, uint256 amount) external payable
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `amount`  | `uint256` | WIP         |

## View Functions

### [Total Fertilized Beans](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L85)

```solidity
function totalFertilizedBeans() external view returns (uint256 beans);
```

WIP

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `beans`      | `uint256` | WIP         |

### [Total Unfertilized Beans](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L89)

```solidity
function totalUnfertilizedBeans() external view returns (uint256 beans);
```

WIP

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `beans`      | `uint256` | WIP         |

### [Total Fertilizer Beans](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L93)

```solidity
function totalFertilizerBeans() external view returns (uint256 beans);
```

WIP

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `beans`      | `uint256` | WIP         |

### [Get Fertilizer](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L97)

```solidity
function getFertilizer(uint128 id) external view returns (uint256);
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `id`      | `uint128` | WIP         |

| Return Type | Description |
| ----------- | ----------- |
| `uint256`   | WIP         |

### [Get Next](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L101)

```solidity
function getNext(uint128 id) external view returns (uint128);
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `id`      | `uint128` | WIP         |

| Return Type | Description |
| ----------- | ----------- |
| `uint128`   | WIP         |

### [Get First](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L105)

```solidity
function getFirst() external view returns (uint128);
```

WIP

| Return Type | Description |
| ----------- | ----------- |
| `uint128`   | WIP         |

### [Get Last](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L109)

```solidity
function getLast() external view returns (uint128);
```

WIP

| Return Type | Description |
| ----------- | ----------- |
| `uint128`   | WIP         |

### [Get Active Fertilizer](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L113)

```solidity
function getActiveFertilizer() external view returns (uint256);
```

WIP

| Return Type | Description |
| ----------- | ----------- |
| `uint256`   | WIP         |

### [Is Fertilizing](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L117)

```solidity
function isFertilizing() external view returns (bool);
```

WIP

| Return Type | Description |
| ----------- | ----------- |
| `bool`      | WIP         |

### [Beans Per Fertilizer](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L121)

```solidity
function beansPerFertilizer() external view returns (uint128 bpf);
```

WIP

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `bpf`        | `uint128` | WIP         |

### [Get Humidity](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L125)

```solidity
function getHumidity(uint128 _s) external pure returns (uint128 humidity);
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `_s`      | `uint128` | WIP         |

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `humidity`   | `uint128` | WIP         |

### [Get Current Humidity](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L129)

```solidity
function getCurrentHumidity() external view returns (uint128 humidity);
```

WIP

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `humidity`   | `uint128` | WIP         |

### [Get End BPF](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L133)

```solidity
function getEndBpf() external view returns (uint128 endBpf);
```

WIP

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `endBpf`     | `uint128` | WIP         |

### [Remaining Recapitalization](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L137)

```solidity
function remainingRecapitalization() external view returns (uint256);
```

WIP

| Return Type | Description |
| ----------- | ----------- |
| `uint256`   | WIP         |

### [Balance of Unfertilized](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L141)

```solidity
function balanceOfUnfertilized(address account, uint256[] memory ids)
    external
    view
    returns (uint256 beans);
```

WIP

| Parameter | Type        | Description |
| --------- | ----------- | ----------- |
| `account` | `address`   | WIP         |
| `ids`     | `uint256[]` | WIP         |

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `beans`      | `uint256` | WIP         |

### [Balance of Fertilized](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L149)

```solidity
function balanceOfFertilized(address account, uint256[] memory ids)
    external
    view
    returns (uint256 beans);
```

WIP

| Parameter | Type        | Description |
| --------- | ----------- | ----------- |
| `account` | `address`   | WIP         |
| `ids`     | `uint256[]` | WIP         |

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `beans`      | `uint256` | WIP         |

### [Balance of Fertilizer](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L157)

```solidity
function balanceOfFertilizer(address account, uint256 id)
    external
    view
    returns (IFertilizer.Balance memory);
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `id`      | `uint256` | WIP         |

| Return Type           | Description |
| --------------------- | ----------- |
| `IFertilizer.Balance` | WIP         |

### [Balance of Batch Fertilizer](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L165)

```solidity
function balanceOfBatchFertilizer(
    address[] memory accounts,
    uint256[] memory ids
) external view returns (IFertilizer.Balance[] memory);
```

WIP

| Parameter  | Type        | Description |
| ---------- | ----------- | ----------- |
| `accounts` | `address[]` | WIP         |
| `ids`      | `uint256[]` | WIP         |

| Return Type             | Description |
| ----------------------- | ----------- |
| `IFertilizer.Balance[]` | WIP         |

### [Get Fertilizers](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L172)

```solidity
function getFertilizers()
    external
    view
    returns (Supply[] memory fertilizers);
```

WIP

| Return Value  | Type       | Description |
| ------------- | ---------- | ----------- |
| `fertilizers` | `Supply[]` | WIP         |

## Events

### [Set Fertilizer](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/FertilizerFacet.sol#L23) <a href="#event-set-fertilizer" id="event-set-fertilizer"></a>

```solidity
event SetFertilizer(uint128 id, uint128 bpf);
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `id`      | `uint128` | WIP         |
| `bpf`     | `uint128` | WIP         |
