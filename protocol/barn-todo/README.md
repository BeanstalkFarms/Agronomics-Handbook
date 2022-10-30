# Barn (TODO)

On April 17, 2022, Beanstalk was exploited via a governance attack. The attacker used a flash loan to exploit the protocol’s then on-chain governance mechanism and transferred all of the Deposited assets in the Silo to an address they controlled, resulting in a theft of \~$77M in non-Bean assets.

Upon exploit, Beanstalk was Paused and the on-chain governance mechanism was removed. Stalkholders voted [via Snapshot](https://snapshot.org/#/beanstalkfarms.eth/proposal/0xb87854d7f6f40f0877a1333028eab829b213fbcce03f16f9dd3832c8a98ab99b) on how Beanstalk should proceed.

The Barn is the Beanstalk recapitalization facility used to Replant Beanstalk. The Barn Raise started on June 6, 2022 while the protocol was offline and continues until the recapitalization target has been reached.

### Fertilizer

Fertilizer is an ERC-1155 token issued for participation in the Barn Raise. Fertilizer entitles holders to a pro rata portion of 1/3 of Bean mints when Active. Fertilizer can be minted (become Active) as long as the recapitalization target has not been reached.&#x20;

Fertilizer is minted with a given % Humidity. Each Fertilizer entitles its holder up to `1 + humidity` Unfertilized Beans. Unfertilized Beans become Fertilized Beans when Beans are distributed to Fertilizer holders. When Fertilizer has no more corresponding Unfertilized Beans, it becomes Used and no longer receives Bean mints.&#x20;

To track Active Fertilizer, Beanstalk has a global variable `s.bpf`, which is the cumulative Fertilizer paid back at every season. Fertilizer is indexed by `endBpf = s.bpf + 1 + humidity` at the time of minting. This signals that once `s.bpf` reaches `endBpf`, the Fertilizer becomes Used. Beanstalk sorts all non-zero Fertilizer Ids by `endBpf` in `s.endBpfs`. It stores this in a linked list where `s.fFirst` is the start of the list and `s.fLast` is the end of the list.&#x20;

Every Season, Beanstalk increments `s.bpf` by the number of new Bean mints distributed to fertilizer divided by `s.activeFertilizer`. Note that Beanstalk integrates `s.bpf` over `s.activeFertilizer`, every time `s.bpf` reaches `s.fFirst`, `s.activeFertilizer` decreases by the supply of Fertilizer with an id of `s.fFirst`. It then pops the first item off of the linked list and sets `s.fFirst` to the next item. When `s.fFirst == 0`, Beanstalk stops paying Beans to Fertilizer as all Fertilizer is inactive and `s.activeFertilizer = 0`.

Humidity is dependent on the Season. During Season 6074 (The Season Beanstalk was paused at), the Humidity is 500%. The next Season, Humidity will be set to 250% and will continue to decrease by 0.5% every Season until it reaches 20%, at which point it will remain at 20% until all Fertilizer is sold.

Before Beanstalk is Unpaused, Fertilizer is deployed as `FertilizerPreMint.sol`, which transfers USDC from the caller to the Beanstalk Community Multisig address in exchange for Fertilizer. The Fertilizer is issued at the id `6_000_000` as the Humidity is 500%

When Beanstalk is unpaused, the BCM will call the function

`addFertilizerOwner( uint128 id, uint128 amount, uint256 minLP ) external`

which will handle the process of adding BEAN:3CRV liquidity and minting new Deposited Bean for all of the Fertilizer minted prior to Unpause.

At the same time, the Fertilizer contract will be upgraded to [`Fertilizer.sol`](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/FertilizerFacet.sol).  This moved the `mintFertilizer()` functionality to Beanstalk itself instead of happening in the Fertilizer contract. At this point, Beanstalk will automatically add new liquidity for Unripe LP holders and new Beans in the same transaction as when Fertilizer is minted. Beanstalk will also start to automatically change the Fertilizer Id as describe above.

Fertilizer can be claimed via the `claimFertilizer` function or it is claimed automatically whenever Fertilizer is transferred. The Fertilizer contract stores the `lastBpf` value for each token Id that the Farmer owns. When a Farmer claims Fertilizer, Beanstalk computes how many Beans have been Fertilized since the last time the Farmer Fertilized that Id with: `min(s.bpf, s.endBpfs[id]) – lastBpf`. It then gives the Farmer that many Beans for each Fertilizer they have of that id.









During the Barn Raise, Beanstalk issued Unripe Bean and Unripe LP tokens in place of Bean and LP Silo Deposits that existed prior to the attack. All Silo Deposits (Bean:Eth, Bean:3CRV + Bean:LUSD) all receive Unripe LP tokens.



During the Barn Raise, Farmers can purchase Fertilizer for 1 USDC each. When Fertilizer is sold, Beanstalk adds liquidity to the BEAN:3CRV pool at a ratio of 1:0.866616. Adding liquidity at this ratio causes the deltaB in the BEAN:3CRV pool to trend towards the pre-exploit deltaB. &#x20;

### ****

The Barn mints an additional amount of Beans proportional to the % of Deposited Beans that have been paid back to Unripe Bean holders and distribute the Beans to Unripe Bean holders.&#x20;



### **Unripe Assets**

Upon Replant, Farmers who held Beans in the block prior to the exploit received 1 Unripe Bean for every pre-exploit Bean; Farmers who held whitelisted LP Tokens in the block prior to the exploit received 1 Unripe BEAN:3CRV LP for every 1 BDV of each pre-exploit whitelisted LP Token.

****

Upon Replant, Beanstalk minted Unripe Beans and Unripe LP to all holders of Bean and Bean LP tokens in the block prior to the governance exploit. As the Barn Raise sells Fertilizer, it will distribute Beans to all Unripe Bean holders pro rata using the shares and underlying token model that [EIP-4626](https://eips.ethereum.org/EIPS/eip-4626) uses for yield-bearing tokens. The Unripe tokens are the Shares and Beans/LP are the underlying assets. The underlying portion will continue to fill up as Fertilizer is minted in exchange for USDC and Beanstalk is recapitalized.

Farmers can Chop their Unripe assets at any point for a penalized percent of their corresponding underlying tokens. The penalized percent is equal to the percent of Unfertilized Beans that have been Fertilized. This can be computed as `s.fertilizedIndex / s.unfertilizedIndex`.

Unripe assets can still be Converted between Unripe Beans and Unripe LP.

Beanstalk issues 1 Unripe Bean for every existing Bean in the block prior to the exploit.

Beanstalk issued 1 Unripe BEAN:3CRV LP for every existing BDV of LP in the block prior to the exploit in the BEAN:ETH Uniswap V2 pool, the BEAN:3CRV metapool and the BEAN:LUSD pool.&#x20;

###
