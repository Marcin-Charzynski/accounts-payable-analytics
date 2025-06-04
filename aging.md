---
layout: page
title: Invoice Aging & Payment Timeliness
permalink: /aging/
---

## ⏳ Invoice Aging & Payment Timeliness

This section analyzes how effectively invoices are paid in relation to their due dates. Understanding payment behaviors helps control risk, maintain supplier relationships, and optimize cash flow.

---

### 📌 Key Metrics

- **Overdue Invoices** – How many invoices are past due? By how many days?
- **On-time vs Early Payments** – Are we paying suppliers too early or just in time?
- **DPO (Days Payable Outstanding)** – Average number of days the company takes to pay its invoices.
- **Vendors Frequently Paid Late** – Identifying patterns by supplier.

---

### 📁 Sample Dataset

> The data used here simulates a real-world Accounts Payable extract from a large enterprise system (e.g. iPower, SAP).  
> The dataset includes:  
> `Invoice ID`, `Vendor`, `Invoice Date`, `Due Date`, `Payment Date`, `Amount`, `Currency`.

*You can download the full CSV here:*  
📥 [Download Aging Dataset]({{ site.baseurl }}/data/invoice_aging_sample.csv)

---

### 📊 Visualization Preview

**Example charts (Power BI / Excel):**

- Aging buckets (0–30, 31–60, 61–90, 90+ days)
- Line chart of DPO over time
- Top 10 vendors by overdue amount
- Bar chart: % of on-time, early, late payments

<img src="{{ site.baseurl }}/assets/images/aging-dashboard-sample.png" alt="Invoice Aging Dashboard" class="rounded-xl shadow-md mt-4" />

---

### 🧠 Analytical Insight

> “Our average DPO is currently **58.2 days**, which is within acceptable limits.  
> However, **23%** of invoices are paid **after their due date**, with recurring late payments observed for Vendor X and Vendor Z.  
> Early payments represent **18%** of total invoices, which could be optimized to improve cash liquidity.”

---

### 🛠 Tools Used

- Excel (pivot tables, aging formulas)
- Power BI (date diff, conditional formatting, DAX)
- SQL (for data cleaning and bucket calculation)

---

*Return to [Home]({{ site.baseurl }}/).*
