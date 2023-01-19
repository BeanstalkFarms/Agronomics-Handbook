# Curve Facet

## Call Functions

### Exchange

```solidity
function exchange(
    address pool,
    address registry,
    address fromToken,
    address toToken,
    uint256 amountIn,
    uint256 minAmountOut,
    LibTransfer.From fromMode,
    LibTransfer.To toMode
) external payable nonReentrant;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/CurveFacet.sol#L33)

Swaps a token for another token in a Curve base, meta, plain or crypto pool. Slippage is tolerated on the amount out. It also verifies that the pool exists in the Curve Factory. This function does not support underlying tokens.

* The stable pair Curve Factory can be found at: [`0xB9fC157394Af804a3578134A6585C0dc9cc990d4`](https://etherscan.io/address/0xB9fC157394Af804a3578134A6585C0dc9cc990d4)&#x20;
* The non-stable Curve factory can be found at: [`0x0959158b6040D32d04c301A72CBFD6b39E21c9AE`](https://etherscan.io/address/0x0959158b6040D32d04c301A72CBFD6b39E21c9AE)``

| Parameter      | Type      | Description                                                                                                       |
| -------------- | --------- | ----------------------------------------------------------------------------------------------------------------- |
| `pool`         | `address` | The address of the pool to exchange in. The pool must be registered in one of the Curve Factories.                |
| `registry`     | `address` | The Curve Registry to query `pool` data from.                                                                     |
| `fromToken`    | `address` | The token to swap from.                                                                                           |
| `toToken`      | `address` | The token to swap to.                                                                                             |
| `amountIn`     | `uint256` | The amount to swap from.                                                                                          |
| `minAmountOut` | `uint256` | The minimum amount to receive from the swap.                                                                      |
| `fromMode`     | `From`    | Specifies what balance to receive the tokens from (see [Internal Balances](../../overview/internal-balances.md)). |
| `toMode`       | `To`      | Specifies what balance to send the tokens to (see [Internal Balances](../../overview/internal-balances.md)).      |

### Exchange Underlying

```solidity
function exchangeUnderlying(
    address pool,
    address fromToken,
    address toToken,
    uint256 amountIn,
    uint256 minAmountOut,
    LibTransfer.From fromMode,
    LibTransfer.To toMode
) external payable nonReentrant;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/CurveFacet.sol#L68)

