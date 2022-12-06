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
|-----------------------|-----------|-------------|
| `index`               | `uint256` |             |
| `start`               | `uint256` |             |
| `amount`              | `uint256` |             |
| `pricePerPod`         | `uint24`  |             |
| `maxHarvestableIndex` | `uint256` |             |
| `minFillAmount`       | `uint256` |             |
| `mode`                | `To`      |             |

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
|-----------------------|-----------|-------------|
| `index`               | `uint256` |             |
| `start`               | `uint256` |             |
| `amount`              | `uint256` |             |
| `maxHarvestableIndex` | `uint256` |             |
| `minFillAmount`       | `uint256` |             |
| `pricingFunction`     | `bytes`   |             |
| `mode`                | `To`      |             |

### Fill Pod Listing

```solidity
function fillPodListing(
    PodListing calldata l,
    uint256 beanAmount,
    LibTransfer.From mode
) external payable;
```

| Parameter    | Type         | Description |
|--------------|--------------|-------------|
| `l`          | `PodListing` |             |
| `beanAmount` | `uint256`    |             |
| `mode`       | `From`       |             |

```solidity
function fillPodListingV2(
    PodListing calldata l,
    uint256 beanAmount,
    bytes calldata pricingFunction,
    LibTransfer.From mode
) external payable;
```

| Parameter         | Type         | Description |
|-------------------|--------------|-------------|
| `l`               | `PodListing` |             |
| `beanAmount`      | `uint256`    |             |
| `pricingFunction` | `bytes`      |             |
| `mode`            | `From`       |             |

```solidity
function getAmountPodsFromFillListingV2(
    uint256 placeInLine, 
    uint256 podListingAmount,
    uint256 fillBeanAmount,
    bytes calldata pricingFunction
) public pure returns (uint256 amount);
```

| Parameter          | Type      | Description |
|--------------------|-----------|-------------|
| `placeInLine`      | `uint256` |             |
| `podListingAmount` | `uint256` |             |
| `fillBeanAmount`   | `uint256` |             |
| `pricingFunction`  | `bytes`   |             |

### Cancel Pod Listing

```solidity
function cancelPodListing(uint256 index) external payable;
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `index`   | `uint256` |             |

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
|------------------|-----------|-------------|
| `beanAmount`     | `uint256` |             |
| `pricePerPod`    | `uint24`  |             |
| `maxPlaceInLine` | `uint256` |             |
| `minFillAmount`  | `uint256` |             |
| `mode`           | `From`    |             |

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
|-------------------|-----------|-------------|
| `beanAmount`      | `uint256` |             |
| `maxPlaceInLine`  | `uint256` |             |
| `minFillAmount`   | `uint256` |             |
| `pricingFunction` | `bytes`   |             |
| `mode`            | `From`    |             |

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
|-----------|------------|-------------|
| `o`       | `PodOrder` |             |
| `index`   | `uint256`  |             |
| `start`   | `uint256`  |             |
| `amount`  | `uint256`  |             |
| `mode`    | `To`       |             |

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
|-------------------|------------|-------------|
| `o`               | `PodOrder` |             |
| `index`           | `uint256`  |             |
| `start`           | `uint256`  |             |
| `amount`          | `uint256`  |             |
| `pricingFunction` | `bytes`    |             |
| `mode`            | `To`       |             |

```solidity
function getAmountBeansToFillOrderV2(
    uint256 placeInLine, 
    uint256 amountPodsFromOrder,
    bytes calldata pricingFunction
) public pure returns (uint256 beanAmount);
```

| Parameter             | Type      | Description |
|-----------------------|-----------|-------------|
| `placeInLine`         | `uint256` |             |
| `amountPodsFromOrder` | `uint256` |             |
| `pricingFunction`     | `bytes`   |             |

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
|------------------|-----------|-------------|
| `pricePerPod`    | `uint24`  |             |
| `maxPlaceInLine` | `uint256` |             |
| `minFillAmount`  | `uint256` |             |
| `mode`           | `To`      |             |

```solidity
function cancelPodOrderV2(
    uint256 maxPlaceInLine,
    uint256 minFillAmount,
    bytes calldata pricingFunction,
    LibTransfer.To mode
) external payable;
```

| Parameter         | Type      | Description |
|-------------------|-----------|-------------|
| `maxPlaceInLine`  | `uint256` |             |
| `minFillAmount`   | `uint256` |             |
| `pricingFunction` | `bytes`   |             |
| `mode`            | `To`      |             |

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
|-------------|-----------|-------------|
| `sender`    | `address` |             |
| `recipient` | `address` |             |
| `id`        | `uint256` |             |
| `start`     | `uint256` |             |
| `end`       | `uint256` |             |

### Approve Pods

```solidity
function approvePods(address spender, uint256 amount)
    external
    payable
    nonReentrant;
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `spender` | `address` |             |
| `amount`  | `uint256` |             |

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
