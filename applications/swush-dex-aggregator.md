# Open Source Grant Application – Swush v2 (Lean MVP)

## Project Overview

**Project Name:** Swush 

**Team Name:** Swush Labs

**Payment Address:** 124C7vfXbvBausfviN3ydZjj4voxPyEwmnJDuNJ9y4kU3ETN

### Overview
Swush is a cross-chain DEX aggregator built on Polkadot. In our previous grant, we successfully delivered an MVP that finds and executes optimal swaps(best output price) across Asset Hub and Hydration.

#### Why Swush Matters for Polkadot

Polkadot’s core strength is cross-chain interoperability - but the user experience for swaps and asset movement across parachains remains fragmented and complex.

Swush bridges that gap. It's a lightweight, open-source DEX aggregator built for Polkadot, enabling optimal asset swaps between parachains (like Moonbeam, Bifrost, HydraDX) by finding best output asset rates via DEX’es and also across ecosystem like Ethereum L2 like Arbitrum and Solana. 

By abstracting away the underlying complexity of XCM and bridge mechanics, Swush builds upon the missing UX layer that lets users interact with Polkadot’s full liquidity stack.


#### Taking inspiration from Solana(Jupiter) and Ethereum(1inch)

Our approach,  similar to how **Jupiter** unlocked Solana and **1inch** on Ethereum by simplifying access to liquidity across fragmented DEXs. Our MVP (Swush v1) successfully routed Polkadot Asset Hub native assets using HydraDX and Asset Hub, validating the core model.

Swush v2 offers: 

- **Seamless asset swaps** between Asset Hub, HydraDX, Moonbeam, Acala and Bifrost using native XCM routing
- **Cross-ecosystem routing** from Polkadot to Arbitrum/Solana using Chainflip
- **One-click deposits** into Hyperliquid, bridging Polkadot-native assets into perps markets


#### User Incentives and Ecosystem-Alignment

Inspired by CRED (App to pay credit card bills), which rewards users for payments (e.g., pay bills), Swush brings a similar mechanic to DeFi.

Each successful swap earns **rewards**, which users can redeem and use for **post-swap actions** like redirecting to staking, vaults, or dApps on the target parachain. This helps parachains **onboard and retain liquidity**, while users gain deeper, contextual benefits.

**Sample flow**

- **Boosted incentives from partner parachains**
    
    *(e.g., after swapping DOT → aUSD into Acala, the user receives a Swush voucher or NFT. They are prompted to deposit the aUSD into Acala’s LDOT-aUSD stability pool. Once the holding period is met(e.g., 7 days), the voucher unlocks a partner-funded reward which could be an ACA token airdrop, fee rebate, voucher, or exclusive NFT. This ensures rewards go to genuine engaged users, and provides measurable ROI for the partner.)*
    

