# Diamond Cut Facet

The Diamond Cut Facet is used by the owner to upgrade Beanstalk.

## Call Functions

### [Diamond Cut](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/diamond/DiamondCutFacet.sol#L22)

```solidity
function diamondCut(
    FacetCut[] calldata _diamondCut,
    address _init,
    bytes calldata _calldata
) external override;
```

Add, replace, and/or remove any number of functions and optionally execute a function with `delegatecall`. Can only be called by the owner of Beanstalk.

| Parameter     | Type         | Description                                                                                                          |
| ------------- | ------------ | -------------------------------------------------------------------------------------------------------------------- |
| `_diamondCut` | `FacetCut[]` | Contains the facet addresses and function selectors.                                                                 |
| `_init`       | `address`    | The address of the contract or facet to execute `_calldata`.                                                         |
| `_calldata`   | `bytes`      | A function call, including function selector and arguments (`_calldata` is executed with `delegatecall` on `_init`). |

## View Functions

None.

## Events

None.
