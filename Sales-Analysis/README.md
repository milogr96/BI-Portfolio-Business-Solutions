# 📈 Sales Performance & Revenue Tracking

Power BI dashboard built from a **Zakidata (DaxusLatam) masterclass** and extended with my own analytical layer: a date table, time-intelligence measures, a metric selector, store × month heat map and Pareto (ABC) analysis by store and by product.

🇪🇸 **[Leer en español](README.es.md)**

---

## 🎯 Business questions

1. How are billing, commission and order volume evolving month by month?
2. Which stores and products sustain the revenue, and how concentrated is it?
3. Where are the weak spots (stores or months) that need commercial attention?

## 🧭 What is mine vs. what comes from the masterclass

| Component | Origin |
|---|---|
| Page 1 layout (background, cards, map, product filter, monthly chart, store table) | Zakidata masterclass template |
| Page 2 design and all of its visuals | **My own work** |
| Date table (`Calendario`) and time-intelligence measures | **My own work** |
| Metric selector (field parameter), MoM variation by metric | **My own work** |
| Store × month heat map | **My own work** |
| Pareto / ABC analysis (stores and products) and 80% KPIs | **My own work** |

Some static texts on page 1 are part of the template's background image (some labels appear in Portuguese). They are left unmodified on purpose.

## 🖼️ Screenshots

<!-- Sube las capturas a la carpeta 2.Screenshots y ajusta los nombres de archivo si son distintos -->
| Page 1 – Overview | Page 2 – Detail & Pareto |
|---|---|
| ![Page 1](2.Screenshots/page 1.png) | ![Page 2](2.Screenshots/page 2.png) |

## 📊 Dashboard content

### Page 1 – Overview (template)
- KPI cards: billing, total orders, commission.
- Map of store locations in Brazil.
- Product filter, monthly billing chart and billing share by store.

### Page 2 – Detail & concentration (own work)
- **Metric selector** (Commission / Orders / Billing) driving the by-store bar chart and the monthly variation chart.
- **Monthly variation (MoM %)** for the selected metric.
- **Heat map store × month** of billing (color scale from `#F8EFEE` to `#D0948B`).
- **Pareto charts** by store and by product, classified A / B / C.
- **Concentration KPIs:** share of stores and products that generate 80% of billing.

## 🔍 Key findings (2023 data)

- **Revenue is fairly spread out:** 5 of 8 stores and 5 of 8 products are needed to reach 80% of billing. There is no strong dependency on a single store or product.
- **Store classification:** stores 2, 4, 5, 6 and 7 are class A; store 3 is class B; stores 1 and 8 are class C.
- **Product classification:** Billetera, Bolso, Maleta, Mochila and Tennis are class A; Audífonos and Botella are class B; Gorra is class C.
- **Store 8** has very low volume and recorded no sales of any product in July and December (visible as blank cells in the heat map).
- **Month-to-month swings are large:** for example, the variation shows peaks above +20% and drops close to -18% within the same year.

## 🧮 KPI dictionary

| KPI | Unit | Definition | Decision it supports |
|---|---|---|---|
| `Facturacion_total` | Currency of the dataset | Sum of billing | Overall commercial performance |
| `Comisión` | Currency of the dataset | Sum of commissions | Cost of sales and incentive planning |
| `Total_Pedidos` | Count (orders) | Number of orders | Demand and operational load |
| `Facturacion YTD` / `MTD` | Currency | Billing accumulated in the year / month to date | Progress against the period |
| `Variación MoM % Métrica` | % | Change vs. previous month for the selected metric | Detect acceleration or slowdowns |
| `Pareto % Acum` (store / product) | % | Cumulative share of billing, ranked from highest to lowest | Visualize concentration |
| `Clase ABC` (store / product) | A / B / C | A: first 80% of billing, B: up to 95%, C: the rest | Prioritize attention and resources |
| `% Tiendas / Productos que generan el 80%` | % | Class A items ÷ items with sales | Measure revenue concentration risk |

## 🧱 Data model

- **Fact table:** `RegistroVentas` (orders, billing, commission, order date).
- **Dimensions:** `Tiendas`, `Productos`, `Calendario`.
- `Calendario` is a calculated date table marked as the model's date table and related to the order date.
- Measures are organized in a dedicated `_Medidas` table.

## 🛠️ Tech stack

Power BI Desktop · DAX (calculated date table, time intelligence, Pareto/ABC with `ALLSELECTED`, `FILTER` and `SUMX`, field parameters) · Conditional formatting and custom color scales.

## ⚠️ Limitations

- The dataset covers **only 2023**, so year-over-year comparisons are not possible.
- It is a practice dataset provided by the masterclass, not real company data.
- The Pareto analysis is computed on billing and does not react to the metric selector by design.

## 📂 Files

- `1.Dashboard/` – Power BI report (`.pbix`).
- `2.Screenshots/` – screenshots of both pages.
- `3.Dax/` – DAX measures and calculated date table.
- `4.Data/` – source data used by the report.

## 🙌 Credits

Page 1 design and base dataset: Zakidata (DaxusLatam) masterclass. Everything listed under "My own work" was developed by me on top of that base.
