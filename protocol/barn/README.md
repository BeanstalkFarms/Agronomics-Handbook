# Barn

On April 17, 2022, Beanstalk was exploited via a governance attack. The attacker used a flash loan to exploit the protocol’s then on-chain governance mechanism and transferred all of the Deposited assets in the Silo to an address they controlled, resulting in a theft of \~$77M in non-Bean assets.

Upon exploit, Beanstalk was Paused and the on-chain governance mechanism was removed. Stalkholders voted [via Snapshot](https://snapshot.org/#/beanstalkfarms.eth/proposal/0xb87854d7f6f40f0877a1333028eab829b213fbcce03f16f9dd3832c8a98ab99b) on how Beanstalk should proceed.

The Barn is the Beanstalk recapitalization facility used to Replant Beanstalk. The Barn Raise started on June 6, 2022 while the protocol was offline and continues until the recapitalization target has been reached.

### Fertilizer

Fertilizer is a semi-fungible limited debt issuance to recapitalize $77M in stolen liquidity.

At the beginning of the Barn Raise, there was 77M Available Fertilizer. Available Fertilizer is the number of Fertilizer that can be bought from Beanstalk in exchange for 1 USDC each. Fertilizer becomes Active when it is bought, at which point the ERC-1155 Fertilizer token is minted.&#x20;

Active Fertilizer entitles holders to a pro rata portion of 1/3 of Bean mints.

Fertilizer is minted with a given % Humidity. Each Fertilizer entitles its holder up to `1 + humidity` Unfertilized Beans. Unfertilized Beans become Fertilized Beans when Beans are distributed to Active Fertilizer holders. When Fertilizer has no more corresponding Unfertilized Beans, it becomes Used and no longer receives Bean mints.&#x20;

To track Active Fertilizer, Beanstalk has a global variable `s.bpf`, which is the cumulative Fertilizer paid back at every Season. Fertilizer is indexed by `endBpf = s.bpf + 1 + humidity` at the time of minting. This signals that once `s.bpf` reaches `endBpf`, the Fertilizer becomes Used. Beanstalk sorts all non-zero Fertilizer ids by `endBpf` in `s.endBpfs`. This is stored in a linked list where `s.fFirst` is the start of the list and `s.fLast` is the end of the list.&#x20;

Every Season, Beanstalk increments `s.bpf` by the number of new Bean mints distributed to Fertilizer holders divided by `s.activeFertilizer`. Note that Beanstalk integrates `s.bpf` over `s.activeFertilizer`—every time `s.bpf` reaches `s.fFirst`, `s.activeFertilizer` decreases by the supply of Fertilizer with an id of `s.fFirst`. The first item is then popped off the linked list and `s.fFirst` is set to the next item. When `s.fFirst == 0`, Beanstalk stops paying Beans to Fertilizer as all Fertilizer is either Used or Available (and thus `s.activeFertilizer == 0`).

Humidity is dependent on the Season during which the Fertilizer is minted. During Season 6074 (the Season Beanstalk was Paused at), the Humidity was 500%. The next Season, Humidity was set to 250% and decreased 0.5% every Season until it reached 20%. The Humidity will remain at 20% until all Fertilizer is sold.

Fertilizer can be claimed via the `claimFertilizer()` function (or it is claimed automatically whenever Fertilizer is transferred). The Fertilizer contract stores the `lastBpf` value for each token id that the Farmer owns. When a Farmer claims Fertilizer, Beanstalk computes how many Beans have been Fertilized since the last time the Farmer Fertilized that id with: `min(s.bpf, s.endBpfs[id]) – lastBpf`. It then gives the Farmer that many Beans for each Fertilizer they have of that id.

#### Pre-Replant Fertilizer

Before Beanstalk was Replanted, Fertilizer was deployed as `FertilizerPreMint.sol`, which transferred USDC from the caller to [the Beanstalk Community Multisig (BCM) address](https://gnosis-safe.io/app/eth:0xa9bA2C40b263843C04d344727b954A545c81D043/transactions/queue) in exchange for Fertilizer. The Fertilizer was issued at the id `6_000_000` as the Humidity is 500%

When Beanstalk was Replanted, the BCM called the `addFertilizerOwner()` function that handled the process of adding liquidity to the BEAN:3CRV pool and minting new Beans for all of the Fertilizer minted prior to Replant.

At the same time, the Fertilizer contract was upgraded to [`Fertilizer.sol`](https://github.com/BeanstalkFarms/Beanstalk/blob/master/protocol/contracts/farm/facets/FertilizerFacet.sol). This moved the `mintFertilizer()` functionality to Beanstalk itself instead of the Fertilizer contract. From this point forward, Beanstalk automatically adds new liquidity for Unripe LP holders and new Beans for Unripe Bean holders in the same transaction that Fertilizer is minted in.

### **Unripe Assets**

Upon Replant, Farmers who held Beans in the block prior to the exploit received 1 Unripe Bean for every pre-exploit Bean; Farmers who held whitelisted LP Tokens in the block prior to the exploit received 1 Unripe BEAN:3CRV LP for every 1 BDV of each pre-exploit whitelisted LP Token.

As Fertilizer is sold, Beans are distributed to all Unripe Bean holders pro rata (and BEAN:3CRV LP is distributed to all Unripe LP holders) using the shares and underlying token model that [EIP-4626](https://eips.ethereum.org/EIPS/eip-4626) uses for yield-bearing tokens. The Unripe tokens are the Shares and Beans/LP are the underlying assets. The underlying portion will continue to increase as Fertilizer is minted in exchange for USDC.

Farmers can Chop their Unripe assets at any point for a penalized percent of the corresponding underlying tokens. The penalized percent is equal to the percent of Unfertilized Beans that have been Fertilized. This can be computed as `s.fertilizedIndex / s.unfertilizedIndex`.
