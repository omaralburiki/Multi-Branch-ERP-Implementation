# Business Requirements Document (BRD)
## Multi-Branch ERP Implementation

---

## Document Control

| Field | Value |
|---|---|
| Document Title | Business Requirements Document, Multi-Branch ERP Implementation |
| Prepared By | Omar Ahmed Al-Buriki, Business Systems Analyst |
| Company | Mohd. Saeed Balbid Company |
| Project Duration | Jun 2020 to Aug 2021 |
| Related Prior Engagement | Inventory Gap Analysis & ERP Readiness (see companion dossier) |
| Document Status | Representative sample, reconstructed from project dossier |

---

## Table of Contents

1. Introduction and Purpose
2. Business Context and Problem Statement
3. Business Objectives
4. Scope
5. Stakeholders and RACI
6. Current State Summary (AS-IS)
7. Business Requirements
8. Functional Requirements
9. Business Rules Specification
10. Order Lifecycle
11. Approval Governance Matrix
12. Audit and Traceability Considerations
13. Assumptions and Constraints
14. Requirements Traceability and UAT Validation
15. Document Governance

---

## 1. Introduction and Purpose

This document defines the business and functional requirements for replacing the organization's legacy ERP system with a fully integrated platform covering finance, inventory, sales, purchasing, HR, CRM, and POS across 7 branches. It translates the operational gaps identified in the preceding Inventory Gap Analysis engagement into requirements a technical implementation team can build against, and defines the acceptance basis for UAT sign-off.

---

## 2. Business Context and Problem Statement

The organization operated a custom, in-house ERP across 7 branches that had never been designed for operational control. It recorded invoices but did not enforce stock deduction, reservation, credit limits, or approval governance. This gap had already been quantified and diagnosed in the preceding Inventory Gap Analysis engagement, which established the business case for replacing the system entirely.

The prior system's absence of operational control created 6 confirmed failure conditions:

| ID | Failure Condition |
|---|---|
| F-01 | No real-time inventory synchronization |
| F-02 | No stock reservation logic |
| F-03 | No negative-stock prevention |
| F-04 | No credit limit enforcement |
| F-05 | No approval governance with audit trail |
| F-06 | No reliable financial reporting |

These failures directly matched the root causes identified in the earlier gap analysis and required a full system replacement, not a patch.

---

## 3. Business Objectives

| ID | Objective |
|---|---|
| OBJ-01 | Replace the legacy system with a fully integrated ERP covering finance, inventory, sales, purchasing, HR, CRM, and POS |
| OBJ-02 | Eliminate phantom inventory and enforce real-time stock accuracy |
| OBJ-03 | Stop negative-stock selling and enforce credit limits automatically |
| OBJ-04 | Digitize the wholesale order fulfillment journey |
| OBJ-05 | Establish structured procurement and returns governance with a full audit trail |

---

## 4. Scope

### 4.1 In Scope

- 7 branches, 150+ users.
- 7 ERP functional modules: Finance, Inventory, Sales, Purchasing, CRM, HR, POS.
- Migration of 10,000+ SKUs.
- Company-wide order, inventory, and credit control business rules, not limited to a single branch type.
- Branch-type pricing (wholesale, supermarket, mini-market).
- Central and branch-level warehousing with inter-branch transfers.
- Batch and expiry tracking.
- Structured purchasing workflow, including supplier quotation comparison ahead of purchase order issuance.

### 4.2 Out of Scope

- Customer-segment pricing tiers. This capability was addressed separately in the later B2B E-commerce platform, not this ERP implementation.

---

## 5. Stakeholders and RACI

| Stakeholder | Role | Requirements Involvement |
|---|---|---|
| Sales | Requirement source | Order lifecycle, pricing at order entry |
| Finance | Requirement source, approval authority | Credit control rules, credit limit override approval, financial reporting |
| Warehouse | Requirement source | Stock reservation, deduction, goods receipt, batch/expiry tracking |
| Executive Management | Sponsor | Business direction, negative-stock override tier (CFO-level) |
| ERP Solution Provider | Technical delivery | Configuration and build against approved requirements; defect resolution |
| Business Systems Analyst (Omar) | Requirements owner | Gathered and verified requirements with all functions above; finalized BRD content for technical handoff; coordinated UAT against each requirement |

