# Operational Risk, Settlement & Dunning Controls

## 1. Checkout Latency & API SLA Controls
* **Target Latency:** End-to-end credit and fraud decisioning must complete in **< 1,200 milliseconds** to prevent cart abandonment.
* **Fallback Rule:** If a third-party credit bureau API times out (>800ms), the decision engine automatically falls back to internal device-fingerprinting and historical repayment data for returning users.

## 2. Merchant Settlement & Reconciliation
* **T+1 Net Settlement:** Merchants are settled on the next business day (`Gross Order Value` minus `MDR %` minus `Refunds/Chargebacks`).
* **Daily Ledger Reconciliation:** Automated finance script matches daily payout batches against ERP general ledger clearing accounts; any variance > €1.00 triggers an automated FinOps investigation ticket.

## 3. Automated Dunning (Collections) Cadence
To maximize recovery without damaging customer retention:
* **T - 2 Days (Pre-Due):** Automated push notification and SMS reminder confirming upcoming auto-debit.
* **Day 0 (Payment Failure):** Immediate soft retry after 6 hours (to clear temporary bank network timeouts) + account spending limit frozen.
* **Day +3 (First Hard Retry):** Automated retry aligned with standard payroll clearing cycles + option to self-reschedule once within 7 days.
* **Day +14 (Escalation):** Account restricted from new checkouts; routed to structured repayment plan workflow before external collections.