![insert-image-here](https://github.com/swush-labs/swush-dex-aggregator/blob/main/images/swush-flow.png)

TODO: add an interactive flow or example 


#### Building Brand & Community Through NFTs

Taking inspiration from Pudgy Penguins - an NFT project that evolved into a full-fledged consumer brand - Swush plans to build an identity around its own original character: a playful, fiery avatar. 

![insert-image-here](https://github.com/swush-labs/swush-dex-aggregator/blob/main/images/swush-flow.png)

These NFTs are more than collectibles—they’re brand anchors and functional rewards. Early supporters and active users will receive limited-edition **Swush Flame Avatars**, which can:

- Unlock premium features
- Be used in loyalty tiers or in future community campaigns
- Represent the user’s status or journey within the Swush ecosystem

**Over time, these avatars may evolve into a standalone IP - usable in content, merchandise, or cross-chain partnerships.** Just as Pudgy Penguins became more than NFTs through storytelling and emotional resonance, Swush aims to create a recognizable, narrative-driven brand that can grow alongside the product.



#### Existing products

While tools like [Turtle.cool](https://turtle.cool/) provide basic cross-chain transfers and swaps, Swush is:

- A **multi-hop swap router**, not just a bridge
- Integrated with **multiple parachain DEXs** via XCM (HydraDX, Moonbeam, Bifrost)
- Solution combining swaps, ecosystem incentives, and brand loyalty

This creates a strong foundation and a sticky, high-retention user experience.


#### In Summary

Swush is simple:

- **Find the best path. Route the liquidity. Reward the user. Activate the chain.**

It's not just a DEX aggregator—it's a **distribution engine** for parachains, a **loyalty engine** for users, and a **UX unlock** for Polkadot.


## Team 

### **Team members**

**Name of team leader:**
- Anwesh Nayak (@muddlebee)

**Names of team members:**
- Arnav Nayak
- Junior developer(yet to finalize)

### **Contact**
- **Contact Name:** Anwesh Nayak
- **Contact Email:** [anweshknayak@gmail.com](mailto:anweshknayak@gmail.com)

### **Legal Structure**
- **Registered Address:** NA
- **Registered Legal Entity:** NA

### **Team's experience**

I have around 6 years of experience in full stack development. Previously worked as a tech lead at B2B fintech firm. Also, previously was a polkadot ambassador and the community manager/moderator of the official polkadot/kusama discord. I have been contributing to the ecosystem since 3 years. Also participated in Thousand Contributors Programme by w3f and have been adding suggestions/improvements across the w3f github projects(polkodot-wiki).

Also wrote a comprehensive tutorial to get started with Polkadot using the polkadot-js API (https://polkadotjs-developer-hub.gitbook.io/)

**Arnav**, our lead designer has 4 years of experience in product, UI/UX design and management.

### **Team Code Repos**

https://github.com/swush-labs/

### **Team Profiles (if available)**

muddlebee
- https://github.com/muddlebee
- https://www.linkedin.com/in/anweshnayak/

Arnav
- https://www.linkedin.com/in/arnav-nayak-321595141/

## Project Details

### Core Features, Components & Architecture

**Router-Core Service**

- Fetches best asset rates for cross chain swaps across
    - Asset Hub
    - Hydration
    - Bifrost
    - Acala
    - Moonbeam.
- Executes XCM message building and runtime dry-runs for transaction validation.

**Multi-Wallet & Multi-Network Manager**

- Supports both Substrate and EVM wallets across major ecosystem(Polkadot, Ethereum)
- Selects optimal and stable RPC connections.

**Fee Estimation & Dry-Run Layer**

- Calculates fees for entire transaction steps like transaction, XCM fees etc
- Performs runtime `dry_run` to confirm weight, fee sufficiency, and successful execution before sending.

**Analytics Dashboard**

- User view: Historical past swaps of a particular user
    - amount sent and received
    - networks transacted over

**Ethereum L2(Arbitrum)/Solana cross chain swap + Hyperliquid Integration**

- One click deposit using DOT/USDC/USDT → USDC on Arbitrum via Chainflip.
- Post deposit to Arbitrum, user can add balance to Hyperliquid through a referral link.

### User Flow
**Milestone 1: Cross-chain swaps within Polkadot ecosystem**

*(Asset Hub ↔ HydraDX ↔ Moonbeam ↔ Bifrost, with multi-wallet & fee estimation)*

1. **User Connects Wallet**
    - Substrate or EVM wallet detection (multi-wallet support)
    - Network manager selects optimal RPC endpoints for each chain
2. **Select Swap**
    - Choose source/destination chain + token
    - Router-core computes best route via connected parachains (e.g., Asset Hub → HydraDX → Bifrost)
3. **Fee Estimation & Dry Run**
    - Fetch XCM fee weights (BuyExecution, Transact, ReserveAssetDeposit) and transaction/swap estimated fees
    - Dry-run transaction on runtime to confirm execution & estimate outcome
4. **Sign & Execute**
    - User signs swap transaction
    - XCM message sent and executed across chain

---

**Milestone 2: Cross-chain swaps beyond Polkadot & Hyperliquid integration**

*(Chainflip → Ethereum L2s, Hyperliquid perps on-ramp, analytics dashboard)*

1. **User Analytics and XP Points** 
    - User view: transaction history, chain-specific swaps
    - Points awarded on each successful transaction
2. **Select External Destination and EVM wallet**
    - Example: DOT on Asset Hub → USDC on Arbitrum via Chainflip
    - Select destination address and connect popular evm wallets like Metamask/Rabby
3. **Fee Estimation**
    - Display combined bridge fee, slippage, and execution time estimate
4. **Execute Cross-Chain Swap**
    - Initiate transfer via Chainflip deposit-channel
    - Track status until funds reach target chain
5. **Hyperliquid Deposit (Optional)**
    - Prompt for 1-click deposit into Hyperliquid using EIP-2612 permit
    - Redirect user to Hyperliquid with referral link

### Mockups & UI Components

- **Swap UI**: Multi-chain swap form with source/destination selection, best-route display, fee estimate, and status tracker.
- **Transaction Tracker**: Progress bar UI with XCM hop status updates.
- **Analytics Dashboard**: Filterable transaction history for users; aggregated swap metrics for admins.
- **Hyperliquid On-Ramp UI**: Post-bridge deposit prompt with “Trade Now” CTA.

### **Technology Stack**

- **Frontend:** Next.js and React
- **Backend:** Node.js with TypeScript to handle core logic, API integrations, and cross-chain messaging.
- **Database:** Supabase **+** PostgreSQL to store user transaction history and application metadata.
- **Blockchain Integration:** Polkadot.js API/Papi to enable wallet connections, XCM transactions, and interaction with DEXs across Polkadot’s parachains.
- **DevOps:** CI/CD with GitHub Actions for efficient development workflows.

## Development Roadmap

### Overview
- **Estimated Duration:** 5 months
- **Full-Time Equivalent (FTE):** 2.0
- **Total Costs:** $30,000 USD


### Milestone 1: Polkadot Cross-Chain Routing Core


| Deliverable | Specification | TODO |
| --- | --- | --- |
| Core router : cross chain swaps | Fetches best asset rates for cross chain swaps across across Asset Hub, Hydration, Moonbeam, Bifrost, Acala | diagram |
| Transaction tracker  | Track swap status for multi-hop XCM transfers and asset swaps |  |
| Route selector and Total Fee Estimation | Select source & destination chains with fee estimate |  |
| Multi-wallet enablement | Support for both Substrate and EVM-based wallets |  |
| Multi-network connection | Robust and fast connection handling for multiple chain endpoints |  |
| Transaction dry run | Simulated execution with XCM flow validation |  |
| Tests & mock flows | Integration tests with XCM mocking |  |
| Docs | Tutorials to use and test the features |  |

- **Estimated Duration:** 2-2.5 months
- **Full-Time Equivalent (FTE):** 2.0
- **Total Costs:** $18,000 USD

### Milestone 2: External Chain Integration & Hyperliquid On-Ramp

| Deliverable | Specification | TODO |
| --- | --- | --- |
| Chainflip integration for Arbitrum and Solana | Channel routing for Asset Hub based assets like DOT/USDC/USDT to Arbitrum and Solana |  |
| Hyperliquid referral on-ramp | One-click Asset Hub/Polkadot(USDC/USDT) → Arbitrum(with chainflip) → Hyperliquid deposit | Hyperliquid referral explanation |
| Currency dollar value | USD valuation of assets integrated in UI |  |
| Currency metadata rendering | Currency logo display, names, symbols, and decimals per chain |  |
| Ethereum EVM support | Extended evm wallet support for Ethereum/Arbitrum-based chains |  |
| User XP Points | Post swap completion, awarding each user XP Points and unlock new levels on more points. |  |
| User analytics (basic) | Track usage stats, transaction/swap history across multiple chains |  |
| Docs | Tutorials to use the overall app |  |
| Admin dashboard | Admin dashboard to view all activity done through the app, like user swaps, transactions etc |  |

- **Estimated Duration:** 2-2.5 months
- **Full-Time Equivalent (FTE):** 2.0
- **Total Costs:** $12,000 USD

### Budget Breakdown

| Category | Item | FTE | Total | Description |
| --- | --- | --- | --- | --- |
| Personell | Project Lead | 1 FTE | 20,000 USD | leading project with tech architecture and implementation |
| Personell | Product Lead,
UI design/dev | 1 FTE | 10,000 USD | product management, design and UI/UX planning |
| --- | --- | **Total** | **30,000USD** |  |