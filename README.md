
# 📊 Sales Data Analysis Using Python

This project contains an end–to–end Sales Data Analysis process done completely in **Python**, using real monthly sales CSV files. The goal of the analysis is to combine multiple monthly datasets, clean the data, extract new insights, and visualize sales trends.

🧰 Technologies & Libraries Used

Python
Pandas
Matplotlib / Seaborn (if graphs included)
Jupyter Notebook

📁 Dataset Description

The dataset contains multiple monthly CSV files with fields such as:

  `Order ID`
  `Product`
  `Quantity Ordered`
  `Price Each`
  `Order Date`
  `Purchase Address`

The files were combined and analyzed as a single dataset.


🔄 Steps Performed in the Notebook

1️⃣ Importing Required Libraries

python
import pandas as pd
import os

2️⃣ Importing and Combining Multiple CSV Files

All monthly CSV files were read using a loop
Files were merged into one dataframe

python
files = os.listdir("Sales_Data")
df = pd.concat([pd.read_csv("Sales_Data/" + f) for f in files])

The combined data was saved as `all_data.csv`.

3️⃣ Loading the Combined Dataset

python
all_data = pd.read_csv("all_data.csv")

4️⃣ Data Cleaning

✔ Removing missing values

python
all_data = all_data.dropna(how="all")

✔ Dropping unnecessary rows

python
all_data = all_data.drop(1)

5️⃣ Feature Engineering

📅 Extracting Month from `Order Date`

python
all_data["Month"] = all_data["Order Date"].str[0:2].astype("int32")


💰 Creating `Sales` column

python
all_data["Sales"] = all_data["Quantity Ordered"].astype(int) * all_data["Price Each"].astype(float)

 🗺 Extracting City from Address

python
all_data["City"] = all_data["Purchase Address"].apply(lambda x: x.split(",")[1].strip())


📈 Data Analysis Performed

✔ 1. Total Monthly Sales
✔ 2. Best Performing Cities
✔ 3. Most Sold Products
✔ 4. Relationship Between Price & Quantity

 📊 Visualizations

📌 1. Monthly Sales Trend (Line Chart)

Shows which months generated maximum revenue.

<img width="640" height="480" alt="Months Wise Sales ($)" src="https://github.com/user-attachments/assets/83b9636b-8c5f-4d55-ac76-6e0223c854c0" />

📌 2. City-wise Sales (Bar Chart)

Helpful for geographic business decisions.
<img width="640" height="480" alt="City Wise Total Sales($)" src="https://github.com/user-attachments/assets/99e02565-39ab-4773-9bd3-75fdc25936c8" />



🚀 Conclusion

This project demonstrates how Python alone can:

* Process multiple datasets
* Clean and transform data
* Perform analysis & visualization
* Extract meaningful business insights
