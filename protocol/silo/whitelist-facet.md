# Whitelist Facet

Whitelist Facet handles the whitelisting/dewhitelisting of assets on the [Deposit Whitelist](https://docs.bean.money/almanac/farm/silo#deposit-whitelist).

## Call Functions

### [Dewhitelist Token](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/WhitelistFacet.sol#L26)

```solidity
function dewhitelistToken(address token) external payable;
```

Dewhitelists tokens on the Deposit Whitelist. A token can no longer be Deposited in the Silo after dewhitelisting. Can only be called by the owner of Beanstalk.

| Parameter | Type      | Description                       |
| --------- | --------- | --------------------------------- |
| `token`   | `address` | The token address to dewhitelist. |

### [Whitelist Token](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/WhitelistFacet.sol#L37)

```solidity
function whitelistToken(
    address token,
    bytes4 selector,
    uint32 stalk,
    uint32 stalkEarnedPerSeason
) external payable;
```

Adds a token to the Deposit Whitelist. Can only be called by the owner of Beanstalk.

| Parameter              | Type      | Description                                   |
| ---------------------- | --------- | --------------------------------------------- |
| `token`                | `address` | The token address to whitelist.               |
| `selector`             | `bytes4`  | The selector for the BDV function of `token`. |
| `stalk`                | `uint32`  | Stalk per BDV for `token`.                    |
| `stalkEarnedPerSeason` | `uint32`  | Grown Stalk per BDV per Season for `token`.   |

### [Update Stalk per BDV per Season for Token](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/WhitelistFacet.sol#L52)

```solidity
function updateStalkPerBdvPerSeasonForToken(
    address token,
    uint32 stalkEarnedPerSeason
) external payable;
```

Changes the Grown Stalk per BDV per Season for a token on the Deposit Whitelist.&#x20;

| Parameter              | Type      | Description                                 |
| ---------------------- | --------- | ------------------------------------------- |
| `token`                | `address` | The token address on the Deposit Whitelist. |
| `stalkEarnedPerSeason` | `uint32`  | The new Grown Stalk per BDV per Season.     |

## View Functions

None.

## Events

### [Whitelist Token](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/WhitelistFacet.sol#L17) <a href="#event-whitelist-token" id="event-whitelist-token"></a>

```solidity
event WhitelistToken(
    address indexed token,
    bytes4 selector,
    uint32 stalkEarnedPerSeason,
    uint256 stalk
);
```

Emitted when a token is added to the Deposit Whitelist.

| Parameter              | Type      | Description                                   |
| ---------------------- | --------- | --------------------------------------------- |
| `token`                | `address` | The whitelisted token address.                |
| `selector`             | `bytes4`  | The selector for the BDV function of `token`. |
| `stalkEarnedPerSeason` | `uint32`  | Grown Stalk per BDV per Season for `token`.   |
| `stalk`                | `uint256` | Stalk per BDV for `token`.                    |

### [Update Stalk per BDV per Season](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/WhitelistFacet.sol#L24) <a href="#event-dewhitelist-token" id="event-dewhitelist-token"></a>

```solidity
event UpdatedStalkPerBdvPerSeason(
    address indexed token,
    uint32 stalkEarnedPerSeason,
    uint32 season
);
```

Emitted when the Grown Stalk per BDV per Season for a token on the Deposit Whitelist is changed.&#x20;

| Parameter              | Type      | Description                                   |
| ---------------------- | --------- | --------------------------------------------- |
| `token`                | `address` | The token address on the Deposit Whitelist.   |
| `stalkEarnedPerSeason` | `uint32`  | The new Grown Stalk per BDV per Season.       |
| `season`               | `uint32`  | The current Season at the time of the change. |

### [Dewhitelist Token](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/beanstalk/silo/WhitelistFacet.sol#L30) <a href="#event-dewhitelist-token" id="event-dewhitelist-token"></a>

```solidity
event DewhitelistToken(address indexed token);
```

Emitted when a token is removed from the Deposit Whitelist.

| Parameter | Type      | Description                      |
| --------- | --------- | -------------------------------- |
| `token`   | `address` | The dewhitelisted token address. |
