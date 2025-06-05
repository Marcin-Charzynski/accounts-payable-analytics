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


| Table      | Description                                       | Key Columns                                       |
|------------|-------------------------------------------------|--------------------------------------------------|
| **Invoices** | Invoice-level details including payment and due dates | **InvoiceID** (PK), **VendorID**, **InvoiceDate**, **DueDate**, **PaymentDate**, **Amount** |

- **InvoiceID** — Unique invoice identifier  
- **VendorID** — Unique supplier/vendor identifier  
- **InvoiceDate** — Date the invoice was issued  
- **DueDate** — Date payment is due  
- **PaymentDate** — Actual payment date (can be blank if unpaid)  
- **Amount** — Invoice total value  

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
> Vendor ID ‘12345’ had over **40%** of their invoices paid after the due date.  
> Early payments accounted for **15%**, potentially reducing available cash unnecessarily.”

---

### 🛠 Tools & Techniques

- **Excel** – payment aging formulas, pivots  
- **Power BI** – DAX measures, filters  

---

### 🔧 Key DAX Measures

<details>
<summary>Show DAX Code</summary>

<pre><code class="language-dax">
DaysLate = DATEDIFF('Invoices'[DueDate], 'Invoices'[PaymentDate], DAY)

LateBucket = 
SWITCH(
    TRUE(),
    'Invoices'[DaysLate] <= 0, "On Time / Early",
    'Invoices'[DaysLate] <= 30, "1–30 days",
    'Invoices'[DaysLate] <= 60, "31–60 days",
    "61+ days"
)

TotalInvoices = COUNT('Invoices'[InvoiceID])

LateInvoices = 
CALCULATE(
    COUNT('Invoices'[InvoiceID]),
    'Invoices'[DaysLate] > 0
)

OnTimeOrEarlyInvoices = 
CALCULATE(
    COUNT('Invoices'[InvoiceID]),
    'Invoices'[DaysLate] <= 0
)

PercentLate = DIVIDE([LateInvoices], [TotalInvoices], 0)

PercentOnTime = DIVIDE([OnTimeOrEarlyInvoices], [TotalInvoices], 0)

InvoiceMonth = FORMAT('Invoices'[InvoiceDate], "YYYY-MM")
</code></pre>

</details>
