# Fertilizer Facet

## Call Functions

### Claim Fertilized Beans

```solidity
function claimFertilized(uint256[] calldata ids, LibTransfer.To mode)
    external
    payable;
```

| Parameter | Type        | Description |
|-----------|-------------|-------------|
| `ids`     | `uint256[]` | WIP         |
| `mode`    | `To`        | WIP         |

### Mint Fertilizer

```solidity
function mintFertilizer(
    uint128 amount,
    uint256 minLP,
    LibTransfer.From mode
) external payable;
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `amount`  | `uint128` | WIP         |
| `minLP`   | `uint256` | WIP         |
| `mode`    | `From`    | WIP         |

### Add Fertilizer Owner

```solidity
function addFertilizerOwner(
    uint128 id,
    uint128 amount,
    uint256 minLP
) external payable;
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `id`      | `uint128` | WIP         |
| `amount`  | `uint128` | WIP         |
| `minLP`   | `uint256` | WIP         |

### Pay Fertilizer

```solidity
function payFertilizer(address account, uint256 amount) external payable
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `account` | `address` | WIP         |
| `amount`  | `uint256` | WIP         |

## View Functions

```solidity
function totalFertilizedBeans() external view returns (uint256 beans);

function totalUnfertilizedBeans() external view returns (uint256 beans);

function totalFertilizerBeans() external view returns (uint256 beans);

function getFertilizer(uint128 id) external view returns (uint256);

function getNext(uint128 id) external view returns (uint128);

function getFirst() external view returns (uint128);

function getLast() external view returns (uint128);

function getActiveFertilizer() external view returns (uint256);

function isFertilizing() external view returns (bool);

function beansPerFertilizer() external view returns (uint128 bpf);

function getHumidity(uint128 _s) external pure returns (uint128 humidity);

function getCurrentHumidity() external view returns (uint128 humidity);

function getEndBpf() external view returns (uint128 endBpf);

function remainingRecapitalization() external view returns (uint256);

function balanceOfUnfertilized(address account, uint256[] memory ids)
    external
    view
    returns (uint256 beans);

function balanceOfFertilized(address account, uint256[] memory ids)
    external
    view
    returns (uint256 beans);
    
function balanceOfFertilizer(address account, uint256 id)
    external
    view
    returns (IFertilizer.Balance memory);

function balanceOfBatchFertilizer(
    address[] memory accounts,
    uint256[] memory ids
) external view returns (IFertilizer.Balance[] memory);

function getFertilizers()
    external
    view
    returns (Supply[] memory fertilizers);
```

## Events

```solidity
event SetFertilizer(uint128 id, uint128 bpf);
```
