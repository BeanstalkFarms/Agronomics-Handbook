# Diamond Loupe Facet

## Call Functions

```solidity
None
```

## View Functions

### [Facets](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/DiamondLoupeFacet.sol#L28)

```solidity
function facets() external view override returns (Facet[] memory facets_);
```

| Return Value | Type      | Description |
|--------------|-----------|-------------|
| `facets_`    | `Facet[]` | WIP         |

### [Facet Function Selectors](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/DiamondLoupeFacet.sol#L42)

```solidity
function facetFunctionSelectors(address _facet)
    external
    view
    override
    returns (bytes4[] memory facetFunctionSelectors_);
```

| Parameter | Type      | Description |
|-----------|-----------|-------------|
| `_facet`  | `address` | WIP         |

| Return Value              | Type       | Description |
|---------------------------|------------|-------------|
| `facetFunctionSelectors_` | `bytes4[]` | WIP         |

### [Facet Addresses](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/DiamondLoupeFacet.sol#L54)

```solidity
function facetAddresses() 
    external 
    view 
    override 
    returns (address[] memory facetAddresses_);
```

| Return Value      | Type        | Description |
|-------------------|-------------|-------------|
| `facetAddresses_` | `address[]` | WIP         |
   
### [Facet Address](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/DiamondLoupeFacet.sol#L63)

```solidity 
function facetAddress(bytes4 _functionSelector)
    external
    view
    override
    returns (address facetAddress_);
```

| Parameter           | Type     | Description |
|---------------------|----------|-------------|
| `_functionSelector` | `bytes4` | WIP         |

| Return Value    | Type      | Description |
|-----------------|-----------|-------------|
| `facetAddress_` | `address` | WIP         |

### [Supports Interface](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/DiamondLoupeFacet.sol#L74)
   
```solidity 
function supportsInterface(bytes4 _interfaceId) 
    external 
    view 
    override 
    returns (bool);
```

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
