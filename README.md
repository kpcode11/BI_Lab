**Title : MINI – PROJECT - BI Report** 

**Problem Definition :** 
Modern retail businesses generate massive amounts of transaction data but struggle to convert it into actionable insights. The core problem is identifying which specific customer segments, geographical regions, and product sub-categories drive the highest profitability. Furthermore, the business needs to understand the hidden costs of operations—specifically, how discount campaigns impact product return rates, and how shipping delays affect overall customer satisfaction.

**Software Used :** 
*   **Microsoft Power BI Desktop:** Used for Data Extraction, Transformation (via M-Code in Power Query), Data Modeling (DAX Measures), and building interactive Visualizations.
*   **Notepad / VS Code:** Used for scripting DAX measures and custom JSON UI themes.

**Description :** 

**a) Data mining task needed,**
*   **Exploratory Data Analysis (EDA):** Identifying sales trends, seasonal peaks, and Year-over-Year (YoY) revenue growth.
*   **Customer Segmentation:** Grouping customers by Age, Gender, and calculating "Revenue per Customer" to identify high-value consumer profiles.
*   **Correlation & Behavioral Analysis:** Analyzing the relationship between "Shipping Duration" and "Customer Rating," as well as "Discount Percentage" versus "Return Rate" using scatter plots.

**b) Datasets used,**
A synthetic transactional retail dataset named retail_dataset_45k.csv containing 45,000 sales records. The dataset features 22 attributes grouping into identifiers (Order ID, Customer ID), demographics (Age, Gender, Geography), product hierarchy (Category, Sub-category), financials (Total Amount, Discount), and operations (Order Status, Ship Mode).

**c) Snapshots showing implementation of the data mining algorithm of your choice and the results,**
*(Note for you: You will need to take screenshots of the following and paste them into your Word document)*
1.  **Power Query Editor Screenshot:** Show the transformed columns (where you created "Age Group" and calculated "Shipping Duration").
2.  **Scatter Plot Screenshot:** Show the chart comparing *Average Discount %* vs. *Total Quantity Sold/Return Rate*. 
3.  **Table/Matrix Screenshot:** Show the Customer Profiling table (*customer_state*, *Unique Customers*, *Revenue per Customer*).
4.  **Decomposition Tree Screenshot:** Show the AI visual breaking down *Total Revenue* by *Product Category* and *Customer Segment*.

**d) Interpretation and visualize the results,**
The dashboard visualizes the findings across multiple dimensions:
*   **Executive & Time Series:** Monthly revenue trends reveal seasonal shopping peaks.
*   **Product Performance Matrix:** Highlights that while some product categories generate the highest total revenue, smaller sub-categories might yield a higher Average Order Value (AOV).
*   **Customer Value Profiling:** The table visual reveals a geographic disparity: states with the highest raw customer count (e.g., California) do not necessarily yield the highest *Revenue per Customer*. Smaller, niche markets often spend more per transaction.
*   **Fulfillment Impact:** Line and scatter visualizations demonstrate an inverse correlation between shipping times and customer ratings—as shipping duration increases, average ratings drop and order return states increase.

**e) Provide clearly the BI decision that is to be taken as a result of mining.**
Based on the BI analysis, the management team should take the following strategic decisions:
1.  **Reallocate Marketing Spend:** Shift digital marketing budgets away from purely high-population states and target the specific states/regions identified in the dashboard as having the highest "Revenue per Customer" to maximize ROI.
2.  **Revise Discount Strategy:** The data reveals if steep discounts increase sales volume or simply lead to higher return rates. Stop offering arbitrary aggressive discounts (e.g., 30%+) on product sub-categories that show a high correlation with "Returned" order statuses.
3.  **Optimize Logistics:** Since shipping duration negatively correlates with customer ratings, the business must discontinue contracts with underperforming shipping modes for fragile/expensive items, prioritizing faster fulfillment to preserve customer satisfaction.

***