# DukaanSaathi-Smart-Business-Management-System
Smart Business Management &amp; Inventory System (ADSA Mini-Project) built for Indian micro-retailers &amp; Kirana stores. Features an O(1) inventory lookup hash map, Min-Heap stock alerts, 0/1 Knapsack restock optimizer, C++17 core engine, MySQL 8.0 schema, and a responsive web frontend.
# DukaanSaathi – Smart Business Management System

**Domain:** Retail FinTech & Inventory Accounting for Indian MSMEs (Kirana, Grocery, Stationery & General Stores)

---

## Overview

**DukaanSaathi** replaces manual paper registers (*bahi-khata*) with a digital inventory, Point-of-Sale (POS), expense tracking, and automated Profit & Loss (P&L) accounting platform designed for Indian shopkeepers.

### Architecture Note
* **Interactive Web Prototype (`frontend/index.html`):** Fully functional client-side web application powered by a modular JavaScript ADSA & Accounting Engine with `localStorage` multi-store persistence.
* **Core C++17 Engine (`backend_cpp/dukaansaathi_adsa.cpp`):** Standalone C++17 implementation of all ADSA data structures, sorting/searching algorithms, financial calculators, and Dynamic Programming optimizers.
* **Relational Database (`database/schema.sql`):** Normalized MySQL 8.0 schema with foreign key constraints, analytical views, and ACID-compliant stored procedures.

---

## Core ADSA Algorithms Implemented

| Module | Data Structure / Algorithm | Time Complexity | Business Use Case |
| :--- | :--- | :--- | :--- |
| **Product Lookup** | Hash Table (`unordered_map`) | $O(1)$ average | Instant SKU/Product ID lookup during POS billing |
| **Inventory Ranking** | Merge Sort | $O(n \log n)$ | Sorting products by price, stock quantity, and unit profit |
| **Low-Stock Alerts** | Min-Heap Priority Queue | $O(n + k \log n)$ | Surfacing critical low-stock items at the top of the dashboard |
| **Smart Restock Advisor** | 0/1 Knapsack (Dynamic Programming) | $O(n \times W)$ | Selecting optimal restock items within a fixed working capital budget `₹W` |
| **Ledger Filtering** | Linear Range Scan | $O(n)$ | Daily, weekly, and monthly financial aggregation |

---

## Accounting & P&L Logic

DukaanSaathi strictly separates **Inventory Purchases** (asset additions) from **Cost of Goods Sold (COGS)** so net profit is never distorted by restocking:

$$\text{Revenue} = \sum (\text{Selling Price} \times \text{Quantity Sold})$$
$$\text{COGS} = \sum (\text{Unit Purchase Cost at Sale} \times \text{Quantity Sold})$$
$$\text{Gross Profit} = \text{Revenue} - \text{COGS}$$
$$\text{Net Profit / Loss} = \text{Gross Profit} - \text{Operating Expenses}$$
$$\text{Profit Margin (\%)} = \left(\frac{\text{Net Profit}}{\text{Revenue}}\right) \times 100$$

---

## How to Run

### 1. Run the Web Application
Open `frontend/index.html` directly in any modern browser (Chrome, Edge, Firefox) or serve it via VS Code **Live Server** / GitHub Pages. Click **"1-Click Demo Login (Sharma Kirana)"** to explore pre-loaded Indian retail data.

### 2. Compile & Run the C++17 ADSA Engine
```bash
cd backend_cpp
g++ -std=c++17 -O2 dukaansaathi_adsa.cpp -o dukaansaathi_adsa
./dukaansaathi_adsa
