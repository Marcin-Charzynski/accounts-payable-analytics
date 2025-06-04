---
layout: page
title: Invoice Timeliness
permalink: /aging/
---

## 📅 Invoice Timeliness

This section focuses on how promptly invoices are paid in relation to their due dates — a critical factor in maintaining supplier trust and managing working capital.

---

### 🔍 Objectives

- Assess the proportion of invoices paid **on time**, **early**, or **late**.
- Quantify delays using aging buckets (e.g., 1–30, 31–60, 61+ days late).
- Identify vendors or time periods with consistent late payments.
- Support improvements in **AP processes** and **cash flow efficiency**.

---

### 🧾 Dataset Overview

This analysis is based on a sample of invoice-level records including:

- `Invoice ID`
- `Vendor`
- `Invoice Date`
- `Due Date`
- `Payment Date`
- `Amount`
- `Currency`

📥 [Download sample CSV]({{ site.baseurl }}/data/accounts_payable_sample.csv)

---

### 📊 Visual Highlights

Example insights from visualizations:

- ✅ % of invoices paid on time, early, or late
- 🕒 Aging distribution of overdue invoices
- 📈 Monthly trend in payment timeliness
- 🚩 Vendors with the highest late payment ratios

<img src="{{ site.baseurl }}/assets/invoice-timeliness-dashboard.png" alt="Invoice Timeliness Dashboard" class="rounded-xl shadow-md mt-4" />

---

### 💡 Key Findings (Sample)

> “Out of 1,200 invoices analyzed, **26%** were paid **late**, with an average delay of **12.5 days**.  
> Vendor ‘ABC Logistics’ had over **40%** of their invoices paid after the due date.  
> Early payments accounted for **15%**, potentially reducing available cash unnecessarily.”

---

### 🛠 Tools & Techniques

- **Excel** – payment aging formulas, pivots  
- **SQL** – days late calculation, categorization  
- **Power BI** – conditional formatting, DAX filters

---

[← Back to Overview]({{ site.baseurl }}/)
