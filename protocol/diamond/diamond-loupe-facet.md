# Diamond Loupe Facet

## Call Functions

```solidity
None
```

## View Functions

### Facets

```solidity
function facets() external view override returns (Facet[] memory facets_);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/DiamondLoupeFacet.sol#L28)

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `facets_`    | `Facet[]` | WIP         |

### Facet Function Selectors

```solidity
function facetFunctionSelectors(address _facet)
    external
    view
    override
    returns (bytes4[] memory facetFunctionSelectors_);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/DiamondLoupeFacet.sol#L42)

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `_facet`  | `address` | WIP         |

| Return Value              | Type       | Description |
|---------------------------|------------|-------------|
| `facetFunctionSelectors_` | `bytes4[]` | WIP         |

### Facet Addresses

```solidity
function facetAddresses() 
    external 
    view 
    override 
    returns (address[] memory facetAddresses_);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/DiamondLoupeFacet.sol#L54)

| Return Value      | Type        | Description |
|-------------------|-------------|-------------|
| `facetAddresses_` | `address[]` | WIP         |
   
### Facet Address   

```solidity 
function facetAddress(bytes4 _functionSelector)
    external
    view
    override
    returns (address facetAddress_);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/DiamondLoupeFacet.sol#L63)

| Parameter           | Type     | Description |
|---------------------|----------|-------------|
| `_functionSelector` | `bytes4` | WIP         |

| Return Value    | Type      | Description |
|-----------------|-----------|-------------|
| `facetAddress_` | `address` | WIP         |

### Supports Interface
   
```solidity 
function supportsInterface(bytes4 _interfaceId) 
    external 
    view 
    override 
    returns (bool);
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/DiamondLoupeFacet.sol#L74)

| Parameter      | Type     | Description |
|----------------|----------|-------------|
| `_interfaceId` | `bytes4` | WIP         |

| Return Value | Description |
|--------------|-------------|
| `bool`       | WIP         |

## Events

```solidity
None
```
