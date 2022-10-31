# Field

The Field is Beanstalk's credit facility. Beanstalk relies on a decentralized set of creditors to maintain Bean price stability.

Anytime Beanstalk is willing to issue debt, there is Soil in the Field. Soil represents the number of Beans that Beanstalk is currently willing to borrow.

Anytime there is Soil in the Field, Farmers can Sow Beans in exchange for Pods. Pods are stored in Plots and placed at the end of the Pod Line.&#x20;

Pods become Harvestable on a First In, First Out (FIFO) basis when `deltaB > 0` over the course of a Season. Assuming there are Unharvestable Pods and Unfertilized Beans, 1/3 of Bean mints turn Pods into Harvestable Pods, which can be Harvested (redeemed) for Beans via the `harvest()` function. When a Plot is Harvested, it is deleted from storage.

Pods are implemented using 3 indices:

* `podIndex` -> The total number of Pods ever created.
* `harvestableIndex` -> The total number of Pods that ever became Harvestable.
* `harvestedIndex` -> The total number of Pods ever Harvested.

When Beans are Sown, a Plot is created at the current `podIndex` with `beans * (1 + weather)`. Pods and `podIndex` are incremented by the number of Pods.

When Pods become Harvestable, `harvestableIndex` is incremented by the number of newly Harvestable Pods. Plots are Harvestable if the index of a Plot is less than `harvestableIndex`. Plots can be partially Harvested, in which case Beanstalk deletes the first part of the Plot and creates a new Plot at the `harvestableIndex`. When a Plot is Harvested, the `harvestedIndex` increases by the number of Harvested Pods.

## Fundraiser

Fundraisers allow Beanstalk to raise non-Bean stablecoins to pay for services on behalf of the protocol, such as audits. Fundraisers can be created through the `createFundraiser()` function by Beanstalk or the owner of the contract.

Each Fundraiser requires:

1. The token address of the non-Bean token being raised;
2. The amount of tokens being raised; and
3. The address to send the tokens to upon completion of the Fundraiser.

Farmers `fund()` Fundraisers by transferring the non-Bean stablecoin to Beanstalk and in exchange receive Pods at the current Weather at the end of the Pod Line. Funding is akin to Sowing, but instead of burning Beans, Beanstalk is raising a non-Bean stable coin.

Once all of the Funds have been raised, the tokens are transferred to the payee address stored in the Fundraiser.

You can find links to past BIPs that created Fundraisers [here](https://docs.bean.money/protocol-resources/fundraiser).
