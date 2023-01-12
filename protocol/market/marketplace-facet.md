# Marketplace Facet

## Call Functions

### Create Pod Listing

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

| Parameter             | Type      | Description |
| --------------------- | --------- | ----------- |
| `index`               | `uint256` | WIP         |
| `start`               | `uint256` | WIP         |
| `amount`              | `uint256` | WIP         |
| `pricePerPod`         | `uint24`  | WIP         |
| `maxHarvestableIndex` | `uint256` | WIP         |
| `minFillAmount`       | `uint256` | WIP         |
| `mode`                | `To`      | WIP         |

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

| Parameter             | Type      | Description |
| --------------------- | --------- | ----------- |
| `index`               | `uint256` | WIP         |
| `start`               | `uint256` | WIP         |
| `amount`              | `uint256` | WIP         |
| `maxHarvestableIndex` | `uint256` | WIP         |
| `minFillAmount`       | `uint256` | WIP         |
| `pricingFunction`     | `bytes`   | WIP         |
| `mode`                | `To`      | WIP         |

### Fill Pod Listing

```solidity
function fillPodListing(
    PodListing calldata l,
    uint256 beanAmount,
    LibTransfer.From mode
) external payable;
```

| Parameter    | Type         | Description |
| ------------ | ------------ | ----------- |
| `l`          | `PodListing` | WIP         |
| `beanAmount` | `uint256`    | WIP         |
| `mode`       | `From`       | WIP         |

```solidity
function fillPodListingV2(
    PodListing calldata l,
    uint256 beanAmount,
    bytes calldata pricingFunction,
    LibTransfer.From mode
) external payable;
```

| Parameter         | Type         | Description |
| ----------------- | ------------ | ----------- |
| `l`               | `PodListing` | WIP         |
| `beanAmount`      | `uint256`    | WIP         |
| `pricingFunction` | `bytes`      | WIP         |
| `mode`            | `From`       | WIP         |

```solidity
function getAmountPodsFromFillListingV2(
    uint256 placeInLine, 
    uint256 podListingAmount,
    uint256 fillBeanAmount,
    bytes calldata pricingFunction
) public pure returns (uint256 amount);
```

| Parameter          | Type      | Description |
| ------------------ | --------- | ----------- |
| `placeInLine`      | `uint256` | WIP         |
| `podListingAmount` | `uint256` | WIP         |
| `fillBeanAmount`   | `uint256` | WIP         |
| `pricingFunction`  | `bytes`   | WIP         |

### Cancel Pod Listing

