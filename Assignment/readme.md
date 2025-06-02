# Microsoft Fabric Masterclass: End-to-End Analytics Project

## 🧠 Objective

This assignment will challenge you to apply your knowledge of Microsoft Fabric to build a comprehensive analytics solution for a simulated business scenario. You will ingest relational data files, transform them in the Lakehouse, perform analysis using SQL and DAX, and create interactive Power BI reports — culminating in a demonstration of your end-to-end solution.

## 🏪 Scenario

You’ve been brought on as a data analytics consultant by **FreshMart Grocers**, a mid-sized grocery retail chain that operates across several cities and countries. Their leadership is seeking clarity on sales performance, regional dynamics, employee productivity, and customer behavior. The business has been collecting data in structured CSV files, but lacks a unified, insightful reporting system.

FreshMart’s management wants you to help them:

- Integrate their various data files into a centralized data environment.
- Uncover trends in product sales and regional revenue.
- Analyze employee contributions and customer demographics.
- Build an intuitive dashboard that informs business decisions.

You are expected to design a modern data analytics solution using Microsoft Fabric.

---

## ✅ Suggested Learning Outcomes

By completing this project, you should be able to:

- Design and implement an end-to-end analytics workflow in Microsoft Fabric.
- Build and manage Lakehouse and SQL Warehouse environments.
- Perform ETL/ELT operations using Fabric Notebooks.
- Construct semantic models and write efficient DAX measures.
- Build insightful and interactive Power BI dashboards for business users.
- Translate raw datasets into meaningful business intelligence.

---

## 📦 Data Sources

FreshMart has shared **seven structured CSV files**, each representing a table within a relational schema. These files contain transactional, customer, product, and regional data — all essential for building a star-schema model.

