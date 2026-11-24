# Multi-Branch ERP Implementation

Replacing a 7-branch distributor's legacy system with a full ERP, and designing the order, stock, and credit rules the old system never had.

**FMCG retailer and wholesaler, Saudi Arabia · Jun 2020 – Aug 2021 · Role: ERP Business Analyst**

## Why the system had to change

The company's in-house system recorded invoices and not much else. It did not reserve stock, stop negative stock, enforce credit limits, or keep an audit trail of approvals. The [gap analysis](https://github.com/omaralburiki/Inventory-Gap-Analysis-ERP-Readiness) done before this project had already shown what that was costing the business, so the decision was to replace the system rather than patch it.

Scope: 7 branches, 150+ users, 7 modules (Finance, Inventory, Sales, Purchasing, CRM, HR, POS), and more than 10,000 SKUs migrated.

## My role

I worked on the business side of the rollout from requirements through stabilization, and shared the business-side project management with a colleague. Together we ran the meetings with the ERP provider and the internal departments, tracked risks, issues, and delays, verified deliverables, and were responsible for getting the system ready for go-live.

I gathered requirements from Sales, Finance, Warehouse, and Executive Management, wrote the BRD and functional requirements, and designed the business rules together with the people who would work under them. The ERP solution provider configured the system against the BRD. I ran UAT against each rule, trained users, coordinated master data migration, supported go-live in all 7 branches, and provided on-site hypercare.

## The rules

| Rule | What the system does | Who can override |
|---|---|---|
| Hard stock block | Stops an order when the quantity exceeds available stock and shows what is available | Nobody |
| Credit limit check | Blocks the order when the customer's balance is over the approved limit | Finance Manager, with a logged reason |
| Soft stock reservation | Holds stock against a draft order for a set period, then releases it | Supervisor, with a reason code |
| Deduction at pick | Deducts stock only when the warehouse confirms the pick by barcode scan | Nobody |
| Negative-stock prevention | Rejects any transaction that would take stock below zero | CFO, logged and timestamped |
| Returns approval | Original invoice and a 14-day window required; approval depends on the amount | Supervisor for the lower tier, branch manager for the higher tier |

None of these existed in the old system, and every override is logged.

## After go-live

Go-live was not smooth. Orders with 100+ lines were slow to enter, users made mistakes while they learned the system, and work piled up at the handoffs between sales, cashier, and warehouse. During stabilization I enforced the Sales, Cashier, Warehouse flow as the only path for an order and made barcode scanning mandatory at picking, with the system rejecting the wrong item or quantity. Once things settled, day-to-day ownership of inventory control and finance alignment moved to those departments, and my role became monitoring and coordination.

## Outcome

The ERP went live in all 7 branches, and credit limits, stock reservation, and negative-stock prevention were enforced company-wide for the first time.

## Related projects

This is part 2 of the company's ERP work. Part 1, the [Inventory Gap Analysis & ERP Readiness](https://github.com/omaralburiki/Inventory-Gap-Analysis-ERP-Readiness), built the business case. This ERP later became the source of truth for stock and prices on the [B2B E-commerce platform](https://github.com/omaralburiki/B2B-E-commerce-Implementation).

## Documents

- [Full case study](docs/Case-Study.md): the implementation lifecycle, order lifecycle, UAT findings, and diagrams.
- [BRD](docs/BRD.md): business and functional requirements, rule specifications, and the approval matrix. This is a representative version; the original belongs to the company.
