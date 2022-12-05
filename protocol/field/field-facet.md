# Field Facet

## Call Functions

### Sow

```solidity
function sow(uint256 amount, LibTransfer.From mode)
    external
    payable
    returns (uint256);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `amount`  | `uint256` | WIP         |
| `mode`    | `From`    | WIP         |

```solidity
function sowWithMin(
    uint256 amount,
    uint256 minAmount,
    LibTransfer.From mode
) public payable;
```

| Parameter   | Type      | Description |
|-------------|-----------|-------------|
| `amount`    | `uint256` | WIP         |
| `minAmount` | `uint256` | WIP         |
| `mode`      | `From`    | WIP         |

### Harvest

```solidity
function harvest(uint256[] calldata plots, LibTransfer.To mode)
    external
    payable;
```

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `plots`   | `uint256[]` | WIP         |
| `mode`    | `To`        | WIP         |

## View Functions

```solidity
function podIndex() public view returns (uint256);

function harvestableIndex() public view returns (uint256);

function totalPods() public view returns (uint256);

function totalHarvested() public view returns (uint256);

function totalHarvestable() public view returns (uint256);

function totalUnharvestable() public view returns (uint256);

function plot(address account, uint256 plotId)
    public
    view
    returns (uint256);
    
function totalSoil() public view returns (uint256);
```

## Events

```solidity
event Sow(
    address indexed account,
    uint256 index,
    uint256 beans,
    uint256 pods
);

event Harvest(address indexed account, uint256[] plots, uint256 beans);

event PodListingCancelled(address indexed account, uint256 index);
```
