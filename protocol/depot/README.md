# Farm

The Farm allows Farmers to call multiple functions in a single transaction and use assets between different functions in a composable manner, without those assets every leaving Beanstalk (thanks to [Internal Balances](../../overview/internal-balances.md)). Internal Balances allow the `farm` function to use the output of a function in the next function call.

The Farm also provides composable Beanstalk-native interfaces for other DeFi protocols. This allows Farmers to call supported external protocols through the `farm` function and leverage Internal Balances. The current protocols that the Farm supports are:

* WETH -> wrapping and unwrapping; and
* Curve -> swapping and adding/removing liquidity.
* Pipeline -> performing an arbitrary series of actions in the EVM in a single transaction.

The Farm creates an interface to transfer ERC-20 tokens between Internal and External Balances, as well as between Farmers through the `transferToken` function.

The Farm consists of 5 facets:

* [Farm Facet](farm-facet.md)
* [Depot Facet](depot-facet.md)
* [Token Facet](token-facet.md)
* [Token Support Facet](token-support-facet.md)
* [Curve Facet](curve-facet.md)
