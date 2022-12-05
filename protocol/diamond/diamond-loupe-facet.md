# Diamond Loupe Facet

## Call Functions

```solidity
None
```

### View Functions

```solidity
function facets() external view override returns (Facet[] memory facets_);

function facetFunctionSelectors(address _facet)
    external
    view
    override
    returns (bytes4[] memory facetFunctionSelectors_);

function facetAddresses() 
    external 
    view 
    override 
    returns (address[] memory facetAddresses_);
    
function facetAddress(bytes4 _functionSelector)
    external
    view
    override
    returns (address facetAddress_);
    
function supportsInterface(bytes4 _interfaceId) 
    external 
    view 
    override 
    returns (bool);
```

## Events

```solidity
None
```
