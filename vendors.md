---
layout: page
title: Vendor Analysis
permalink: /vendor-analysis/
---

## 🧾 Vendor Analysis

This section focuses on supplier-level insights — identifying who the company spends the most with, how frequently they invoice, and what opportunities exist for renegotiation or optimization.

---

### 🔍 Objectives

- Identify vendors with the **highest total spend**.
- Determine which vendors issue the **most invoices**.
- Count the number of **unique vendors**.
- Compare **payment terms** or negotiated conditions across suppliers.

---

### 🧾 Dataset Overview

All metrics are derived from the invoice-level dataset containing supplier details:

| Table      | Description                                       | Key Columns                                       |
|------------|--------------------------------------------------|--------------------------------------------------|
| **Invoices** | Invoice-level details including vendor and amount | **InvoiceID** (PK), **VendorID**, **InvoiceDate**, **DueDate**, **PaymentDate**, **Amount** |

- **VendorID** — Unique supplier/vendor identifier  
- **InvoiceDate** — Date the invoice was issued  
- **Amount** — Invoice total value  
- **DueDate / PaymentDate** — Used to infer payment terms and behaviors  

📥 [Download sample CSV]({{ site.baseurl }}/data/invoice_aging_sample.csv)

---

### 📊 Visual Highlights

Example insights from visualizations:

- 🏆 Top vendors by total spend
- 📈 Vendors by invoice frequency
- 🧮 Count of unique suppliers
- 💸 Comparison of vendor payment behaviors and conditions

<img src="{{ site.baseurl }}/assets/vendor-analysis-dashboard.png" alt="Vendor Analysis Dashboard" class="rounded-xl shadow-md mt-4" />

---

### 💡 Key Findings (Sample)

> The company worked with **50 unique suppliers** over the reporting period.  
> Just **5 vendors** accounted for **47%** of total invoice value.  
> Vendor ‘ACME Corp’ issued the highest number of invoices (**124**) and was responsible for the single largest invoice (**$18,900**).  
> Several high-value vendors offer **net 30 terms**, but early payment discounts were not consistently utilized.

---

### 🛠 Tools & Techniques

- **Power BI** – Grouping by vendor, aggregation, filtering by vendor size  
- DAX – Unique counts, top N analysis, vendor-specific metrics  

---

### 🔧 Key DAX Measures

<details>
<summary>Show DAX Code</summary>

<pre><code class="language-dax">
TotalSpendPerVendor = 
SUMX(
    VALUES('Invoices'[VendorID]),
    CALCULATE(SUM('Invoices'[Amount]))
)

InvoiceCountPerVendor = 
CALCULATE(
    COUNT('Invoices'[InvoiceID]),
    ALLEXCEPT('Invoices', 'Invoices'[VendorID])
)

UniqueVendors = 
DISTINCTCOUNT('Invoices'[VendorID])

TopVendorsBySpend = 
TOPN(5, 
    SUMMARIZE(
        'Invoices', 
        'Invoices'[VendorID], 
        "TotalSpend", SUM('Invoices'[Amount])
    ),
    [TotalSpend],
    DESC
)
</code></pre>

</details>
