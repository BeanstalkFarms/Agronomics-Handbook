# Convert Getters Facet

{% hint style="warning" %}
Note that this page has not been updated to reflect the current state of Beanstalk, but is left here as a reference.
{% endhint %}

The Convert Getters Facet contains view functions for Convert data.

## Call Functions

None.

## View Functions

### [Get Max Amount In](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ConvertGettersFacet.sol#L19)

```solidity
function getMaxAmountIn(address tokenIn, address tokenOut)
    external
    view
    returns (uint256 amountIn);
```

Estimate the maximum number of tokens that can currently be Converted from `tokenIn` to `tokenOut`.&#x20;

| Parameter  | Type      | Description                                        |
| ---------- | --------- | -------------------------------------------------- |
| `tokenIn`  | `address` | The whitelisted token to estimate Converting from. |
| `tokenOut` | `address` | The whitelisted token to estimate Converting to.   |

| Return Value | Type      | Description                                                                                 |
| ------------ | --------- | ------------------------------------------------------------------------------------------- |
| `amountIn`   | `uint256` | The maximum number of tokens that can currently be Converted from `tokenIn` to `tokenOut`.  |

### [Get Amount Out](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/ConvertGettersFacet.sol#L30)

```solidity
function getAmountOut(
    address tokenIn,
    address tokenOut,
    uint256 amountIn
) external view returns (uint256 amountOut);
```

Estimate the amount of tokens received from Converting `tokenIn` to `tokenOut` given an amount of `tokenIn`.

| Parameter  | Type      | Description                                        |
| ---------- | --------- | -------------------------------------------------- |
| `tokenIn`  | `address` | The whitelisted token to estimate Converting from. |
| `tokenOut` | `address` | The whitelisted token to estimate Converting to.   |

| Return Value | Type      | Description                                                                       |
| ------------ | --------- | --------------------------------------------------------------------------------- |
| `amountOut`  | `uint256` | The amount of `tokenOut` received from a Conversion from `tokenIn` to `tokenOut`. |

## Events

None.
