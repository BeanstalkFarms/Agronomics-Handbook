# Marketplace Facet

## Call Functions

### MarketplaceFacet.sol

#### Create Pod Listing

```solidity
function createPodListing(
    uint256 index,
    uint256 start,
    uint256 amount,
    uint24 pricePerPod,
    uint256 maxHarvestableIndex,
    uint256 minFillAmount,
    LibTransfer.To mode
) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L24)

| Parameter             | Type      | Description |
|-----------------------|-----------|-------------|
| `index`               | `uint256` | WIP         |
| `start`               | `uint256` | WIP         |
| `amount`              | `uint256` | WIP         |
| `pricePerPod`         | `uint24`  | WIP         |
| `maxHarvestableIndex` | `uint256` | WIP         |
| `minFillAmount`       | `uint256` | WIP         |
| `mode`                | `To`      | WIP         |

#### Create Pod Listing V2

```solidity
function createPodListingV2(
    uint256 index,
    uint256 start,
    uint256 amount,
    uint256 maxHarvestableIndex,
    uint256 minFillAmount,
    bytes calldata pricingFunction,
    LibTransfer.To mode
) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L44)

| Parameter             | Type      | Description |
|-----------------------|-----------|-------------|
| `index`               | `uint256` | WIP         |
| `start`               | `uint256` | WIP         |
| `amount`              | `uint256` | WIP         |
| `maxHarvestableIndex` | `uint256` | WIP         |
| `minFillAmount`       | `uint256` | WIP         |
| `pricingFunction`     | `bytes`   | WIP         |
| `mode`                | `To`      | WIP         |

#### Fill Pod Listing

```solidity
function fillPodListing(
    PodListing calldata l,
    uint256 beanAmount,
    LibTransfer.From mode
) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L65)

| Parameter    | Type         | Description |
|--------------|--------------|-------------|
| `l`          | `PodListing` | WIP         |
| `beanAmount` | `uint256`    | WIP         |
| `mode`       | `From`       | WIP         |

#### Fill Pod Listing V2

```solidity
function fillPodListingV2(
    PodListing calldata l,
    uint256 beanAmount,
    bytes calldata pricingFunction,
    LibTransfer.From mode
) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L81)

| Parameter         | Type         | Description |
|-------------------|--------------|-------------|
| `l`               | `PodListing` | WIP         |
| `beanAmount`      | `uint256`    | WIP         |
| `pricingFunction` | `bytes`      | WIP         |
| `mode`            | `From`       | WIP         |

#### Cancel Pod Listing

```solidity
function cancelPodListing(uint256 index) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L99)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `index`   | `uint256` | WIP         |

#### Create Pod Order

```solidity
function createPodOrder(
    uint256 beanAmount,
    uint24 pricePerPod,
    uint256 maxPlaceInLine,
    uint256 minFillAmount,
    LibTransfer.From mode
) external payable returns (bytes32 id);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L113)

| Parameter        | Type      | Description |
|------------------|-----------|-------------|
| `beanAmount`     | `uint256` | WIP         |
| `pricePerPod`    | `uint24`  | WIP         |
| `maxPlaceInLine` | `uint256` | WIP         |
| `minFillAmount`  | `uint256` | WIP         |
| `mode`           | `From`    | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `id`         | `bytes32` | WIP         |

#### Create Pod Order V2

```solidity
function createPodOrderV2(
    uint256 beanAmount,
    uint256 maxPlaceInLine,
    uint256 minFillAmount,
    bytes calldata pricingFunction,
    LibTransfer.From mode
) external payable returns (bytes32 id);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L124)

| Parameter         | Type      | Description |
|-------------------|-----------|-------------|
| `beanAmount`      | `uint256` | WIP         |
| `maxPlaceInLine`  | `uint256` | WIP         |
| `minFillAmount`   | `uint256` | WIP         |
| `pricingFunction` | `bytes`   | WIP         |
| `mode`            | `From`    | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `id`         | `bytes32` | WIP         |

#### Fill Pod Order

```solidity
function fillPodOrder(
    PodOrder calldata o,
    uint256 index,
    uint256 start,
    uint256 amount,
    LibTransfer.To mode
) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L136)

| Parameter | Type       | Description |
|-----------|------------|-------------|
| `o`       | `PodOrder` | WIP         |
| `index`   | `uint256`  | WIP         |
| `start`   | `uint256`  | WIP         |
| `amount`  | `uint256`  | WIP         |
| `mode`    | `To`       | WIP         |

#### Fill Pod Order V2

