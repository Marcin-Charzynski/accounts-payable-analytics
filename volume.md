---
layout: page
title: Invoice Volume & Value
permalink: /volume-value/
---

## 📦 Invoice Volume & Value

This section explores invoice volume and value trends across time — key for cost control, forecasting, and identifying anomalies in spending patterns.

---

### 🔍 Objectives

- Understand the volume of invoices processed over time (monthly, quarterly, annually).

- Monitor the total cost of invoiced purchases across time periods.

- Track the average invoice value to detect pricing or purchasing shifts.

- Identify spending anomalies and seasonal spikes that may signal unusual activity or cost control issues.

- Support budgeting, forecasting, and cost optimization efforts through data-driven insights.


---

### 🧾 Dataset Overview

This analysis is based on the same invoice-level dataset used in other sections:

| Table      | Description                                       | Key Columns                                       |
|------------|--------------------------------------------------|--------------------------------------------------|
| **Invoices** | Invoice-level details including amounts and dates | **InvoiceID** (PK), **VendorID**, **InvoiceDate**, **DueDate**, **PaymentDate**, **Amount** |

- **InvoiceID** — Unique invoice identifier  
- **VendorID** — Unique supplier/vendor identifier  
- **InvoiceDate** — Date the invoice was issued  
- **DueDate** — Date payment is due  
- **PaymentDate** — Actual payment date (can be blank if unpaid)  
- **Amount** — Invoice total value  

📥 [Download sample CSV]({{ site.baseurl }}/data/invoice_aging_sample.csv)

---

### 📊 Visual Highlights

Example insights from visualizations:

- 📅 Invoice count over time (e.g. by month)
- 💰 Monthly and quarterly invoice amounts
- 📉 Average invoice value trends
- 📌 Identification of cost spikes by category or vendor

<img src="{{ site.baseurl }}/assets/invoice-volume-value-dashboard.png" alt="Invoice Volume & Value Dashboard" class="rounded-xl shadow-md mt-4" />
<img src="{{ site.baseurl }}/assets/invoice-volume-value-pivot.png" alt="Invoice Volume & Value Pivot" class="rounded-xl shadow-md mt-4" />

---

### 💡 Key Findings (Sample)

> Over a 17-month period, the company processed **1,000 invoices**, with monthly volumes ranging between **3 to 71 invoices**.  
> The **average invoice value** was approximately **$10,130**, with noticeable cost peaks in **April** and **July**.  
> These peaks were driven by large, infrequent purchases from two key vendors.

---

### 🛠 Tools & Techniques

- **Power BI** 
- **Excel** 

---

### 🔧 Key DAX Measures

<details>
<summary>Show DAX Code</summary>

<pre><code class="language-dax">
TotalInvoiceAmount = 
SUM('Invoices'[Amount])

InvoiceCount = 
COUNT('Invoices'[InvoiceID])

AverageInvoiceValue = 
DIVIDE([TotalInvoiceAmount], [InvoiceCount], 0)

InvoiceMonth = 
FORMAT('Invoices'[InvoiceDate], "YYYY-MM")

InvoiceQuarter = 
"Q" & FORMAT('Invoices'[InvoiceDate], "Q") & " " & YEAR('Invoices'[InvoiceDate])

MonthlyInvoiceAmount = 
CALCULATE(
    [TotalInvoiceAmount],
    GROUPBY('Invoices', 'Invoices'[InvoiceMonth])
)

MonthlyInvoiceCount = 
CALCULATE(
    [InvoiceCount],
    GROUPBY('Invoices', 'Invoices'[InvoiceMonth])
)
</code></pre>

</details>
