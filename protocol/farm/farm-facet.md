# Farm Facet

## Call Functions

### Farm

```solidity
function farm(bytes[] calldata data) external payable;
```

`farm()` loops through the list of encoded selectors in `data` and performs a `delegateCall` on each of them.

| Parameters | Type      | Description                            |
| ---------- | --------- | -------------------------------------- |
| `data`     | `bytes[]` | List of encoded function calls to make |

## View Functions

```
None
```

## Events

```
None
```
