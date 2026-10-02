# olist-ecommerce-powerbi-dashboard
# 🛒 Olist E-Commerce Analytics Dashboard

End-to-end analytics project on the Olist Brazilian e-commerce dataset using **PostgreSQL** and **Power BI (DirectQuery)**.

## 📌 Project Overview
This project takes raw Olist CSV data through database design, validation, indexing and SQL BI views, and ends with an interactive 8-page Power BI dashboard. It helps answer questions about sales, products, customers, delivery performance, reviews, payments and sellers.

## 🛠 Tech Stack
- **Database:** PostgreSQL (pgAdmin)
- **BI Tool:** Power BI Desktop (DirectQuery)
- **Languages:** SQL, DAX
- **Dataset:** [Olist Brazilian E-Commerce Dataset (Kaggle)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

## 📂 Repository Structure
```
├── dashboard/        # Power BI file (.pbix)
├── sql/              # SQL scripts (tables, load, validation, indexes, views)
├── screenshots/      # Dashboard page screenshots
├── dax/              # DAX measures
└── README.md
```

## 🔄 Project Workflow (Step by Step)

### Part 1: PostgreSQL (Data Engineering)
1. **Download dataset:** Downloaded the Olist dataset (ZIP) from Kaggle and extracted all CSV files.
2. **Create database:** Created a PostgreSQL database named `olist_db`.
3. **Create raw tables:** Created raw tables for orders, order_items, customers, products, sellers, payments, reviews and category_translation.
4. **Load data:** Loaded the CSV files into the raw tables using `COPY` / pgAdmin import.
5. **Validate data:** Checked row counts, null values, sample records and key uniqueness.
6. **Create indexes:** Added indexes on join and filter columns (`order_id`, `customer_id`, `product_id`, `seller_id`, `purchase_timestamp`) to improve query speed.
7. **Create BI views:** Built cleaned and optimized views for reporting, mainly `bi_fact_sales` plus optional dimension views.
8. **Test views:** Ran SELECT queries to confirm there is no duplication and that totals are correct.

### Part 2: Power BI (Data Modeling and Visualization)
9. **Connect to PostgreSQL:** Power BI Desktop → Get Data → PostgreSQL → **DirectQuery**.
10. **Load only BI views:** Loaded `bi_fact_sales` and the optional dimension views, not the raw tables.
11. **Create DimDate:** Created a date table (Import mode) and related it to `purchase_date`.
12. **Build relationships:** Set up relationships between the fact and dimension tables and confirmed the storage mode.
13. **Write DAX measures:** Revenue, Orders, Customers, AOV, YoY %, On-time Delivery %, Average Rating, etc.
14. **Design report pages:** Overview, Sales, Products, Customers, Logistics, Reviews, Payments, Sellers.
15. **Optimize performance:** Avoided heavy visuals, limited high-cardinality columns, reduced cross-filtering and used Performance Analyzer to find slow visuals.

## 📊 Dashboard Pages
| Page | What it shows |
|------|---------------|
| Overview | Key KPIs: revenue, orders, customers, AOV |
| Sales | Sales trends over time, YoY growth |
| Products | Top categories and products |
| Customers | Customer distribution and behavior |
| Logistics | Delivery performance, On-time % |
| Reviews | Rating trends and review scores |
| Payments | Payment types and installments |
| Sellers | Seller performance |

## 🖼 Dashboard Preview
[Overview]<img width="1151" height="650" alt="image" src="https://github.com/user-attachments/assets/9d87725c-5564-42cc-b79d-d3c90ce59a7b" />

[Sales]<img width="1153" height="645" alt="image" src="https://github.com/user-attachments/assets/3dec55ff-4114-49fa-a4f3-084e2a4729d4" />

[Products]<img width="1157" height="647" alt="image" src="https://github.com/user-attachments/assets/c61c1539-71cc-4a54-99ce-20dfb7eeed55" />

[Customers]<img width="1151" height="647" alt="image" src="https://github.com/user-attachments/assets/0d0f3183-3c42-4488-9db3-748147405b70" />

[Logistics]<img width="1158" height="645" alt="image" src="https://github.com/user-attachments/assets/06525927-5293-4776-871e-804cbedd11ef" />

[Reviews]<img width="1157" height="652" alt="image" src="https://github.com/user-attachments/assets/c4af3024-c4b4-4a21-aabb-fc3b7ccb340f" />

[Payments]<img width="1162" height="648" alt="image" src="https://github.com/user-attachments/assets/61cdb4b4-add9-43d4-8837-5725a34e91c3" />

[Sellers]<img width="1157" height="648" alt="image" src="https://github.com/user-attachments/assets/c348ed50-910f-41aa-9329-d857a15923b8" />
