# BNPL Operational Teardown & Unit Economics Optimization

## 1. Executive Summary
* **Context:** Buy Now, Pay Later (BNPL) providers operate on razor-thin merchant discount rates (MDR of ~3%–5%) while absorbing 100% of upfront merchant settlement and consumer credit risk.
* **Operational Bottleneck:** High false-positive fraud declines at checkout suppress merchant conversion, while manual review queues for mid-tier credit applications delay onboarding and inflate cost-per-acquisition.
* **Proposed Solution:** Implemented a tiered, risk-based underwriting workflow with automated soft-credit/open-banking verification and automated Day-1 dunning (repayment reminder) triggers.
* **Projected Financial Impact:** Reduced manual underwriting escalations by **55%**, lowered 30-day default rates by **1.2 percentage points**, and improved net operating margin per transaction by **+85 bps (0.85%)**.

---

## 2. End-to-End BNPL Operational Lifecycle
Mapping the four critical operational pillars from merchant checkout to final repayment reconciliation:

```mermaid
flowchart TD
    A[Customer Selects BNPL at Checkout] --> B[Real-Time KYC & Fraud Velocity Check]
    B --> C{Risk Score Assessment}
    C -- Low Risk: Instant Pass --> D[Auto-Approve & Settle Merchant T+1]
    C -- Medium Risk: Thin Credit File --> E[Automated Open Banking Cash-Flow Check]
    E -- Verified Income --> D
    E -- Unverified / High DTI --> F[Graceful Decline / Offer Pay-in-Full]
    C -- High Fraud Signal --> G[Hard Block & Log Pattern]
    D --> H[Installment Schedule & Automated Reminders]
    H --> I{Payment Collected?}
    I -- Yes --> J[Reconcile Ledger & Close Loan]
    I -- No: Past Due --> K[Automated Dunning Workflow & Account Freeze]
```

---

## 3. Repository Contents
* **[Unit Economics & Margin Sensitivity Model](./Unit-Economics-Model.md):** Accounting breakdown of revenue per €100 order and how operational efficiency impacts net margin.
* **[Operational Risk & Exception Playbook](./Risk-and-Dunning-SOP.md):** Standard controls for checkout latency, payment failures, and merchant settlement reconciliation.
