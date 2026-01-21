# Restaurant-Sales-Analysis
 Restaurant Sales Analysis 
📝 Project Overview
This project focuses on the cleaning, preprocessing, and exploratory analysis of a restaurant order history dataset (sourced from Kaggle). The dataset contains over 21,000 records of food orders from the Delhi NCR region, tracking details such as order status, kitchen preparation time (KPT), rider wait times, and customer ratings.
The primary goal of this notebook was to handle significant missing data, remove redundant features, and prepare a clean dataset for further analysis or machine learning tasks.
________________________________________
📂 Dataset Overview
•	Source: order_history_kaggle_data.csv from Kaggle
•	Dimensions (Raw): 21,321 rows × 29 columns
•	Location Scope: Delhi NCR
•	Key Features:
o	Order Info: Order ID, Placed Time, Status, Items in Order.
o	Financials: Bill Subtotal, Packaging Charges, Discounts, Total.
o	Logistics: Kitchen Preparation Time (KPT), Rider Wait Time, Distance.
o	Feedback: Ratings, Reviews (removed during cleaning).
________________________________________
🛠️ Data Cleaning & Methodology
1. Initial Inspection
•	Identified that the dataset covers only one city (Delhi NCR), making the City column redundant.
•	Missing Value Detection:
o	Rating: 18,830 missing values (Significant gap).
o	KPT duration: 295 missing values.
o	Rider wait time: 168 missing values.
2. Feature Selection
Dropped columns irrelevant to the analytical objective or containing mostly null/redundant information:
•	Operational tags: Instructions, Order Ready Marked, Delivery, Customer complaint tag.
•	Financial niche tags: Discount construct, Gold discount, Restaurant penalty.
•	Text data: Review, Cancellation / Rejection reason.
3. Advanced Imputation Strategy
Instead of dropping rows or filling with a global mean, missing values were imputed based on specific restaurant performance to maintain data integrity:
•	Ratings: Filled NaN values with the Median Rating of the specific restaurant.
•	Kitchen Prep Time (KPT): Filled NaN values with the Median KPT of the specific restaurant.
•	Rider Wait Time: Filled NaN values with the Median Wait Time of the specific restaurant.
4. Final Processing
•	Renamed complex column names for better readability (e.g., Restaurant discount (Flat offs...) → Restaurant discount).
•	Verified the dataset for duplicates (0 duplicates found).
________________________________________
📈 Key Findings & EDA
1. Distribution of Ratings
A histogram analysis of the Rating column (post-imputation) reveals the distribution of customer satisfaction.
•	Observation: The ratings are heavily skewed towards positive values (4.0 - 5.0), partly due to the median imputation strategy filling the large volume of missing data with the typical high ratings of popular restaurants.
2. Top Performing Restaurants
We analysed the order volume to identify the most popular eateries.
•	Visual: A count plot displaying the top 6 restaurants by order frequency.
•	Top Entrants: Restaurants like "Aura Pizzas", "Swaad", and "Tandoori Junction" appear frequently in the dataset.
________________________________________
 Dashboard Design & Features Created
This dashboard was designed to provide a high-level overview of restaurant performance metrics. Key features implemented in the layout include:
•	Key Performance Indicators (KPIs): Prominent scorecards displaying Total Orders, Average Order Value, Average Rating, and Preparation Time.
•	Product Performance Visualization: A vertical bar chart ranking the "Top Dishes" by quantity sold.
•	Geographical Insight: An "Order Radius" histogram analysing delivery distances ranging from less than 1km to 9km.
•	Temporal Analysis: A "Peak Hours" line graph tracking the number of orders over time.
•	Competitive Landscape: A "Market Share" pie chart illustrating the revenue distribution among competitors.
•	Interactive Filtering: The dashboard features drop-down filters for "Restaurant name"  and "Subzone" to allow for granular data drilling.
2. Operational Performance Metrics
The selected data indicates strong operational efficiency and high customer satisfaction:
•	Volume & Value: The restaurant has processed a total of 21K orders. The Average Order Value (AOV) stands at 682.62, indicating a healthy revenue per transaction.
•	Quality & Speed: The restaurant maintains an exceptional Average Rating of 4.92, suggesting high customer retention and satisfaction. Operationally, the kitchen is efficient with an average Prep Time of 17.32 minutes.
3. Product Analysis: Top Dishes
The "Top Dishes" chart highlights customer preferences, with pizzas dominating the menu:
•	Bageecha Pizza is the clear best-seller, with sales volume exceeding 3,000 units.
•	Chilli Cheese Garlic Bread follows as a popular side item, nearing 2,000 units.
•	Other top performers include All About Chicken Pizza, Makhani Paneer Pizza, and Margherita Pizza.
4. Geographical & Market Insights
•	Delivery Radius: The dashboard tracks orders across a wide radius. Significant order volumes are recorded at the 2km and 3km marks, extending out to 9km.
•	Market Share: The market share visualization breaks down the sales distribution among key players such as Aura Pizzas, Swaad, Tandoori Junction, Dilli Burger Adda, The Chicken Junction, and Masala Junction.
•	Dominance: The largest market segment captures 73.87% (10.75M) of the share, followed by a secondary segment holding 24.36% (3.55M).

________________________________________
💡 Business Recommendations
Based on the data cleaning process and initial analysis, the following actions are recommended for stakeholders:
1.	Incentivize Customer Feedback:
o	Observation: Over 88% of orders (18,830 out of 21,321) were missing ratings.
o	Action: Implement a loyalty point system or small discount on future orders for customers who leave a rating. This will reduce data sparsity and provide a more accurate picture of customer sentiment.
2.	Optimize Logistics for Outliers:
o	Observation: While most operational times (KPT and Rider Wait Time) were standard, imputation was required for missing values.
o	Action: Investigate the specific restaurants or time slots where KPT data is missing. Missing operational data often correlates with peak-hour system overloads or manual logging errors.
3.	Capitalize on Top Performers:
o	Observation: "Swaad" and “Aura Pizzas" dominate order volume.
o	Action: Analyse the menu composition and pricing strategy of these top performers to replicate their success in underperforming subzones. Consider bundling their popular items for aggressive marketing campaigns.
________________________________________
💻 Technologies Used
•	Python 3
•	Pandas: For data manipulation and cleaning.
•	NumPy: For numerical operations.
•	Matplotlib & Seaborn: For data visualization.
________________________________________
💾 Deliverables
The cleaned dataset has been exported for future use:
•	Input File: order_history_kaggle_data.csv
•	Output File: cleaned_order_history.csv (16 optimized columns, zero missing values)