```solidity
function fillPodOrderV2(
    PodOrder calldata o,
    uint256 index,
    uint256 start,
    uint256 amount,
    bytes calldata pricingFunction,
    LibTransfer.To mode
) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L146)

| Parameter         | Type       | Description |
|-------------------|------------|-------------|
| `o`               | `PodOrder` | WIP         |
| `index`           | `uint256`  | WIP         |
| `start`           | `uint256`  | WIP         |
| `amount`          | `uint256`  | WIP         |
| `pricingFunction` | `bytes`    | WIP         |
| `mode`            | `To`       | WIP         |

#### Cancel Pod Order

```solidity
function cancelPodOrder(
    uint24 pricePerPod,
    uint256 maxPlaceInLine,
    uint256 minFillAmount,
    LibTransfer.To mode
) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L158)

| Parameter        | Type      | Description |
|------------------|-----------|-------------|
| `pricePerPod`    | `uint24`  | WIP         |
| `maxPlaceInLine` | `uint256` | WIP         |
| `minFillAmount`  | `uint256` | WIP         |
| `mode`           | `To`      | WIP         |

#### Cancel Pod Order V2

```solidity
function cancelPodOrderV2(
    uint256 maxPlaceInLine,
    uint256 minFillAmount,
    bytes calldata pricingFunction,
    LibTransfer.To mode
) external payable;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L167)

| Parameter         | Type      | Description |
|-------------------|-----------|-------------|
| `maxPlaceInLine`  | `uint256` | WIP         |
| `minFillAmount`   | `uint256` | WIP         |
| `pricingFunction` | `bytes`   | WIP         |
| `mode`            | `To`      | WIP         |

#### Transfer Plot

```solidity
function transferPlot(
    address sender,
    address recipient,
    uint256 id,
    uint256 start,
    uint256 end
) external payable nonReentrant;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L219)

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `sender`    | `address` | WIP         |
| `recipient` | `address` | WIP         |
| `id`        | `uint256` | WIP         |
| `start`     | `uint256` | WIP         |
| `end`       | `uint256` | WIP         |

#### Approve Pods

```solidity
function approvePods(address spender, uint256 amount)
    external
    payable
    nonReentrant;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L244)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `spender` | `address` | WIP         |
| `amount`  | `uint256` | WIP         |

### Listing.sol

#### Get Amount Pods From Fill Listing V2

```solidity
function getAmountPodsFromFillListingV2(
    uint256 placeInLine, 
    uint256 podListingAmount,
    uint256 fillBeanAmount,
    bytes calldata pricingFunction
) public pure returns (uint256 amount);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/Listing.sol#L258)

| Parameter          | Type      | Description |
|--------------------|-----------|-------------|
| `placeInLine`      | `uint256` | WIP         |
| `podListingAmount` | `uint256` | WIP         |
| `fillBeanAmount`   | `uint256` | WIP         |
| `pricingFunction`  | `bytes`   | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `amount`     | `uint256` | WIP         |

### Order.sol

#### Get Amount Beans To Fill Order V2

```solidity
function getAmountBeansToFillOrderV2(
    uint256 placeInLine, 
    uint256 amountPodsFromOrder,
    bytes calldata pricingFunction
) public pure returns (uint256 beanAmount);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/Order.sol#L191)

| Parameter             | Type      | Description |
|-----------------------|-----------|-------------|
| `placeInLine`         | `uint256` | WIP         |
| `amountPodsFromOrder` | `uint256` | WIP         |
| `pricingFunction`     | `bytes`   | WIP         |

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `beanAmount` | `uint256` | WIP         |

## View Functions

### MarketplaceFacet.sol

#### Pod Order

```solidity
function podOrder(
    address account,
    uint24 pricePerPod,
    uint256 maxPlaceInLine,
    uint256 minFillAmount
) external view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L178)

| Parameter        | Type      | Description |
|------------------|-----------|-------------|
| `account`        | `address` | WIP         |
| `pricePerPod`    | `uint24`  | WIP         |
| `maxPlaceInLine` | `uint256` | WIP         |
| `minFillAmount`  | `uint256` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Pod Order V2

```solidity
function podOrderV2(
    address account,
    uint256 maxPlaceInLine,
    uint256 minFillAmount,
    bytes calldata pricingFunction
) external view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L194)

| Parameter         | Type      | Description |
|-------------------|-----------|-------------|
| `account`         | `address` | WIP         |
| `maxPlaceInLine`  | `uint256` | WIP         |
| `minFillAmount`   | `uint256` | WIP         |
| `pricingFunction` | `bytes`   | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Pod Order By Id

```solidity
function podOrderById(bytes32 id) external view returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L211)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `id`      | `bytes32` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