---

## 6. Current State Summary (AS-IS)

No structured business rules existed at any of the 7 branches prior to this project. Discrepancies, unauthorized negative-stock sales, uncontrolled credit exposure, and undocumented returns were managed manually, without system enforcement or audit trail. This state was directly confirmed during UAT (Section 14), where the prior system's absence of controls was validated point by point against each new rule.

---

## 7. Business Requirements

| ID | Requirement | Priority | Source |
|---|---|---|---|
| BR-01 | The system shall prevent order creation where requested quantity exceeds available stock | Must Have | Warehouse, Sales |
| BR-02 | The system shall block an order at point of sale when outstanding customer balance exceeds approved credit limit | Must Have | Finance |
| BR-03 | The system shall reserve confirmed stock against a draft order for a defined hold period | Must Have | Sales, Warehouse |
| BR-04 | The system shall deduct physical stock only at confirmed warehouse pick, not at order creation | Must Have | Warehouse |
| BR-05 | The system shall reject any transaction that would drive available stock below zero | Must Have | Executive Management, Finance |
| BR-06 | The system shall enforce a structured, time-bound, tiered returns approval process | Must Have | Finance, Sales |
| BR-07 | The system shall apply distinct price lists by branch type at order entry | Must Have | Sales |
| BR-08 | The system shall support both central and branch-level warehousing with tracked transfers | Must Have | Warehouse |
| BR-09 | The system shall support batch and expiry tracking with advance alerting | Must Have | Warehouse |
| BR-10 | The system shall support a structured purchasing workflow including supplier quotation comparison | Must Have | Purchasing |

---

## 8. Functional Requirements

| ID | Functional Requirement | Related Business Requirement |
|---|---|---|
| FR-01 | On order entry, the system shall check requested quantity against available stock and return the actual available quantity if insufficient, rather than allowing the order to proceed silently | BR-01 |
| FR-02 | On order entry, the system shall check the customer's outstanding balance against their approved credit limit and block the transaction if exceeded, pending Finance Manager override with a mandatory logged reason | BR-02 |
| FR-03 | On draft order creation, the system shall place a time-bound soft reservation on the requested stock, releasing it automatically at expiry or on manual release by a supervisor with a mandatory reason code and immutable log entry | BR-03 |
| FR-04 | On warehouse pick confirmation via barcode scan, the system shall deduct the picked quantity from available stock in real time | BR-04 |
| FR-05 | On any transaction that would result in negative available stock, the system shall reject the transaction unless overridden by CFO-level approval, with the override logged and timestamped | BR-05 |
| FR-06 | On a return request, the system shall require the original invoice, validate the 14-day return window, and route approval based on amount: cashier plus supervisor for amounts up to 1,000 SAR, branch manager for amounts from 1,001 to 10,000 SAR | BR-06 |
| FR-07 | On return processing, the system shall classify returned stock as sellable (returned to warehouse) or damaged (flagged to a separate location), and issue a refund via the original payment method | BR-06 |
| FR-08 | On order entry, the system shall apply the correct price list based on the branch's classification as wholesale, supermarket, or mini-market | BR-07 |
| FR-09 | The system shall maintain separate central and branch-level inventory records with tracked inter-branch transfers | BR-08 |
| FR-10 | On goods receipt, the system shall capture expiry dates via barcode scan and generate an alert 6 months ahead of expiry | BR-09 |
| FR-11 | The system shall support supplier quotation entry and comparison prior to purchase order issuance | BR-10 |
| FR-12 | The system shall log every override event (credit, reservation release, negative-stock) immutably, capturing user, reason, and timestamp | BR-02, BR-03, BR-05 |

---

## 9. Business Rules Specification

Each rule below is specified with its trigger, system action, and override path, matching how each was implemented and later validated in UAT.

### BRule-01: Hard Stock Block
- **Trigger:** Order creation where requested quantity exceeds available stock.
- **System Action:** Order creation is blocked; the system returns the actual available quantity.
- **Override:** None. This is an absolute block.

### BRule-02: Credit Limit Check
- **Trigger:** Order creation where customer's outstanding balance exceeds approved credit limit.
- **System Action:** Order is blocked at point of sale.
- **Override:** Finance Manager approval, with a mandatory logged reason.

