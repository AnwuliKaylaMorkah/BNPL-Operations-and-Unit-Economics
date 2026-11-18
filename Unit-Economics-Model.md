# BNPL Unit Economics & Operational Sensitivity Analysis

## 1. Per-Transaction P&L Breakdown (Baseline vs. Optimized)
*Modelled on an average order value (AOV) of **€100** with a **4.0% Merchant Discount Rate (MDR)** and **1.5% late fee recovery**:*

| Financial / Operational Line Item | Baseline Ops (€) | Optimized Ops (€) | Operational Driver |
| :--- | :---: | :---: | :--- |
| **Gross Revenue (MDR + Late Fees)** | €5.50 | €5.10 | Lower late fees due to better upfront underwriting |
| **Payment Processing & Bank Rails** | (€0.85) | (€0.70) | Shift from card rails to SEPA/Open Banking direct debit |
| **Credit Bureau & KYC API Costs** | (€0.45) | (€0.30) | Tiered API calls (only query secondary bureaus on grey-zone users) |
| **Credit Loss / Default Provision** | (€2.40) | (€1.20) | **-1.2% default reduction** via Open Banking affordability checks |
| **Manual Review & Customer Support Ops** | (€0.75) | (€0.30) | **-55% manual queue volume** & self-service repayment portal |
| **Cost of Capital (Funding Warehouse)** | (€0.35) | (€0.35) | 45-day average receivable duration |
| **Net Operating Margin (€ / %)** | **€0.70 (0.70%)** | **€2.25 (2.25%)** | **+€1.55 (+155 bps) net profit per €100 order** |

---

## 2. Key Operational Takeaways
1. **Default Reduction Beats Fee Generation:** Even though gross revenue drops slightly (€5.50 to €5.10) because fewer customers incur late fees, cutting credit defaults in half more than triples net profit per transaction.
2. **Payment Rail Optimization:** Shifting recurring installment collections from debit/credit cards to automated bank-to-bank rails (SEPA Instant / Open Banking) saves €0.15 per order and eliminates involuntary churn from expired cards.
