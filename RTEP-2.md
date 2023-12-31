|RTEP: 2|Introduce RCAX Token V2|
|-:|:---|
|__Type:__|Fork|
|__Authors:__|Warm Beer|
|__Version:__|0.3.3|
|__Status:__|Final|
|__Created:__|2023-10-14|
|__Updated:__|2023-10-24|
|__Resolution:__|S5 dropped. C1/C, C2, C3.1, C3.2, C3.3, C3.4 & C4 passed.|

# Introduction

This proposal outlines the introduction of RCAX Token V2 through a fork. The existing RCAX token will be rebranded as RCAX Classic or RCAX V1, while the new fork will be known as RCAX Token or RCAX V2.
Readers are expected to be familiar with the [whitepaper](https://whitepaper.rcax.io).

# Specification

The following changes would be made to the RCAX token smart contract and launched on a new token address:

1. Any RCAX Classic tokens can be converted to the new RCAX tokens with a 1:1 ratio, during a time period of 3 months after the fork launches.
2. Burned avatars will be forwarded to the `0x000...dEaD` address instead of being held in the RCAX token smart contract.
3. The `Old School Cool` collection contract address will be fixed so that these avatars can also be burned for mine rewards.
4. The following openzeppelin extensions will be implemented:
```
import "@openzeppelin/contracts-upgradeable@4.9.3/token/ERC20/extensions/ERC20PermitUpgradeable.sol";
import "@openzeppelin/contracts-upgradeable@4.9.3/token/ERC20/extensions/ERC20VotesUpgradeable.sol";
```
These extensions empower the community to propose and vote on project decisions using their tokens after deployment of a governor contract, using a platform such as https://tally.xyz, a vital step towards RCAX's evolution into a DAO (Decentralized Autonomous Organization).

~~5. The maximum supply cap of `72,290,000` will be removed to eliminate confusion about the current supply, as it is highly unlikely to ever be reached.~~

# Specification (optional/recommended)

The following changes will be voted upon by the community through a poll:

### [C1] Base Reward & Halvings

C1/A. Modify the initial base reward to `60` (from `120`, since one halving has already been completed) and remove the maximum halvings lock. The first halving will take place 8 weeks after contract deployment, the second halving will take 16 weeks after the last halving, and any subsequent halvings will be on 24-week intervals.

C1/B. Adjust the initial base reward to `60` (from `120`, since one halving has already been completed). For the first month, 100% of the base reward will be distributed for mining, with subsequent months reducing the reward by 10% of the original base reward. Consequently, after 4 months, the base reward will be 60% of 60, continuing to decrease until it reaches 0%.

C1/C. Modify the initial base reward to `60` (from `120`, since one halving has already been completed) and remove the maximum halvings lock. Set the halving interval to 24 weeks.

### [C2] Development Wallet Reward

C2. Update the additional development wallet reward when mining from 10% to 15%. This will not be applied retroactively and will only count for future mining rewards.

### [C3] Eligible Avatars for Mining

C3.1. Set Gen 4 base reward multiplier to `0`. If Gen 4 sells out in the shop and C4 is passed, set the multiplier to `1`.

C3.2. Set Gen 3 base reward multiplier to `0`. If Gen 3 sells out in the shop and C4 is passed, set the multiplier to `6`.

C3.3. Set Aww, Drip, Meme & Singularity base reward multipliers to `4`.

C3.3. Set WC2022 base reward multiplier to `0.1`.

C3.4. Set NFL (free variant) base reward multiplier to `0.1`.

### [C4] Contract Mutability

C4. Deploy the contract as proxy so that `Warm Beer` (the founder and developer of RCAX) can make changes to the contract post-launch without needing to fork the project again.

# Motivation

### [C1] Base Reward & Halvings

Project adoption plays a pivotal role in its success. Presently, there are only approximately 200 unique holders of RCAX after the initial halving period. This figure falls short of building a robust and vibrant community, and my concern is that the aggressive halving timeline in place might deter potential newcomers from participating in the project. Consequently, I propose a more gradual reduction in the halving timeline to enhance its attractiveness for new entrants.

Solution C1/A is the proposal of `Warm Beer`, while Solution C1/B has been put forward by Discord user `ulang`. The community has the option to choose between these proposals or maintain the current halving timeline.

### [C2] Development Wallet Reward

The development wallet serves as the financial source for disbursing bounties within the RCAX project, motivating community members to contribute. Additionally, it is the sole fund from which developers receive compensation. Moreover, considerable liquidity is demanded by exchanges in exchange for listing tokens, and this liquidity also originates from the development wallet. My apprehension is that the current developer mining reward bonus of 10% might not suffice for these financial obligations. Increasing it to 15% would provide the project with more financial flexibility to cover both existing and future expenses. The development wallet ensures the project's sustainability without reliance on community donations.

### [C3] Eligible Avatars for Mining

I am concerned that the pricing of RCAX is closely tied to the availability of Gen 3 and 4 avatars in the shop. By allowing only sold-out avatars to be used for mining rewards, RCAX's value would only be influenced by the secondary floor prices of these avatars. 

Both the WC2022 and NFL collections boast around 1 million unique owners each. Enabling mining for these avatars would encourage these holders to participate in the RCAX project. This would be a massive increase in new users being eligible to participate in RCAX mining and will be great for adoption.

### [C4] Contract Mutability

Implementing a token fork is a substantial undertaking. It entails updating the token address across all our decentralized applications and documents, as well as ensuring the entire community is well-informed about these changes. This process can be quite burdensome for even minor project adjustments. 

I propose launching the new token as a proxy, allowing post-launch updates. The risk of developers having access to all the burned avatars is no longer there, as they will be redirected to the `0x000...dEaD` address instead of being held within the RCAX token smart contract. This will make it possible to tweak certain settings and fix any problems post-launch without needing to fork.

# Implementation

Implementation of the new RCAX token smart contract if C1/A, C2 & C4 are accepted: https://github.com/rcax-project/rcax-token/blob/main/contracts/RCAXToken.sol

The implementation is not fully tested yet and unaudited. I invite everyone to help review.




