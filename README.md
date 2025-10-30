<p align="center">
  <a href="https://hashbuzz.social">
    <img src="https://www.hashbuzz.social/favicons/mstile-144x144.png" alt="Hashbuzz Social Logo" width="180"/>
  </a>
</p>

<h1 align="center">Hashbuzz</h1>

<p align="center">
  Turns verified social actions into fair rewards on Hedera
</p>

<p align="center">
  Track 3: Immersive Experiences | Sub-track 4: Gamified Community Governance
</p>

---

## Hashbuzz Repos:

Frontend - https://github.com/Hashbuzz-Social/frontend

Backend - https://github.com/Hashbuzz-Social/dApp-backend

Smart Contract - https://github.com/Hashbuzz-Social/smv201

---

## 1 Hedera Integration Summary:

**Wallet connection (WalletConnect)**
Users connect a Hedera wallet via WalletConnect (HashPack-compatible). This gives the frontend a secure, session-scoped signing channel for on-chain actions without key custody. It keeps approvals explicit at each step: associating the reward token, topping up the campaign escrow, and approving withdrawals when needed.

 **Transactions triggered:** user-initiated signing for TokenAssociateTransaction, TransferTransaction, and ContractExecuteTransaction.
 **Economic justification:** explicit, per-action signing plus fast finality keeps UX simple and trustworthy, which is essential for first-time users and price-sensitive campaigns.
 
**Hedera Token Service (HTS)**
HTS moves the reward token between user wallets and the escrow contract. We keep transfers on HTS because token actions are cheap, predictable, and final in seconds, good fit for many small payouts and accumulated rewards.

 **Transaction types:** TokenAssociateTransaction (associate reward token to the contract and user wallets), TransferTransaction (user → escrow top-ups; escrow → user withdrawals; batch or accumulative rewards).
 **Economic justification:** sub-cent, USD-stable fees and high throughput make micro-rewards viable at scale; predictable costs enable fixed campaign budgets without gas-price volatility.

**Hedera Smart Contract Service (HSCS, EVM)**
A single escrow contract coordinates campaign state and funds. Creators register a campaign, top up the escrow with the reward token, and later close or update status. The contract tracks per-user accruals (based on off-chain X comment reads), supports reward adjustments, and releases tokens to users or returns leftovers on close.

 **Transaction types:** ContractCreateTransaction (deploy escrow), ContractExecuteTransaction (register campaign, update status, apply reward adjustments, release payouts, close campaign), optional ContractCallQuery (read-only calls from backend).
 **Economic justification:** moving control and accounting into a small, purpose-built contract removes counterparty risk and automates settlement while keeping the hot path on low-fee HTS transfers..
 
## 2 Deployment & Setup Instructions:
Clear, bulleted, and step by step instructions on how to clone the repo, install dependencies, configure environment variables, and run the project locally on Hedera Testnet.
**Running Environment:** Specify the expected local running state (e.g., to launch the React frontend on and for the backend.).

## 3 Architecture Diagram: 
A simple diagram (e.g., ASCII art or a simple linked image) showing the data flow between your Frontend (UI), Backend/Smart Contracts, and the Hedera network/Mirror Nodes. The diagram must explicitly label the flow of data to and from Hedera.
 
## 4 Deployed Hedera IDs: 
List all key IDs used in the Testnet deployment (e.g., Smart Contract IDs, HTS Token IDs, HCS Topic IDs, key Hedera Account IDs).

## 5 Technology Stack: 
Add details here

---


## NOTES to omPrakash ,,,,,,

**Security & Secrets (Critical):** DO NOT commit any private keys, files, or
sensitive credentials.

**Example Configuration:** Use example configuration files (.env .example) showing
the structure of required variables.

**Judge Credentials:** Instruct the judges in your DoraHacks submission notes on
how to securely access any required test credentials (e.g., Test account ID and
Private Key are provided in the DoraHacks submission text field for verification. ).

**Code Quality:** Utilize clear function names, consistent styling, and include inline
comments where logic is complex, ensuring the code is easily auditable by
technical judges.

**Auditability:** Ensure the core logic files ( ) are clean. Projects