Swaps an underlying token for another underlying token in a Curve metapool. In a Curve metapool, one of the tokens is an LP token of another pool. Underlying tokens include the non-LP token in the pool as well as the tokens in the pool that the LP token belongs to. For example, in the [BEAN:3CRV metapool](https://curve.fi/factory/152), the underlying tokens are Bean, USDC, Tether and Dai.

Slippage is tolerated on the amount out. This function verifies that the pool exists in the Curve Factory.

| Parameter      | Type      | Description                                                                                                       |
| -------------- | --------- | ----------------------------------------------------------------------------------------------------------------- |
| `pool`         | `address` | The address of the pool to exchange in. The pool must be registered in one of the Curve Factories.                |
| `fromToken`    | `address` | The underlying token to swap from.                                                                                |
| `toToken`      | `address` | The underlying token to swap to.                                                                                  |
| `amountIn`     | `uint256` | The amount to swap from.                                                                                          |
| `minAmountOut` | `uint256` | The minimum amount to receive from the swap.                                                                      |
| `fromMode`     | `From`    | Specifies what balance to receive the tokens from (see [Internal Balances](../../overview/internal-balances.md)). |
| `toMode`       | `To`      | Specifies what balance to send the tokens to (see [Internal Balances](../../overview/internal-balances.md)).      |

### Add Liquidity

```solidity
function addLiquidity(
    address pool,
    address registry,
    uint256[] memory amounts,
    uint256 minAmountOut,
    LibTransfer.From fromMode,
    LibTransfer.To toMode
) external payable nonReentrant;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/CurveFacet.sol#L100)

Adds tokens into a liquidity pool on Curve in exchange for LP tokens.

| Parameter      | Type        | Description                                                                                                       |
| -------------- | ----------- | ----------------------------------------------------------------------------------------------------------------- |
| `pool`         | `address`   | The address of the pool to exchange in. The pool must be registered in one of the Curve Factories.                |
| `registry`     | `address`   | The Curve Registry to query `pool` data from.                                                                     |
| `amounts`      | `uint256[]` | The amount of each token to add.                                                                                  |
| `minAmountOut` | `uint256`   | The minimum amount to receive from the swap.                                                                      |
| `fromMode`     | `From`      | Specifies what balance to receive the tokens from (see [Internal Balances](../../overview/internal-balances.md)). |
| `toMode`       | `To`        | Specifies what balance to send the tokens to (see [Internal Balances](../../overview/internal-balances.md)).      |

### Remove Liquidity

```solidity
function removeLiquidity(
    address pool,
    address registry,
    uint256 amountIn,
    uint256[] calldata minAmountsOut,
    LibTransfer.From fromMode,
    LibTransfer.To toMode
) external payable nonReentrant;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/CurveFacet.sol#L159)

Removes liquidity from a pool on Curve in exchange for equal amounts of all  tokens in the liquidity pool. The Farmer burns their LP tokens in the process.&#x20;

| Parameter       | Type        | Description                                                                                                       |
| --------------- | ----------- | ----------------------------------------------------------------------------------------------------------------- |
| `pool`          | `address`   | The address of the pool to exchange in. The pool must be registered in one of the Curve Factories.                |
| `registry`      | `address`   | The Curve Registry to query `pool` data from.                                                                     |
| `amountIn`      | `uint256`   | The amount of LP to remove.                                                                                       |
| `minAmountsOut` | `uint256[]` | The minimum amount to receive in each of the tokens.                                                              |
| `fromMode`      | `From`      | Specifies what balance to receive the tokens from (see [Internal Balances](../../overview/internal-balances.md)). |
| `toMode`        | `To`        | Specifies what balance to sent the tokens to (see [Internal Balances](../../overview/internal-balances.md)).      |

### Remove Liquidity Imbalance&#x20;

```solidity
function removeLiquidityImbalance(
    address pool,
    address registry,
    uint256[] calldata amountsOut,
    uint256 maxAmountIn,
    LibTransfer.From fromMode,
    LibTransfer.To toMode
) external payable nonReentrant;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/CurveFacet.sol#L236)

Removes liquidity from a pool on Curve in exchange for an unequal amounts of tokens in the liquidity pool. The Farmer burns LP tokens in the process.

| Parameter     | Type        | Description                                                                                                       |
| ------------- | ----------- | ----------------------------------------------------------------------------------------------------------------- |
| `pool`        | `address`   | The address of the pool to exchange in. The pool must be registered in one of the Curve Factories.                |
| `registry`    | `address`   | The Curve Registry to query `pool` data from.                                                                     |
| `amountsOut`  | `uint256[]` | The amount of each token to receive.                                                                              |
| `maxAmountIn` | `uint256`   | The max amount of LP tokens to burn.                                                                              |
| `fromMode`    | `From`      | Specifies what balance to receive the tokens from (see [Internal Balances](../../overview/internal-balances.md)). |
| `toMode`      | `To`        | Specifies what balance to send the tokens to (see [Internal Balances](../../overview/internal-balances.md)).      |

### Remove Liquidity One Token

```solidity
function removeLiquidityOneToken(
    address pool,
    address registry,
    address toToken,
    uint256 amountIn,
    uint256 minAmountOut,
    LibTransfer.From fromMode,
    LibTransfer.To toMode
) external payable nonReentrant;
```
[GitHub](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/farm/facets/CurveFacet.sol#L306)

Removes liquidity from a pool on Curve in exchange for an amount of one token in the liquidity pool. The Farmer burns LP tokens in the process.

| Parameter      | Type      | Description                                                                                                       |
| -------------- | --------- | ----------------------------------------------------------------------------------------------------------------- |
| `pool`         | `address` | The address of the pool to exchange in. The pool must be registered in one of the Curve Factories.                |
| `registry`     | `address` | The Curve Registry to query `pool` data from.                                                                     |
| `toToken`      | `address` | The token to receive in exchange for burning LP tokens.                                                           |
| `amountIn`     | `uint256` | The amount of LP tokens to burn.                                                                                  |
| `minAmountOut` | `uint256` | The minimum amount of the token to receive.                                                                       |
| `fromMode`     | `From`    | Specifies what balance to receive the tokens from (see [Internal Balances](../../overview/internal-balances.md)). |
| `toMode`       | `To`      | Specifies what balance to send the tokens to (see [Internal Balances](../../overview/internal-balances.md)).      |

## View Functions

```
None
```

## Events

```
None
```
