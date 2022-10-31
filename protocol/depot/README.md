# Depot

The Depot facilitates complex, gas-efficient transactions within Beanstalk and across the Ethereum network.&#x20;

Using the `farm()` function, Farmers can call multiple functions in a single transaction and use assets between different function calls in a composable manner, without those assets ever leaving Beanstalk (thanks to [Internal Balances](../../overview/internal-balances.md)). Internal Balances allow the `farm()` function to use the output of a function in the next function call.

The Depot also provides composable Beanstalk-native interfaces for other DeFi protocols, known as Pipelines. This allows Farmers to call supported external protocols through the `farm()` function and leverage Internal Balances. The current protocols that the Depot supports are:

* WETH -> wrapping and unwrapping; and
* Curve -> swapping and adding/removing liquidity.

The Depot creates an interface to transfer ERC-20 tokens between Internal and External Balances, as well as between Farmers through the `transferToken()` function.
