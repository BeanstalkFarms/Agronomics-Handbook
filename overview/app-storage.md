# App Storage

Because Beanstalk is a single contract, all of the Facets can share a common state through the [`AppStorage`](https://dev.to/mudgen/appstorage-pattern-for-state-variables-in-solidity-3lki) pattern.

Each Facet should define the `AppStorage` storage variable in the base contract and define **no other** `internal` or `public` state variables.

```solidity
AppStorage internal s;
```

The `AppStorage` struct can be found in the [`AppStorage.sol`](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/AppStorage.sol) file.

When adding new state variables, always add them to the end of the `AppStorage` struct to ensure consistent mapping of state variables to storage slots. When depreciating unnecessary state variables, either replace them with a different variable denoting that the state variable is depreciated or leave them as is.
