# Query Examples

{% hint style="warning" %}
All subgraph documentation is under active development.
{% endhint %}

Below are some sample queries you can use to gather information from the Beanstalk contracts.

You can build your own queries using a [GraphQL Explorer](https://graphiql-online.com/graphiql) and enter your endpoint to limit the data to exactly what you need.

## Silo Asset Balances

Current balances of Deposited assets in the Silo with historical BDV amounts.

```graphql
query CurrentDepositedSiloAssets {
  siloAssets(
    where: {
      silo: "0xc1e088fc1323b20bcbee9bd1b9fc9546db5624c5", 
      depositedAmount_gt: "0"
    }
  ) {
    token
    depositedAmount
    depositedBDV
  }
}
```

Bean Deposits over time for the past 4 weeks.

```graphql
query BeanDepositsOverTime {
  siloAssets(
    where: {
      silo: "0xc1e088fc1323b20bcbee9bd1b9fc9546db5624c5", 
      token: "0xbea0000029ad1c77d3d5d23ba2d8893db9d1efab"
    }
  ) {
    dailySnapshots(orderBy: season, orderDirection: desc, first: 28) {
      season
      updatedAt
      depositedAmount
      depositedBDV
      deltaDepositedAmount
      deltaDepositedBDV
    }
  }
}
```

## Field Balances

Current Pod Line Breakdown.

```graphql
query PodLineBreakdown {
  field(id: "0xc1e088fc1323b20bcbee9bd1b9fc9546db5624c5") {
    unharvestablePods
    harvestablePods
    harvestedPods
  }
}
```

Pod Line Breakdown over the last 14 days.

```graphql
query DailyPodLineBreakdown {
  field(id: "0xc1e088fc1323b20bcbee9bd1b9fc9546db5624c5") {
    dailySnapshots(orderBy: season, orderDirection: desc, first: 14) {
      season
      updatedAt
      unharvestablePods
      harvestablePods
      harvestedPods
    }
  }
}


```

Data on the last 10 seasons where all Soil was Sown, and how many blocks it took until it was all Sown.

```graphql
query SoldOutSoilData {
  field(id: "0xc1e088fc1323b20bcbee9bd1b9fc9546db5624c5") {
    hourlySnapshots(
      where: {soilSoldOut: true}
      first: 10
      orderBy: season
      orderDirection: desc
    ) {
      season
      issuedSoil
      temperature
      blocksToSoldOutSoil
    }
  }
}
```

## Pod Market

Data about all active Pod Listings.

```graphql
query ActivePodListings {
 podListings(first: 1000, skip: 0, where: {status: ACTIVE}) {
    start
    pricePerPod
    plot {
      id
      index
    }
    amount
    filledAmount
    maxHarvestableIndex
    status
  }
```

## Farmer Balances

All of the Silo Deposits for the Farmer with address the specified address.

```graphql
query FarmerDeposits {
  farmer(id: "0x1234567890abcdef1234567890abcdef12345678") {
    deposits {
      season
      bdv
      withdrawnBDV
      amount
      withdrawnAmount
      createdAt
      updatedAt
    }
  }
}
```
