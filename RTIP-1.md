|RTIP: 0001|Introduce RCAX Token V2|
|-:|:---|
|__Type:__|Fork|
|__Authors:__|Warm Beer|
|__Version:__|0.1.0|
|__Status:__|Draft|
|__Created:__|2023-10-14|
|__Updated:__||
|__Resolution:__||

# Introduction
This is a proposal to fork the RCAX token. The current RCAX token would be renamed RCAX Classic or RCAX V1. This new fork would be called RCAX token or RCAX V2. 

# Specification
__The following changes would be made to the RCAX token smart contract and launched on a new token address:__

1. Any RCAX Classic tokens can be converted to the new RCAX tokens with a 1:1 ratio.
2. Burned avatars will be forwarded to the `0x000...dEaD` address instead of being held in the RCAX token smart contract.
3. The `Old School Cool` collection contract address will be fixed so that these avatars can also be burned for mine rewards.
4. The following openzeppelin extensions will be implemented:
```
import "@openzeppelin/contracts-upgradeable@4.9.3/token/ERC20/extensions/ERC20PermitUpgradeable.sol";
import "@openzeppelin/contracts-upgradeable@4.9.3/token/ERC20/extensions/ERC20VotesUpgradeable.sol";
```
These extensions allow the community to create proposals for the project and vote using their tokens. A necessary step for RCAX to become
a DAO.

5. The max supply cap of `72,290,000` will be removed as it is extremely unlikely that it will be reached and only causes confusion about the current supply.


__The following changes are recommended, but the community will decide whether they will be included by a poll:__

### [C1] Base Reward & Halvings

C1/A. Change the starting base reward to `60` and remove the max halvings lock. The first halving will occur 8 weeks after contract deployment, the second halving will take 16 weeks, then any subsequent halving will take 24 weeks.

C1/B. Change the starting base reward to `60`. The first month, 100% of the base reward will be rewarded for mining and any subsequent months will lower the reward by 10% of the original base reward. So after 4 months, the base reward will be 60% of `60`. Until the base reward reaches 0%.

### [C2] Development Wallet Reward

C2. Update the development wallet reward when mining from 10% to 15%. This will NOT be applied retroactively.

### [C3] Eligible Avatars for Mining

C3.1. Set Gen 4 base reward multiplier to `0`.

C3.2. Set Gen 3 base reward multiplier to `0`.

C3.3. Set Aww, Drip, Meme & Singularity base reward multipliers to `4`.

C3.3. Set WC2022 base reward multiplier to `0.1`.

C3.4. Set NFL (The free one) base reward multiplier to `0.1`.

### [C4] Contract Mutability

C4. Deploy the contract as proxy so that `Warm Beer` can make changes to the contract post-launch without needing to fork the project again.

# Motivation

### [C1]

Adoption is very important for a project such as this. Currently there are only about ~200 unique holders of RCAX after the first halving period. I believe that this is not enough for a healthy community and I worry that with the current aggressive halvening timeline, new people would be very hesitant to get invested in the project. This is why I want to propose slowing down the halvening timeline to make it more appealing for new people to join the project.

Solution C1/A is `Warm Beer`'s proposal. Solution C1/B has been suggested by Discord user `ulang`. The community may choose between one of these proposals or not to change the halvening timeline at all.

### [C2]

The development wallet is used to pay out bounties for the RCAX project and incentives community members to improve the project. This is also the only fund where developers are paid from. Exchanges also require quite a hefty sum of liquidity in exchange for token listings and this will also have to come from the development wallet. I worry that the current dev mine reward bonus of 10% is just too small to pay for all this and upping it to 15% from now on would give the project more room to pay for these (future) expenses. The development wallet makes sure that the project does not have to rely on community donations.

### [C3]

WIP

### [C4]

WIP

# Implementation

If C1/A, C2 & C4 are accepted: https://github.com/rca-explorer/rcax-token/blob/main/contracts/RCAXToken.sol






