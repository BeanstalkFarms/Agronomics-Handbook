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
    LibTransfer.To mode
) external payable;
```

### Fill Pod Listing

```solidity
function fillPodListing(
    PodListing calldata l,
    uint256 beanAmount,
    LibTransfer.From mode
) external payable;
```

### Cancel Pod Listing

```solidity
function cancelPodListing(uint256 index) external payable;
```

### Create Pod Order

```solidity
function createPodOrder(
    uint256 beanAmount,
    uint24 pricePerPod,
    uint256 maxPlaceInLine,
    LibTransfer.From mode
) external payable returns (bytes32 id);
```

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

### Cancel Pod Order

```solidity
function cancelPodOrder(
    uint24 pricePerPod,
    uint256 maxPlaceInLine,
    LibTransfer.To mode
) external payable;
```

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

### Approve Pods

```solidity
function approvePods(address spender, uint256 amount)
    external
    payable
    nonReentrant;
```

## View Functions

```solidity
/**
 * MarketplaceFacet
 **/
 
function podOrder(
    address account,
    uint24 pricePerPod,
    uint256 maxPlaceInLine
) external view returns (uint256);

function podOrderById(bytes32 id) external view returns (uint256);

function podListing(uint256 index) external view returns (bytes32)

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
    LibTransfer.To mode
);

event PodListingFilled(
    address indexed from,
    address indexed to,
    uint256 index,
    uint256 start,
    uint256 amount
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
    uint256 maxPlaceInLine
);

event PodOrderFilled(
    address indexed from,
    address indexed to,
    bytes32 id,
    uint256 index,
    uint256 start,
    uint256 amount
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
