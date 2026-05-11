# Retail Performance Power BI Dashboard — Complete Build Guide

This guide ensures you can build your Retail Performance Dashboard rapidly and structurally from the included `retail_dataset_45k.csv` dataset.

---

## What You'll Build

A 4-page Power BI dashboard featuring:
- **Page 1** – Executive Summary (High-level revenue and overarching business KPIs)
- **Page 2** – Customer Insights (Demographics like age/gender & geographics)
- **Page 3** – Product Performance (Sales by categories, sub-categories & impact of discounts)
- **Page 4** – Operations & Fulfillment (Shipping dynamics, returns, and payment methods)

---

## Prerequisites

- **Power BI Desktop** installed and open.
- The 4 retail project files located in your workspace:
  1. `retail_dataset_45k.csv`
  2. `Retail_Theme.json`
  3. `PowerQuery_M_Code_Retail.txt`
  4. `DAX_Measures_Retail.txt`

---

## STEP 1 — Apply the Theme

1. In your blank report, go to the **View** tab in the top ribbon.
2. Select the **Themes** dropdown → **Browse for themes**.
3. Locate `Retail_Theme.json` on your PC and click **Open**. 
*(This will set standard professional palette colors like blues, greens, and proper backgrounds).*

---

## STEP 2 — Load the Data with Power Query

We will use M-code to automatically parse custom date formats and derive helpful structural columns.

1. Go to the **Home** tab → **Get data** → **Blank query**.
2. Click **Advanced Editor** (Home tab).
3. Delete the default code, and paste the entire contents of `PowerQuery_M_Code_Retail.txt`.
4. **Important**: Verify line 10 in the code inside the editor ensures the `File.Contents("C:\...\retail_dataset_45k.csv")` points exactly to your file.
5. Click **Done**.
6. Rename the query text on the left sidebar to `retail_dataset_45k`. 
7. Click **Close & Apply** (top-left corner).

---

## STEP 3 — Set Sort Order Properties

Ensure months sort properly in order (Jan to Dec), rather than alphabetically.

1. Switch to the **Data view** (table icon on the left).
2. Click anywhere on the `MonthName` column.
3. In the top ribbon **Column tools** tab → **Sort by column** → click on `Month`.

---

## STEP 4 — Create the Measures Table

Let's maintain a neat 'Fields' pane by aggregating formulas in one place.

1. Click **Home** tab → **Enter data**.
2. Name the table `_Measures` and click **Load**. 
3. Go to the Fields pane, click the ellipsis (`...`) near Column1 in your new table and click **Hide**.
4. Open the `DAX_Measures_Retail.txt` file. For every block of code starting with `=` in that file:
   - Click `_Measures` to activate it. 
   - Under the **Modeling** tab, click **New measure**.
   - Paste the code (including the name) and hit Enter.

---

## STEP 5 — Build Page 1: Executive Summary

Name the first page tab **Executive Summary**.

### 1. KPI Strategy Cards (Place across the top)
Add a **Card** visual for each of the following (drag metric into the *Fields* box):
- `Total Revenue`
- `Total Orders`
- `Average Order Value (AOV)`
- `Return Rate %`

*Optional: Format -> Callout Value -> Apply conditional formatting (under fx) to Return Rate % utilizing your conditional `Return Rate Color` DAX measure.*

### 2. Line Chart: Monthly Revenue YoY
- **Visual**: Line chart
- **X-axis**: `MonthName`
- **Y-axis**: `Total Revenue`
- **Legend**: `Year`
- Format -> Title -> "Revenue Trend - Month over Month"

### 3. Donut: Category Contribution
- **Visual**: Donut chart
- **Legend**: `product_category`
- **Values**: `Total Revenue`
- Format -> Labels -> Turn on Data labels -> Detail labels: "Category, percent of total"

### 4. Bar Chart: Fulfillment Breakdown
- **Visual**: Stacked Bar chart
- **Y-axis**: `order_status`
- **X-axis**: `Total Orders`

---

## STEP 6 — Build Page 2: Customer Insights

Add a new page, name it **Customer Insights**.

### 1. Demographics Cards
- Add cards for `Unique Customers` and `Average Customer Rating`.

### 2. Bar Chart: Revenue by Segment & Gender
- **Visual**: Clustered Column Chart
- **X-axis**: `customer_segment`
- **Y-axis**: `Total Revenue`
- **Legend**: `customer_gender`

### 3. Column Chart: Age Distribution
- **Visual**: Stacked Column Chart
- **X-axis**: `Age Group` (derived from M-code)
- **Y-axis**: `Total Revenue`

### 4. Map Visual: Revenue by State
- **Visual**: Map (Globe symbol)
- **Location**: `customer_state`
- **Bubble size**: `Total Revenue`

---

## STEP 7 — Build Page 3: Product Performance

Add a new page, name it **Product Insights**.

### 1. Matrix: Product Hierarchy drill-down
- **Visual**: Matrix
- **Rows**: `product_category` and below it place `product_sub_category`.
- **Values**: `Total Quantity Sold`, `Total Orders`, `Total Revenue`, `Average Order Value (AOV)`.
*(Allows users to hit the `+` button in visual to expand standard categories to actual item sub-buckets)*

### 2. Scatter Plot: The Impact of Discount
- **Visual**: Scatter chart
- **Values**: `product_sub_category` (drag into Values/Details area, select 'Don't summarize').
- **X-axis**: `Average Discount %`
- **Y-axis**: `Total Quantity Sold`
- **Size**: `Total Revenue`

*(This visual checks whether throwing deep percentage discounts effectively inflates volumes bought).*

---

## STEP 8 — Build Page 4: Operations & Fulfillment

Add a new page, name it **Operations**.

### 1. Speed KPI Cards
- Add cards for `Average Shipping Duration` and `Total Shipping Cost`.

### 2. Bar Chart: Shipping Modes
- **Visual**: Clustered Bar chart
- **Y-axis**: `ship_mode`
- **X-axis**: `Total Orders`
- **Legend**: `order_status`

### 3. Donut Chart: Payments Used
- **Visual**: Donut or Pie
- **Legend**: `payment_method`
- **Values**: `Total Revenue`

---

## STEP 9 — Add Global Slicers

Place slicers at the top right of the Executive Page to allow user toggling contexts, and set them to carry over to other sheets.

1. **Slicer 1**: `Year`
2. **Slicer 2**: `customer_segment`

*(To sync across pages: Navigate to **View tab** → **Sync Slicers** → Ensure checkboxes for visible and sync are ticked for pages 1-4 for those slicers.)*

---

## Finish
1. Turn on Modern Visual Headers via **File → Options and Settings → Options → Current File → Report Settings**.
2. Save your project `Retail_Dashboard.pbix` and enjoy your highly dynamic layout!