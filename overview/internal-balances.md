# Internal Balances

### What are Internal Balances? <a href="#what-are-internal-balances" id="what-are-internal-balances"></a>

Beanstalk uses an Internal Balances system largely inspired by [Balancer's Vault](https://docs.balancer.fi/getting-started/faqs/the-vault#what-are-internal-user-balances). With Internal Balances, Beanstalk is able to store an any ERC-20 token on behalf of a user. Beanstalk stores that the user has that ERC-20 token in [`AppStorage`](app-storage.md). All functions within Beanstalk that either use a user's ERC-20 tokens or send ERC-20 tokens to a user can send/receive the ERC-20 tokens from the user's Internal Balance and/or External Balance (the user's wallet).

The benefit of Internal Balances are that it can significantly reduce transaction costs for those who remain in the Beanstalk ecosystem. For example, say a user buys bean from the curve pool with the intention of sowing. Instead of (1) swapping, (2) transferring to beanstalk, then (3) sowing, internal balances removes (2). As the beanstalk ecosystem evolves, and more protocols utilize the internal balances, the gas savings compound.  

{% hint style="warning" %}
In the Beanstalk ecosystem, **Internal Balances** are referred to as **Farm Balances**. Similarly, **External Balances** (balances in the user's wallet) are referred to as **Circulating Balances**. See [Terminology Discrepancies](../misc/terminology-discrepancies.md).
{% endhint %}

### Relevant Contracts <a href="#associated-contracts" id="associated-contracts"></a>

* &#x20;[`LibTransfer.sol`](https://github.com/BeanstalkFarms/Beanstalk-Replanted/blob/master/protocol/contracts/libraries/Token/LibTransfer.sol)``
* ``[`LibBalance.sol`](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/libraries/Token/LibBalance.sol)

## To/From: 

LibTransfer uses the following structs in order to denote location. 

```solidity
enum From {
    EXTERNAL,
    INTERNAL,
    EXTERNAL_INTERNAL,
    INTERNAL_TOLERANT
}
```
* `EXTERNAL`: Beanstalk will receive tokens from the user's External Balance;
* `INTERNAL`: Beanstalk will receive tokens from the user's Internal Balance;
* `EXTERNAL_INTERNAL`: Beanstalk will receive tokens from the user's Internal Balance and will receive from their External Balance if there is not enough in the Internal Balance; and
* `INTERNAL_TOLERANT`: Beanstalk will receive tokens from the user's Internal Balance and will not fail if there is not enough in their Internal Balance.

```solidity
enum To {
    EXTERNAL,
    INTERNAL
}
```

* `EXTERNAL` Beanstalk will send tokens to the user's External Balance; and
* `INTERNAL` Beanstalk will send tokens to the user's Internal Balance.



### Transferring Internal / External Balances <a href="#transferring-internal-external-balances" id="transferring-internal-external-balances"></a>

At any time, a user can transfer, add or remove ERC-20 tokens from their Internal Balance through the `transferToken()` function in the [`TokenFacet`](../protocol/depot/token-facet.md). `transferToken()` is a general transfer method that allows full control of the tokens start/end location (i.e internal to internal, internal to external, external to internal, external to external).

```solidity
function transferToken(
    IERC20 token,
    address recipient,
    uint256 amount,
    LibTransfer.From fromMode,
    LibTransfer.To toMode
) external payable;
```

### Sending Internal / External Balances <a href="#sending-internal-external-balances" id="sending-internal-external-balances"></a>

A function that sends ERC-20 tokens to users can implement Internal Balances by adding the `To` enum in [`LibTransfer`](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/libraries/Token/LibTransfer.sol) to a function's signature.


Then call `sendToken()` in [`LibTransfer`](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/libraries/Token/LibTransfer.sol) instead of directly calling the ERC-20 function `transferFrom()`.

```solidity
function sendToken(
    IERC20 token,
    uint256 amount,
    address recipient,
    To mode
) internal;
```

### Receiving Internal / External Balances <a href="#receiving-internal-external-balances" id="receiving-internal-external-balances"></a>

A function that receives ERC-20 tokens from users can implement Internal Balances by adding the `From` enum in [`LibTransfer`](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/libraries/Token/LibTransfer.sol) to a function's signature.




Then call `receiveToken` in [`LibTransfer`](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/libraries/Token/LibTransfer.sol) instead of directly calling the ERC-20 function `transfer`.

```solidity
function receiveToken(
    IERC20 token,
    uint256 amount,
    address recipient,
    To mode
) internal;
```
- note: INTERNAL_TOLERANT has been seen to cause security issues, and can be depreciated in the future once it is clear that it is no longer needed.

For protocols building/using Beanstalk and want to interact with internal balances, they can utilize the functions given in [`tokenFacet`](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/TokenFacet.sol), rather than the library itself. 