#### Pod Listing

```solidity
function podListing(uint256 index) external view returns (bytes32);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L104)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `index`   | `uint256` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `bytes32`    | WIP         |

### PodTransfer.sol

#### Allowance Pods

```solidity
function allowancePods(address owner, address spender)
    public
    view
    returns (uint256);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/PodTransfer.sol#L41)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `owner`   | `address` | WIP         |
| `spender` | `address` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `uint256`    | WIP         |

## Events

### Listing.sol

#### Pod Listing Created

```solidity
event PodListingCreated(
    address indexed account, 
    uint256 index, 
    uint256 start, 
    uint256 amount, 
    uint24 pricePerPod, 
    uint256 maxHarvestableIndex, 
    uint256 minFillAmount,
    bytes pricingFunction,
    LibTransfer.To mode,
    LibPolynomial.PriceType pricingType
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/Listing.sol#L32)

| Parameter             | Type        | Description |
|-----------------------|-------------|-------------|
| `account`             | `address`   | WIP         |
| `index`               | `uint256`   | WIP         |
| `start`               | `uint256`   | WIP         |
| `amount`              | `uint256`   | WIP         |
| `pricePerPod`         | `uint24`    | WIP         |
| `maxHarvestableIndex` | `uint256`   | WIP         |
| `minFillAmount`       | `uint256`   | WIP         |
| `pricingFunction`     | `bytes`     | WIP         |
| `mode`                | `To`        | WIP         |
| `pricingType`         | `PriceType` | WIP         |

#### Pod Listing Filled

```solidity
event PodListingFilled(
    address indexed from,
    address indexed to,
    uint256 index,
    uint256 start,
    uint256 amount,
    uint256 costInBeans
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/Listing.sol#L45)

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `from`        | `address` | WIP         |
| `to`          | `address` | WIP         |
| `index`       | `uint256` | WIP         |
| `start`       | `uint256` | WIP         |
| `amount`      | `uint256` | WIP         |
| `costInBeans` | `uint256` | WIP         |

#### Pod Listing Cancelled

```solidity
event PodListingCancelled(address indexed account, uint256 index);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/Listing.sol#L54)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `index`   | `uint256` | WIP         |

### Order.sol

#### Pod Order Created

```solidity
event PodOrderCreated(
    address indexed account,
    bytes32 id,
    uint256 amount,
    uint24 pricePerPod,
    uint256 maxPlaceInLine,
    uint256 minFillAmount,
    bytes pricingFunction,
    LibPolynomial.PriceType priceType
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/Order.sol#L26)

| Parameter         | Type        | Description |
|-------------------|-------------|-------------|
| `account`         | `address`   | WIP         |
| `id`              | `bytes32`   | WIP         |
| `amount`          | `uint256`   | WIP         |
| `pricePerPod`     | `uint24`    | WIP         |
| `maxPlaceInLine`  | `uint256`   | WIP         |
| `minFillAmount`   | `uint256`   | WIP         |
| `pricingFunction` | `bytes`     | WIP         |
| `priceType`       | `PriceType` | WIP         |

#### Pod Order Filled

```solidity
event PodOrderFilled(
    address indexed from,
    address indexed to,
    bytes32 id,
    uint256 index,
    uint256 start,
    uint256 amount,
    uint256 costInBeans
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/Order.sol#L37)

| Parameter     | Type      | Description |
|---------------|-----------|-------------|
| `from`        | `address` | WIP         |
| `to`          | `address` | WIP         |
| `id`          | `bytes32` | WIP         |
| `index`       | `uint256` | WIP         |
| `start`       | `uint256` | WIP         |
| `amount`      | `uint256` | WIP         |
| `costInBeans` | `uint256` | WIP         |

#### Pod Order Cancelled

```solidity
event PodOrderCancelled(address indexed account, bytes32 id);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/Order.sol#L47)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `id`      | `bytes32` | WIP         |

### PodTransfer.sol

#### Plot Transfer

```solidity
event PlotTransfer(
    address indexed from,
    address indexed to,
    uint256 indexed id,
    uint256 pods
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/PodTransfer.sol#L25)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `from`    | `address` | WIP         |
| `to`      | `address` | WIP         |
| `id`      | `uint256` | WIP         |
| `pods`    | `uint256` | WIP         |

#### Pod Approval

```solidity
event PodApproval(
    address indexed owner,
    address indexed spender,
    uint256 pods
);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/PodTransfer.sol#L31)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `owner`   | `address` | WIP         |
| `spender` | `address` | WIP         |
| `pods`    | `uint256` | WIP         |
