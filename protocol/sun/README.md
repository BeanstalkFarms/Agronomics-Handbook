# Sun

The Sun advances Beanstalk to the next Season through the `sunrise` function in the [`SeasonFacet`](season-facet.md). Every time an hour passes, `sunrise` can be called 1 more time.

The Season Facet has [several subcontracts](https://github.com/BeanstalkFarms/Beanstalk/tree/master/protocol/contracts/farm/facets/SeasonFacet):

* ``[`Oracle.sol`](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SeasonFacet/Oracle.sol) -> Calculates the time weighted average number of Beans that Bean is above/below its value peg in all pools on the [Oracle Whitelist](https://docs.bean.money/farm/sun#oracle-whitelist).
* ``[`Weather.sol`](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SeasonFacet/Weather.sol) -> Changes the Weather (interest rate) depending on the Bean price, debt level and demand for Soil.
* ``[`Sun.sol`](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/SeasonFacet/Sun.sol) -> Sets the Soil for the next Season and mints new Beans if `Oracle` returns `deltaB > 0` and distributes them as follows:
  * Up to 1/3 to Active Fertilizer holders (see [Barn](../barn/));
  * Up to 1/2 of the remaining amount to Pod holders (see [Field](../field/)); and
  * The rest to Stalkholders in the Silo (see [Silo](../silo/)).

`sunrise()` does the following steps:

1. Increments the Season number;
2. Calls `Oracle` to get `deltaB`;
3. Calls `Weather` to adjust the Weather and checks for Rain and Season of Plenty;
4. Calls `Sun` to set the Soil and mint Beans if `deltaB > 0`; and
5. Pays `msg.sender` Beans for paying the transaction fee associated with calling the function.

{% hint style="warning" %}
In the Beanstalk ecosystem,&#x20;

* **Rain** is referred to as **Oversaturation**; and
* **Season of Plenty** is referred to as **Flood**.&#x20;

See [Terminology Discrepancies](../../misc/terminology-discrepancies.md).
{% endhint %}
