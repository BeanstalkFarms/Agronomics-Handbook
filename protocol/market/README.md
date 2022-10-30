# Market

The Market will house various DEXs for zero fee trading. For now, there is only the Pod Market, but in the future there may be a zero fee AMM, a zero fee NFT marketplace, etc.

The Pod Market allows Farmers to create, Fill and Cancel Pod Listings and Pod Orders.&#x20;

### Pod Listings

Farmers with Pods can create Pod Listings, which allow other Farmers to buy part or all of their Plots at a given price.

Pod Listings are contained in the following struct:

```solidity
struct PodListing {
    address account;
    uint256 index;
    uint256 start;
    uint256 amount;
    uint24 pricePerPod;
    uint256 maxHarvestableIndex;
    LibTransfer.To mode;
}
```

Pod Listings are created with the `createPodListing()` function. Pod Listings can only be created by the owner of the Plot being listed.

When a Pod Listing is created, The `PodListing` struct with the exception of `account` and `index` is encoded and hashed. Beanstalk stores the hash of the listing on-chain in the `s.podListings` state mapping. Pod Listing hashes are stored by index of the corresponding Plot. The Pod Listing struct is emitted in an event.&#x20;

Pod Listings are Filled with the `fillPodListing()` function. The Pod buyer is required to input the `PodListing` struct associated with the Plot being transferred. Beanstalk hashes the `PodListing` data and verifies that the hash is the same as the hash stored in storage at the corresponding index. If the original Plot owner no longer owns the Plot, then the transaction will fail. If the Fill is successful, Beanstalk then transfers the corresponding part of the Plot to the buyer in exchange for Beans. If the Listing is not empty, the updated Listing is then hashed and stored on-chain.

Pod Listings can be Cancelled at any time with the `cancelPodListing()` function. Pod Listings are automatically Cancelled on Harvest, Transfer or if a new Pod Listing is created with the same plot.

### Pod Orders

Pod Orders allow Farmer with Beans to create Orders to buy Plots. An Order specifies a max Place in Line that the Farmer is will to buy Pods at, the price they are willing to by Pods at and the amount they are willing to buy. All Orders are denominated in Beans. Pod Orders are contained in the following struct:

```solidity
struct PodOrder {
    address account;
    uint24 pricePerPod;
    uint256 maxPlaceInLine;
}
```

Pod Orders are created with the `createPodOrder()` function. Pod Orders can be created by any Farmer.

When a Pod Order is created, The `PodOrder` struct is encoded and hashed. Beanstalk stores the hash of the Order on-chain in the `s.podOrders` state mapping. The hash is the key in the mapping and the amount in the Order is stored in the hash. When a Pod Order is created, Beans are transferred from the Farmer to Beanstalk equal to the amount of Pods being bought times the Price per Pod in the Order. These Beans are locked in Beanstalk until either the Pod Order creator Cancels the Order or the Order is Filled.

Farmers with Pods can sell Pods to open Pod Orders with the `fillPodOrder()` function. The Pod seller is required to input what part of which Plot is being sold and the `PodOrder` struct associated with Order they are filling. Beanstalk hashes the `PodOrder` data and verifies that the hash maps to a non-zero value in `s.podOrders`. The seller is also required to input the Plot being sold as a part of the calldata. If the Fill is successful, the value at the hash key is updated to equal the new amount remaining in the Pod Order.&#x20;

Pod Orders can be Canceled at anytime with the `cancelPodOrder()` function. When an Order is Canceled, Beanstalk returns the remaining Beans in the Pod Order to the Farmer.
