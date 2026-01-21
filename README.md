# 🍽️ Restaurant Sales & Order Analysis (Delhi NCR)

## 📝 Project Overview
This project focuses on the **cleaning, preprocessing, and exploratory analysis** of a restaurant order history dataset sourced from Kaggle. The dataset contains over **21,000 records** of food orders from the Delhi NCR region, tracking details such as order status, kitchen preparation time (KPT), rider wait times, and customer ratings.

The primary goal of this notebook was to handle significant missing data, remove redundant features, and prepare a clean dataset for further analysis or machine learning tasks.

---

## 📂 Dataset Overview
**Source:** `order_history_kaggle_data.csv` (Kaggle) 
* **Dimensions (Raw):** 21,321 rows × 29 columns 
* **Location Scope:** Delhi NCR 
* **Key Features:** 
    * **Order Info:** Order ID, Placed Time, Status, Items in Order.
    * **Financials:** Bill Subtotal, Packaging Charges, Discounts, Total.
    * **Logistics:** Kitchen Preparation Time (KPT), Rider Wait Time, Distance.
    * **Feedback:** Ratings, Reviews (removed during cleaning).

---

## 🛠️ Data Cleaning & Methodology

### 1. Initial Inspection
*Identified that the dataset covers only one city (**Delhi NCR**), making the `City` column redundant.
* **Missing Value Detection:** 
    * `Rating`: **18,830** missing values (Significant gap).
    * `KPT duration`: 295 missing values.
    * `Rider wait time`: 168 missing values.

### 2. Feature Selection
Dropped columns irrelevant to the analytical objective or containing mostly null/redundant information: 
* *Operational tags:* `Instructions`, `Order Ready Marked`, `Delivery`, `Customer complaint tag`.
* *Financial niche tags:* `Discount construct`, `Gold discount`, `Restaurant penalty`.
* *Text data:* `Review`, `Cancellation / Rejection reason`.

### 3. Advanced Imputation Strategy
Instead of dropping rows or filling with a global mean, missing values were imputed based on **specific restaurant performance** to maintain data integrity: 
* **Ratings:** Filled `NaN` values with the **Median Rating** of the specific restaurant.
* **Kitchen Prep Time (KPT):** Filled `NaN` values with the **Median KPT** of the specific restaurant.
* **Rider Wait Time:** Filled `NaN` values with the **Median Wait Time** of the specific restaurant.

### 4. Final Processing
* Renamed complex column names for better readability (e.g., `Restaurant discount (Flat offs...)` → `Restaurant discount`).
* Verified the dataset for duplicates (0 duplicates found).

---

## 📈 Key Findings & EDA

### 1. Distribution of Ratings
A histogram analysis of the `Rating` column (post-imputation) reveals the distribution of customer satisfaction.
* **Observation:** The ratings are heavily skewed towards positive values (4.0 - 5.0), partly due to the median imputation strategy filling the large volume of missing data with the typical high ratings of popular restaurants.

### 2. Top Performing Restaurants
We analyzed the order volume to identify the most popular eateries.
* **Visual:** A count plot displaying the top 6 restaurants by order frequency.
* **Top Entrants:** Restaurants like **"Aura Pizzas"**, **"Swaad"**, and **"Tandoori Junction"** appear frequently in the dataset.

---

## 📊 Dashboard Design & Features Created
A comprehensive dashboard was designed to provide a high-level overview of restaurant performance metrics.

### 1. Layout Features 
* **KPI Scorecards:** Total Orders, Average Order Value, Average Rating, and Preparation Time.
* **Product Performance:** Vertical bar chart ranking "Top Dishes" by quantity sold.
* **Geographical Insight:** "Order Radius" histogram analyzing delivery distances ( <1km to 9km).
* **Temporal Analysis:** "Peak Hours" line graph tracking order volume over time.
* **Competitive Landscape:** "Market Share" pie chart showing revenue distribution.
* **Interactive Filtering:** Filters for "Restaurant name" and "Subzone".

### 2. Operational Performance Metrics 
* **Volume & Value:** 21K total orders with an Average Order Value (AOV) of **682.62**.
* **Quality & Speed:** Exceptional Average Rating of **4.92** and an efficient average Prep Time of **17.32 minutes**.

### 3. Product Analysis: Top Dishes 
* **Bageecha Pizza:** Clear best-seller (>3,000 units).
* **Chilli Cheese Garlic Bread:** Popular side item (~2,000 units).
* **Other Top Items:** All About Chicken Pizza, Makhani Paneer Pizza, Margherita Pizza.

### 4. Geographical & Market Insights 
* **Delivery Radius:** Significant volumes at 2km and 3km marks.
* **Market Dominance:** The largest market segment captures **73.87% (10.75M)** of the share, followed by a secondary segment with **24.36% (3.55M)**.

---

## 💡 Business Recommendations

Based on the data cleaning process and analysis, the following actions are recommended: 

1.  **Incentivize Customer Feedback:**
    * *Observation:* Over 88% of orders were missing ratings.
    * *Action:* Implement loyalty points or discounts for rating orders to reduce data sparsity.

2.  **Optimize Logistics for Outliers:**
    * *Observation:* Imputation was required for missing operational times.
    * *Action:* Investigate specific time slots/restaurants where KPT data is missing (potential system overloads).

3.  **Capitalize on Top Performers:**
    * *Observation:* "Swaad" and "Aura Pizzas" dominate volume.
    * *Action:* Analyze their menu/pricing to replicate success in other subzones; bundle popular items for marketing.

---

## 💻 Technologies Used
* **Python 3** 
* **Pandas:** Data manipulation and cleaning.
* **NumPy:** Numerical operations.
* **Matplotlib & Seaborn:** Data visualization.
* **POWER BI:** Data Visualisation

---

## 💾 Deliverables
* **Input File:** `order_history_kaggle_data.csv` 
* **Output File:** `cleaned_order_history.csv` (16 optimized columns, zero missing values) 
