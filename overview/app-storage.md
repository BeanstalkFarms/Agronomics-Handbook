# App Storage

Because Beanstalk is a single contract, all of the Facets can share a common state through the [`AppStorage`](https://dev.to/mudgen/appstorage-pattern-for-state-variables-in-solidity-3lki) pattern.

Each Facet should define the `AppStorage` storage variable in the base contract and define **no other** `internal` or `public` state variables.

```solidity
AppStorage internal s;
```

The `AppStorage` struct can be found in the [`AppStorage.sol`](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/AppStorage.sol) file.

When adding new state variables, always add them to the end of the `AppStorage` struct to ensure consistent mapping of state variables to storage slots. When deprecating an unnecessary state variables, either replace it with a different variable denoting that the state variable is deprecated or leave it as is.

In the EVM, data is accessed 32 bytes at a time (known as a slot). Because of this, we choose to pack many state variables within the struct to reduce gas costs. For example, say that in `function foo()`, we change the state of 2 uint256 values. Changing a non-zero value to another non-zero value costs 10000 gas (2*5000). If the 2 values could be stored in uint128s instead (meaning the data is in one slot), we shave off 2100 gas, as the state slot is now "warm".