```solidity
function cancelPodListing(uint256 index) external payable;
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `index`   | `uint256` | WIP         |

### Create Pod Order

```solidity
function createPodOrder(
    uint256 beanAmount,
    uint24 pricePerPod,
    uint256 maxPlaceInLine,
    uint256 minFillAmount,
    LibTransfer.From mode
) external payable returns (bytes32 id);
```

| Parameter        | Type      | Description |
| ---------------- | --------- | ----------- |
| `beanAmount`     | `uint256` | WIP         |
| `pricePerPod`    | `uint24`  | WIP         |
| `maxPlaceInLine` | `uint256` | WIP         |
| `minFillAmount`  | `uint256` | WIP         |
| `mode`           | `From`    | WIP         |

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

### Fill Pod Order

```solidity
function fillPodOrder(
    PodOrder calldata o,
    uint256 index,
    uint256 start,
    uint256 amount,
    LibTransfer.To mode
) external payable;
```

| Parameter | Type       | Description |
| --------- | ---------- | ----------- |
| `o`       | `PodOrder` | WIP         |
| `index`   | `uint256`  | WIP         |
| `start`   | `uint256`  | WIP         |
| `amount`  | `uint256`  | WIP         |
| `mode`    | `To`       | WIP         |

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

| Parameter         | Type       | Description |
| ----------------- | ---------- | ----------- |
| `o`               | `PodOrder` | WIP         |
| `index`           | `uint256`  | WIP         |
| `start`           | `uint256`  | WIP         |
| `amount`          | `uint256`  | WIP         |
| `pricingFunction` | `bytes`    | WIP         |
| `mode`            | `To`       | WIP         |

```solidity
function getAmountBeansToFillOrderV2(
    uint256 placeInLine, 
    uint256 amountPodsFromOrder,
    bytes calldata pricingFunction
) public pure returns (uint256 beanAmount);
```

| Parameter             | Type      | Description |
| --------------------- | --------- | ----------- |
| `placeInLine`         | `uint256` | WIP         |
| `amountPodsFromOrder` | `uint256` | WIP         |
| `pricingFunction`     | `bytes`   | WIP         |

### Cancel Pod Order

```solidity
function cancelPodOrder(
    uint24 pricePerPod,
    uint256 maxPlaceInLine,
    uint256 minFillAmount,
    LibTransfer.To mode
) external payable;
```

| Parameter        | Type      | Description |
| ---------------- | --------- | ----------- |
| `pricePerPod`    | `uint24`  | WIP         |
| `maxPlaceInLine` | `uint256` | WIP         |
| `minFillAmount`  | `uint256` | WIP         |
| `mode`           | `To`      | WIP         |

```solidity
function cancelPodOrderV2(
    uint256 maxPlaceInLine,
    uint256 minFillAmount,
    bytes calldata pricingFunction,
    LibTransfer.To mode
) external payable;
```

| Parameter         | Type      | Description |
| ----------------- | --------- | ----------- |
| `maxPlaceInLine`  | `uint256` | WIP         |
| `minFillAmount`   | `uint256` | WIP         |
| `pricingFunction` | `bytes`   | WIP         |
| `mode`            | `To`      | WIP         |

### Transfer Plot

```solidity
function transferPlot(
    address sender,
    address recipient,
    uint256 id,
    uint256 start,
    uint256 end
) external payable nonReentrant;
```

| Parameter   | Type      | Description |
| ----------- | --------- | ----------- |
| `sender`    | `address` | WIP         |
| `recipient` | `address` | WIP         |
| `id`        | `uint256` | WIP         |
| `start`     | `uint256` | WIP         |
| `end`       | `uint256` | WIP         |

### Approve Pods

```solidity
function approvePods(address spender, uint256 amount)
    external
    payable
    nonReentrant;
```

| Parameter | Type      | Description |
| --------- | --------- | ----------- |
| `spender` | `address` | WIP         |
| `amount`  | `uint256` | WIP         |

## View Functions

```solidity
/**
 * MarketplaceFacet
 **/

function podOrder(
    address account,
    uint24 pricePerPod,
    uint256 maxPlaceInLine,
    uint256 minFillAmount
) external view returns (uint256);

function podOrderV2(
    address account,
    uint256 maxPlaceInLine,
    uint256 minFillAmount,
    bytes calldata pricingFunction
) external view returns (uint256);

function podOrderById(bytes32 id) external view returns (uint256);

function podListing(uint256 index) external view returns (bytes32);

/**
 * Order
 **/

function allowancePods(address owner, address spender)
    public
    view
    returns (uint256);
```

## Events

```solidity
/**
 * Listing
 **/

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

event PodListingFilled(
    address indexed from,
    address indexed to,
    uint256 index,
    uint256 start,
    uint256 amount,
    uint256 costInBeans
);

event PodListingCancelled(address indexed account, uint256 index);

/**
 * Order
 **/

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

event PodOrderFilled(
    address indexed from,
    address indexed to,
    bytes32 id,
    uint256 index,
    uint256 start,
    uint256 amount,
    uint256 costInBeans
);

event PodOrderCancelled(address indexed account, bytes32 id);

/**
 * PodTransfer
 **/

event PlotTransfer(
    address indexed from,
    address indexed to,
    uint256 indexed id,
    uint256 pods
);

event PodApproval(
    address indexed owner,
    address indexed spender,
    uint256 pods
);
```
