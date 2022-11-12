# Algorithm Explanations

### **``**[**`remainingRecapitalization(...)`**](https://github.com/BeanstalkFarms/Beanstalk/blob/f0e29aae99ddca90085d8dfdc990cff88451d357/protocol/contracts/libraries/LibFertilizer.sol#L136)

`totalDollars` is the total dollar value required to be raised in the Barn Raise. It is equal to `dollarPerUnripeLP() * unripeLP().totalSupply()`. If no Farmer has forfeited Unripe LP, then `totalDollars` is 77 million, but given that Farmer's can `chop` their Unripe LP and forfeit the funds they have not yet been paid back, we need `totalDollars` to decrease with the total supply of Unripe LP.

**`if (s.recapitalized >= totalDollars) return 0;`** —

A safe guard in case Beanstalk ends up in a situation where too much is raised. This is also possible if someone uses the `chop()` function at a penalty even after the full amount has been raised.

**`return totalDollars.sub(s.recapitalized);`** —

&#x20;`s.recapitalized` is incremented every time USDC is exchanged for Fertilizer (or Unripe LP is generated through Convert), but it is equal to the dollar value that has been recapitalized. Thus, the difference between the two is the amount remaining.

### **``**[**`checkForMaxDeltaB(...)`**](https://github.com/BeanstalkFarms/Beanstalk/blob/ddf3869bcdf7f7802eabe83d6abeebdfc7b8d1ab/protocol/contracts/libraries/Oracle/LibCurveOracle.sol#L152)

See [EBIP-2](algorithm-explanations.md#remainingrecapitalization-...).

It is assumed that if `|deltaB| > beanSupply / 100`, then manipulation occurred. This isn't always true, but the ramifications if `|deltaB| > beanSupply / 100` naturally are minimal as Beanstalk will simply mint fewer Beans/less Soil this Season.

Theoretically, a multi-block MEV attack could manipulate `deltaB` to be any value. Multi-block MEV can only be executed on some time cadence dependent on % ownership of Ethereal stake. Therefore, the greatest vulnerability to Beanstalk is a massive one-time Bean/Soil issuance. By adding this supply cap, the maximum effect of potential manipulation can be at most 1% of supply.
