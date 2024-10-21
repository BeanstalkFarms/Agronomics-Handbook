# Diamond Loupe Facet

{% hint style="warning" %}
Note that this page has not been updated to reflect the current state of Beanstalk, but is left here as a reference.
{% endhint %}

The Diamond Loupe Facet allows anyone to see the available functions within Beanstalk.

## Call Functions

None.

## View Functions

### [Facets](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/DiamondLoupeFacet.sol#L28)

```solidity
function facets() external view override returns (Facet[] memory facets_);
```

Returns facet info for all facets of Beanstalk

| Return Value | Type      | Description          |
| ------------ | --------- | -------------------- |
| `facets_`    | `Facet[]` | Array of facet info. |

### [Facet Function Selectors](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/DiamondLoupeFacet.sol#L42)

```solidity
function facetFunctionSelectors(address _facet)
    external
    view
    override
    returns (bytes4[] memory facetFunctionSelectors_);
```

Returns all the function selectors provided by a facet.

| Parameter | Type      | Description                 |
| --------- | --------- | --------------------------- |
| `_facet`  | `address` | Facet to get selectors for. |

<table><thead><tr><th width="282.3333333333333">Return Value</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td><code>facetFunctionSelectors_</code></td><td><code>bytes4[]</code></td><td>Selectors on <code>_facet</code>.</td></tr></tbody></table>

### [Facet Addresses](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/DiamondLoupeFacet.sol#L54)

```solidity
function facetAddresses() 
    external 
    view 
    override 
    returns (address[] memory facetAddresses_);
```

Get all the facet addresses used by the Beanstalk Diamond.

| Return Value      | Type        | Description                            |
| ----------------- | ----------- | -------------------------------------- |
| `facetAddresses_` | `address[]` | All facet addresses used by Beanstalk. |

### [Facet Address](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/DiamondLoupeFacet.sol#L63)

```solidity
function facetAddress(bytes4 _functionSelector)
    external
    view
    override
    returns (address facetAddress_);
```

Gets the facet that supports the given selector.

| Parameter           | Type     | Description                                  |
| ------------------- | -------- | -------------------------------------------- |
| `_functionSelector` | `bytes4` | Selector to get the corresponding facet for. |

| Return Value    | Type      | Description                         |
| --------------- | --------- | ----------------------------------- |
| `facetAddress_` | `address` | Facet that has `_functionSelector`. |

### [Supports Interface](https://github.com/BeanstalkFarms/Beanstalk/blob/fd132ae4eda02e502441c3d28d04ad2c21b4e339/protocol/contracts/farm/facets/DiamondLoupeFacet.sol#L74)

```solidity
function supportsInterface(bytes4 _interfaceId) 
    external 
    view 
    override 
    returns (bool);
```

Returns if a contract implements an interface. Implements [ERC-165](https://eips.ethereum.org/EIPS/eip-165).

| Parameter      | Type     | Description                                |
| -------------- | -------- | ------------------------------------------ |
| `_interfaceId` | `bytes4` | The interface ID, as specified in ERC-165. |

| Return Type | Description                                                      |
| ----------- | ---------------------------------------------------------------- |
| `bool`      | True if the contract implements `_interfaceId`, false otherwise. |

## Events

None.