### BRule-03: Soft Stock Reservation
- **Trigger:** Draft order creation.
- **System Action:** Confirmed stock is reserved for a defined hold period.
- **Override:** Automatic release at expiry, or manual release by a supervisor with a mandatory reason code and immutable log entry.

### BRule-04: Deduction at Pick Confirmation
- **Trigger:** Warehouse pick confirmed via barcode scan.
- **System Action:** Physical stock is deducted at this point, not at order creation.
- **Override:** None.

### BRule-05: Absolute Negative-Stock Prevention
- **Trigger:** Any transaction that would drive available stock below zero.
- **System Action:** Transaction is rejected at the system level.
- **Override:** CFO-level approval, logged and timestamped.

### BRule-06: Returns Approval Workflow
- **Trigger:** Return request submitted.
- **System Action:** Original invoice required; 14-day window from invoice date enforced. Approval tier is amount-based (see Section 11). Refund follows original payment method. Stock is classified sellable or damaged.
- **Override:** None beyond the defined approval tiers; every return event is logged immutably.

---

## 10. Order Lifecycle

The order lifecycle confirmed as actually implemented in the new ERP follows this sequence: the sales representative creates an order, including large orders of 100+ line items, which generates a draft invoice. The cashier processes payment, after which a final invoice is issued. The warehouse then picks and confirms the order via PDA barcode scan against the order, at which point BRule-04 executes and stock is deducted.

---

## 11. Approval Governance Matrix

| Override Type | Approval Authority | Logging Requirement |
|---|---|---|
| Credit limit override | Finance Manager | Mandatory logged reason |
| Reservation release beyond auto-expiry | Supervisor | Mandatory reason code, immutable log |
| Negative-stock override | CFO | Logged and timestamped |
| Return, up to 1,000 SAR | Cashier plus Supervisor | Immutable log |
| Return, 1,001 to 10,000 SAR | Branch Manager | Immutable log |

Order approval is enforced through these system checks rather than a manual sign-off chain.

---

## 12. Audit and Traceability Considerations

Every override path defined in Section 11 requires immutable logging, capturing at minimum the acting user, the reason provided, and a timestamp. This requirement was treated as non-negotiable across all 5 core business rules (BRule-01 through BRule-05) and the returns workflow (BRule-06), directly addressing failure condition F-05 (no approval governance with audit trail) identified in Section 2.

---

## 13. Assumptions and Constraints

- All 7 branches operate under a shared central ERP instance rather than independent local systems.
- Business rules apply company-wide; no branch-specific exceptions to the core rules described in Section 9.
- The ERP solution provider is responsible for technical configuration and build against these requirements; this document defines business intent, not system architecture.
- Customer-segment pricing was explicitly excluded from this project's scope and deferred to a later, separate digital commerce initiative.

---

## 14. Requirements Traceability and UAT Validation

| Requirement | AS-IS Gap Validated Against | UAT Outcome |
|---|---|---|
| BR-02 (Credit Control) | No per-customer credit limit assignment; manual customer search and aging report review required, with no automated alert | Confirmed: automated credit check functioning as specified |
| BR-03 (Stock Reservation) | No inventory reservation or available-quantity display at order creation | Confirmed: time-bound reservation and real-time availability display functioning as specified |
| BR-09 (Batch/Expiry Tracking) | No batch tracking capability in the prior system | Confirmed: barcode-scanned goods receipt, expiry recording, and 6-month advance alert functioning as specified |
| BR-07 (Branch-Type Pricing) | No price differentiation enforced by branch type | Confirmed: correct price list applied at order entry across wholesale, supermarket, and mini-market branches |

Defects identified during UAT were tracked through a ticketing system, combined with direct communication with the ERP solution provider for resolution.

---

## 15. Document Governance

Requirements in this document were gathered and verified directly with the stakeholders listed in Section 5, then finalized for technical handoff to the ERP solution provider. This finalization was based on direct stakeholder verification rather than a formal signature-based approval gate. Final acceptance of delivered functionality was confirmed through the UAT process described in Section 14, with defects tracked and resolved prior to go-live.
