# Farm Facet

## Call Functions

### Farm

```solidity
function farm(bytes[] calldata data)
    external
    payable
    withEth
    returns (bytes[] memory results);
```

Loops through the list of encoded selectors in `data` and performs a `delegateCall` on each of them.

| Parameter | Type      | Description                                      |
|-----------|-----------|--------------------------------------------------|
| `data`    | `bytes[]` | The encoded function data for each of the calls. |

| Return Value | Type      | Description                             |
|--------------|-----------|-----------------------------------------|
| `results`    | `bytes[]` | The return data from each of the calls. |

```solidity
function advancedFarm(AdvancedFarmCall[] calldata data)
    external
    payable
    withEth
    returns (bytes[] memory results);
```

Execute multiple AdvancedFarmCalls.

| Parameter | Type                 | Description                                                               |
|-----------|----------------------|---------------------------------------------------------------------------|
| `data`    | `AdvancedFarmCall[]` | The encoded function data for each of the calls to make to this contract. |

| Return Value | Type      | Description                                            |
|--------------|-----------|--------------------------------------------------------|
| `results`    | `bytes[]` | The results from each of the calls passed in via data. |

## View Functions

```
None
```

## Events

```
None
```
