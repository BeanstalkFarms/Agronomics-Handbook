# BDV Facet

The BDV Facet holds functions to get the BDV for each whitelisted Silo asset.

## Call Functions

None.

## View Functions

### [Curve to BDV](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/BDVFacet.sol#L24)

```solidity
function curveToBDV(uint256 amount) public view returns (uint256);
```

Returns the BDV of a number of BEAN:3CRV LP tokens.

| Parameter | Type      | Description                          |
| --------- | --------- | ------------------------------------ |
| `amount`  | `uint256` | Number of tokens to get the BDV for. |

| Return Value | Description                                              |
| ------------ | -------------------------------------------------------- |
| `uint256`    | The total BDV of `amount` number of BEAN:3CRV LP tokens. |

### [Bean to BDV](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/BDVFacet.sol#L31)

```solidity
function beanToBDV(uint256 amount) public pure returns (uint256);
```

Returns the BDV of a number of Beans (1 Bean = 1 BDV).

| Parameter | Type      | Description                          |
| --------- | --------- | ------------------------------------ |
| `amount`  | `uint256` | Number of tokens to get the BDV for. |

| Return Value | Description                                |
| ------------ | ------------------------------------------ |
| `uint256`    | The total BDV of `amount` number of Beans. |

### [Unripe LP to BDV](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/BDVFacet.sol#L38)

```solidity
function unripeLPToBDV(uint256 amount) public view returns (uint256);
```

Returns the total BDV of a number of Unripe BEAN:3CRV LP tokens.

| Parameter | Type      | Description                          |
| --------- | --------- | ------------------------------------ |
| `amount`  | `uint256` | Number of tokens to get the BDV for. |

| Return Value | Description                                                     |
| ------------ | --------------------------------------------------------------- |
| `uint256`    | The total BDV of `amount` number of Unripe BEAN:3CRV LP tokens. |

### [Unripe Bean to BDV](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/BDVFacet.sol#L47)

```solidity
function unripeBeanToBDV(uint256 amount) public view returns (uint256);
```

Returns the total BDV of a number of Unripe Beans.

| Parameter | Type      | Description                          |
| --------- | --------- | ------------------------------------ |
| `amount`  | `uint256` | Number of tokens to get the BDV for. |

| Return Value | Description                                       |
| ------------ | ------------------------------------------------- |
| `uint256`    | The total BDV of `amount` number of Unripe Beans. |

### [Well BDV](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/BDVFacet.sol#L57)

```solidity
function wellBdv(address token, uint256 amount)
    external
    view
    returns (uint256);
```

Returns the total BDV of a number of Well LP tokens given a Well LP token.

| Parameter | Type      | Description                    |
| --------- | --------- | ------------------------------ |
| `token`   | `address` | The whitelisted token address. |
| `amount`  | `uint256` | The number of tokens.          |

| Return Value | Description                                  |
| ------------ | -------------------------------------------- |
| `uint256`    | The total BDV of `amount` number of `token`. |

## Events

None.
