# Marketplace Facet

{% hint style="warning" %}
Note that this page has not been updated to reflect the current state of Beanstalk, but is left here as a reference.
{% endhint %}

The Marketplace Facet handles logic for buying and selling Pods on the [Pod Market](https://docs.bean.money/almanac/farm/market#pods).

## Call Functions

### [Create Pod Listing](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L24)

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

WIP

| Parameter             | Type      | Description |
| --------------------- | --------- | ----------- |
| `index`               | `uint256` | WIP         |
| `start`               | `uint256` | WIP         |
| `amount`              | `uint256` | WIP         |
| `pricePerPod`         | `uint24`  | WIP         |
| `maxHarvestableIndex` | `uint256` | WIP         |
| `minFillAmount`       | `uint256` | WIP         |
| `mode`                | `To`      | WIP         |

### [Create Pod Listing V2](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L44)

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

WIP

| Parameter             | Type      | Description |
| --------------------- | --------- | ----------- |
| `index`               | `uint256` | WIP         |
| `start`               | `uint256` | WIP         |
| `amount`              | `uint256` | WIP         |
| `maxHarvestableIndex` | `uint256` | WIP         |
| `minFillAmount`       | `uint256` | WIP         |
| `pricingFunction`     | `bytes`   | WIP         |
| `mode`                | `To`      | WIP         |

### [Fill Pod Listing](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L65)

```solidity
function fillPodListing(
    PodListing calldata l,
    uint256 beanAmount,
    LibTransfer.From mode
) external payable;
```

WIP

| Parameter    | Type         | Description |
| ------------ | ------------ | ----------- |
| `l`          | `PodListing` | WIP         |
| `beanAmount` | `uint256`    | WIP         |
| `mode`       | `From`       | WIP         |

### [Fill Pod Listing V2](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L81)

```solidity
function fillPodListingV2(
    PodListing calldata l,
    uint256 beanAmount,
    bytes calldata pricingFunction,
    LibTransfer.From mode
) external payable;
```

WIP

| Parameter         | Type         | Description |
| ----------------- | ------------ | ----------- |
| `l`               | `PodListing` | WIP         |
| `beanAmount`      | `uint256`    | WIP         |
| `pricingFunction` | `bytes`      | WIP         |
| `mode`            | `From`       | WIP         |

### [Cancel Pod Listing](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L99)

```solidity
function cancelPodListing(uint256 index) external payable;
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `index`   | `uint256` | WIP         |

### [Create Pod Order](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L113)

```solidity
function createPodOrder(
    uint256 beanAmount,
    uint24 pricePerPod,
    uint256 maxPlaceInLine,
    uint256 minFillAmount,
    LibTransfer.From mode
) external payable returns (bytes32 id);
```

WIP

| Parameter        | Type      | Description |
| ---------------- | --------- | ----------- |
| `beanAmount`     | `uint256` | WIP         |
| `pricePerPod`    | `uint24`  | WIP         |
| `maxPlaceInLine` | `uint256` | WIP         |
| `minFillAmount`  | `uint256` | WIP         |
| `mode`           | `From`    | WIP         |

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `id`         | `bytes32` | WIP         |

### [Create Pod Order V2](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L124)

```solidity
function createPodOrderV2(
    uint256 beanAmount,
    uint256 maxPlaceInLine,
    uint256 minFillAmount,
    bytes calldata pricingFunction,
    LibTransfer.From mode
) external payable returns (bytes32 id);
```

| Parameter         | Type      | Description |
| ----------------- | --------- | ----------- |
| `beanAmount`      | `uint256` | WIP         |
| `maxPlaceInLine`  | `uint256` | WIP         |
| `minFillAmount`   | `uint256` | WIP         |
| `pricingFunction` | `bytes`   | WIP         |
| `mode`            | `From`    | WIP         |

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `id`         | `bytes32` | WIP         |

### [Fill Pod Order](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L136)

```solidity
function fillPodOrder(
    PodOrder calldata o,
    uint256 index,
    uint256 start,
    uint256 amount,
    LibTransfer.To mode
) external payable;
```

WIP

| Parameter | Type       | Description |
| --------- | ---------- | ----------- |
| `o`       | `PodOrder` | WIP         |
| `index`   | `uint256`  | WIP         |
| `start`   | `uint256`  | WIP         |
| `amount`  | `uint256`  | WIP         |
| `mode`    | `To`       | WIP         |

### [Fill Pod Order V2](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L146)

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

WIP

| Parameter         | Type       | Description |
| ----------------- | ---------- | ----------- |
| `o`               | `PodOrder` | WIP         |
| `index`           | `uint256`  | WIP         |
| `start`           | `uint256`  | WIP         |
| `amount`          | `uint256`  | WIP         |
| `pricingFunction` | `bytes`    | WIP         |
| `mode`            | `To`       | WIP         |

### [Cancel Pod Order](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L158)

```solidity
function cancelPodOrder(
    uint24 pricePerPod,
    uint256 maxPlaceInLine,
    uint256 minFillAmount,
    LibTransfer.To mode
) external payable;
```

WIP

| Parameter        | Type      | Description |
| ---------------- | --------- | ----------- |
| `pricePerPod`    | `uint24`  | WIP         |
| `maxPlaceInLine` | `uint256` | WIP         |
| `minFillAmount`  | `uint256` | WIP         |
| `mode`           | `To`      | WIP         |

### [Cancel Pod Order V2](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L167)

```solidity
function cancelPodOrderV2(
    uint256 maxPlaceInLine,
    uint256 minFillAmount,
    bytes calldata pricingFunction,
    LibTransfer.To mode
) external payable;
```

WIP

| Parameter         | Type      | Description |
| ----------------- | --------- | ----------- |
| `maxPlaceInLine`  | `uint256` | WIP         |
| `minFillAmount`   | `uint256` | WIP         |
| `pricingFunction` | `bytes`   | WIP         |
| `mode`            | `To`      | WIP         |

### [Transfer Plot](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L219)

```solidity
function transferPlot(
    address sender,
    address recipient,
    uint256 id,
    uint256 start,
    uint256 end
) external payable nonReentrant;
```

WIP

| Parameter   | Type      | Description |
| ----------- | --------- | ----------- |
| `sender`    | `address` | WIP         |
| `recipient` | `address` | WIP         |
| `id`        | `uint256` | WIP         |
| `start`     | `uint256` | WIP         |
| `end`       | `uint256` | WIP         |

### [Approve Pods](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L244)

```solidity
function approvePods(address spender, uint256 amount)
    external
    payable
    nonReentrant;
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `spender` | `address` | WIP         |
| `amount`  | `uint256` | WIP         |

### [Get Amount Pods From Fill Listing V2](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/Listing.sol#L258)

```solidity
function getAmountPodsFromFillListingV2(
    uint256 placeInLine, 
    uint256 podListingAmount,
    uint256 fillBeanAmount,
    bytes calldata pricingFunction
) public pure returns (uint256 amount);
```

WIP

| Parameter          | Type      | Description |
| ------------------ | --------- | ----------- |
| `placeInLine`      | `uint256` | WIP         |
| `podListingAmount` | `uint256` | WIP         |
| `fillBeanAmount`   | `uint256` | WIP         |
| `pricingFunction`  | `bytes`   | WIP         |

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `amount`     | `uint256` | WIP         |

### [Get Amount Beans To Fill Order V2](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/Order.sol#L191)

```solidity
function getAmountBeansToFillOrderV2(
    uint256 placeInLine, 
    uint256 amountPodsFromOrder,
    bytes calldata pricingFunction
) public pure returns (uint256 beanAmount);
```

WIP

| Parameter             | Type      | Description |
| --------------------- | --------- | ----------- |
| `placeInLine`         | `uint256` | WIP         |
| `amountPodsFromOrder` | `uint256` | WIP         |
| `pricingFunction`     | `bytes`   | WIP         |

| Return Value | Type      | Description |
| ------------ | --------- | ----------- |
| `beanAmount` | `uint256` | WIP         |

## View Functions

### [Pod Order](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L178)

```solidity
function podOrder(
    address account,
    uint24 pricePerPod,
    uint256 maxPlaceInLine,
    uint256 minFillAmount
) external view returns (uint256);
```

WIP

| Parameter        | Type      | Description |
| ---------------- | --------- | ----------- |
| `account`        | `address` | WIP         |
| `pricePerPod`    | `uint24`  | WIP         |
| `maxPlaceInLine` | `uint256` | WIP         |
| `minFillAmount`  | `uint256` | WIP         |

| Return Value | Description |
| ------------ | ----------- |
| `uint256`    | WIP         |

### [Pod Order V2](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L194)

```solidity
function podOrderV2(
    address account,
    uint256 maxPlaceInLine,
    uint256 minFillAmount,
    bytes calldata pricingFunction
) external view returns (uint256);
```

WIP

| Parameter         | Type      | Description |
| ----------------- | --------- | ----------- |
| `account`         | `address` | WIP         |
| `maxPlaceInLine`  | `uint256` | WIP         |
| `minFillAmount`   | `uint256` | WIP         |
| `pricingFunction` | `bytes`   | WIP         |

| Return Type | Description |
| ----------- | ----------- |
| `uint256`   | WIP         |

### [Pod Order By Id](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L211)

```solidity
function podOrderById(bytes32 id) external view returns (uint256);
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `id`      | `bytes32` | WIP         |

| Return Type | Description |
| ----------- | ----------- |
| `uint256`   | WIP         |

### [Pod Listing](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/MarketplaceFacet.sol#L104)

```solidity
function podListing(uint256 index) external view returns (bytes32);
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `index`   | `uint256` | WIP         |

| Return Type | Description |
| ----------- | ----------- |
| `bytes32`   | WIP         |

### [Allowance Pods](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/PodTransfer.sol#L41)

```solidity
function allowancePods(address owner, address spender)
    public
    view
    returns (uint256);
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `owner`   | `address` | WIP         |
| `spender` | `address` | WIP         |

| Return Type | Description |
| ----------- | ----------- |
| `uint256`   | WIP         |

## Events

### [Pod Listing Created](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/Listing.sol#L32) <a href="#event-pod-listing-created" id="event-pod-listing-created"></a>

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

WIP

| Parameter             | Type        | Description |
| --------------------- | ----------- | ----------- |
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

### [Pod Listing Filled](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/Listing.sol#L45) <a href="#event-pod-listing-filled" id="event-pod-listing-filled"></a>

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

WIP

| Parameter     | Type      | Description |
| ------------- | --------- | ----------- |
| `from`        | `address` | WIP         |
| `to`          | `address` | WIP         |
| `index`       | `uint256` | WIP         |
| `start`       | `uint256` | WIP         |
| `amount`      | `uint256` | WIP         |
| `costInBeans` | `uint256` | WIP         |

### [Pod Listing Cancelled](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/Listing.sol#L54) <a href="#event-pod-listing-cancelled" id="event-pod-listing-cancelled"></a>

```solidity
event PodListingCancelled(address indexed account, uint256 index);
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `index`   | `uint256` | WIP         |

### [Pod Order Created](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/Order.sol#L26) <a href="#event-pod-order-created" id="event-pod-order-created"></a>

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

WIP

| Parameter         | Type        | Description |
| ----------------- | ----------- | ----------- |
| `account`         | `address`   | WIP         |
| `id`              | `bytes32`   | WIP         |
| `amount`          | `uint256`   | WIP         |
| `pricePerPod`     | `uint24`    | WIP         |
| `maxPlaceInLine`  | `uint256`   | WIP         |
| `minFillAmount`   | `uint256`   | WIP         |
| `pricingFunction` | `bytes`     | WIP         |
| `priceType`       | `PriceType` | WIP         |

### [Pod Order Filled](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/Order.sol#L37) <a href="#event-pod-order-filled" id="event-pod-order-filled"></a>

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

WIP

| Parameter     | Type      | Description |
| ------------- | --------- | ----------- |
| `from`        | `address` | WIP         |
| `to`          | `address` | WIP         |
| `id`          | `bytes32` | WIP         |
| `index`       | `uint256` | WIP         |
| `start`       | `uint256` | WIP         |
| `amount`      | `uint256` | WIP         |
| `costInBeans` | `uint256` | WIP         |

### [Pod Order Cancelled](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/Order.sol#L47) <a href="#event-pod-order-cancelled" id="event-pod-order-cancelled"></a>

```solidity
event PodOrderCancelled(address indexed account, bytes32 id);
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `account` | `address` | WIP         |
| `id`      | `bytes32` | WIP         |

### [Plot Transfer](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/PodTransfer.sol#L25) <a href="#event-plot-transfer" id="event-plot-transfer"></a>

```solidity
event PlotTransfer(
    address indexed from,
    address indexed to,
    uint256 indexed id,
    uint256 pods
);
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `from`    | `address` | WIP         |
| `to`      | `address` | WIP         |
| `id`      | `uint256` | WIP         |
| `pods`    | `uint256` | WIP         |

### [Pod Approval](https://github.com/BeanstalkFarms/Beanstalk/blob/c20cd7d920643016b5d73eacdfd1b7179d0ea9c2/protocol/contracts/farm/facets/MarketplaceFacet/PodTransfer.sol#L31) <a href="#event-pod-approval" id="event-pod-approval"></a>

```solidity
event PodApproval(
    address indexed owner,
    address indexed spender,
    uint256 pods
);
```

WIP

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `owner`   | `address` | WIP         |
| `spender` | `address` | WIP         |
| `pods`    | `uint256` | WIP         |