You can find the dataset here:  
🔗 [Grocery Sales Dataset on Kaggle](https://www.kaggle.com/datasets/andrexibiza/grocery-sales-dataset)

### 🗃️ Dataset Overview

| **File Name**       | **Description**                                             | **Suggested Role**     |
|---------------------|-------------------------------------------------------------|-------------------------|
| `sales.csv`         | Historical transaction records (product, quantity, price, date) | Fact Table              |
| `products.csv`      | Product details such as name and category                    | Dimension Table         |
| `employees.csv`     | Information on employees handling the sales                  | Dimension Table         |
| `customers.csv`     | Customer demographic data                                    | Dimension Table         |
| `categories.csv`    | Mapping of product categories                                | Dimension Table         |
| `cities.csv`        | City-level data including store locations                    | Dimension Table         |
| `countries.csv`     | Country mapping for each city                                | Dimension Table         |

---

### 🧠 Understanding the Data & Designing the Schema

To successfully load and relate the tables:

1. **Download and explore** each CSV file from the Kaggle dataset.
2. Review the column names and data types to understand what each table represents.
3. Use the **data dictionary** (if provided in the dataset or inferred through inspection) to:
   - Identify primary and foreign keys
   - Understand the relationships between tables
4. Create a **star schema diagram**, with `sales.csv` as the central fact table and other tables acting as dimensions.

> 💡 *Tip: Use tools like draw.io, dbdiagram.io, or pen and paper to sketch your schema before building it in Microsoft Fabric.*

---

## 🧭 Tasks & Guidance

You are expected to work through the following phases — each phase will introduce challenges that naturally lead you to load, relate, analyze, and visualize the data using Microsoft Fabric.

### 🔹 Phase 1: Load & Explore the Data (Lakehouse)

- Ingest all seven CSV files into your Fabric Lakehouse.
- Familiarize yourself with each table and understand the relationships.
- Create a data dictionary for your own use (or as part of the final deliverable).

**Reflection Prompt**:
- How do these files relate to one another? Sketch or describe the schema in terms of facts and dimensions.

---

### 🔹 Phase 2: Provision a SQL Warehouse

- Create a Warehouse on top of your Lakehouse.
- Use the shortcut feature or copy the tables directly to your warehouse.
- Confirm that all dimension and fact tables are properly loaded.

> 📌 This separation supports performance optimization and access control, common in production-grade environments.

---

### 🔹 Phase 3: ETL/ELT with Notebooks

- Create a Fabric Notebook (e.g., PySpark or Scala).
- Load the sales table from the Warehouse into a Spark DataFrame.
- Perform the following transformations:
  - Calculate `Revenue = Quantity * UnitPrice` (if not already present)
  - Extract `Year` and `Month` from `OrderDate`
  - Handle missing values or perform data type conversions
- Save the cleaned/transformed data back into a new table in your Warehouse (e.g., `SalesFact_Transformed`)

**Optional Challenge**:
- Add a logic column to flag "High-Value Transactions" (e.g., revenue above a certain threshold).

---

### 🔹 Phase 4: Transform & Analyze (SQL Endpoint)

Use SQL queries (on your Warehouse) to explore business questions such as:

1. Which products generate the most revenue and in which categories?
2. Which employees are handling the most transactions?
3. What is the revenue per country and city?
4. How do customer demographics relate to product types purchased?
5. Which categories have the highest sales volume over time?

> 🛠 Tip: Create SQL views or transformed tables to support your analysis and modeling.

---

### 🔹 Phase 5: Build a Semantic Model

- Build a star schema model with:
  - `SalesFact_Transformed` as the fact table
  - Dimension tables: products, customers, employees, categories, cities, countries
- Create DAX measures for:
  - Total Sales Revenue
  - Total Quantity Sold
  - Average Sale per Transaction
  - Monthly Sales Trend
  - Top Categories by Revenue
  - Employee Productivity

**Optional**:
- Add calculated columns to segment customers (e.g., high-value vs. low-value) based on total purchase volume.

---

### 🔹 Phase 6: Build a Power BI Dashboard

Design a report that communicates insights clearly to a non-technical stakeholder.

**Include Visuals:**
- Monthly sales trend
- Top-selling products and categories
- Sales by region (country & city)
- Employee leaderboard
- Customer breakdown (demographics & geography)

**Include Slicers:**
- Time period (month/year)
- Country or city
- Product category
- Employee

**Bonus:**  
Add KPIs or cards showing:
- Total Sales  
- Total Orders  
- Average Order Value  

---

## 📥 Submission Tips

To ensure your project is well-received and easy to assess:

1. **Fabric Workspace**  
   - Share access with the instructor/team.  
   - Name your workspace and assets clearly (e.g., `FreshMart_Sales_Analysis`).

2. **Documentation Report**  
   - Briefly explain your overall approach.  
   - Mention key challenges and how you overcame them.  
   - Highlight major insights and why they matter to FreshMart’s leadership.

3. **Presentation/Demo**  
   - Walk through your pipeline in 10–15 minutes.  
   - Clearly show the flow from raw CSVs → Lakehouse → SQL Warehouse → Notebook → Semantic Model → Dashboard.  
   - Use visuals and keep explanations clear for non-technical audiences.

> ✅ *Pro Tip: Rehearse your demo with a friend or colleague to refine your flow and time management.*

---

## 🚀 Submission Instructions

After completing the assignment, please submit your project by creating your own repository through our **GitHub Classroom** link below.

### How to Submit:
1. Click the GitHub Classroom invitation link below.
2. Accept the assignment and create your personal repository.
3. Clone your repository locally and add your completed project files following the required folder structure.
4. Commit and push your changes back to your GitHub Classroom repo.
5. Confirm that your final submission includes all deliverables in the correct folders.
6. Submit your Repository via the Submission Link : https://base.zinduaschool.com/form/F-Qp-jhKbNj5-MwIlo_C_ez0RAlZMMFHGQELakdhOW8

### GitHub Classroom Invitation Link:
[Accept the Assignment and Create Your Repo](https://classroom.github.com/a/NWsHXFDH)

---

Thank you, and good luck with your project! 🎉

Happy analyzing! 💡
