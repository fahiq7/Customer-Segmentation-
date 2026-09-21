# E-Commerce Customer Behavior Analytics and Recommendation System

## 📌 Project Overview

**E-Commerce Customer Behavior Analytics and Recommendation System** is a Big Data Analytics project that analyzes large-scale e-commerce transaction data and generates product recommendations based on customer purchasing behavior.

The project combines **Hadoop, HDFS, Apache Hive, MapReduce, PySpark, and K-Nearest Neighbors (KNN)** to demonstrate a complete Big Data processing and recommendation workflow.

The system processes raw transaction data, performs distributed storage and analytics, cleans and transforms the data using PySpark, constructs a Customer–Product Matrix, identifies similar customers using KNN, and generates product recommendations.

---

## 🎯 Objectives

The main objectives of this project are:

* To store large e-commerce transaction data using **Hadoop HDFS**.
* To perform SQL-based analysis using **Apache Hive**.
* To analyze transaction, product, country, and revenue-related information.
* To clean and transform transaction data using **PySpark**.
* To construct a **Customer–Product Matrix** from purchasing behavior.
* To identify similar customers using **K-Nearest Neighbors (KNN)**.
* To generate product recommendations based on similar customer behavior.
* To visualize important analytical and recommendation results.

---

## 🏗️ Project Workflow

The complete workflow of the project is:

```text
E-Commerce Transaction Dataset
              │
              ▼
        Hadoop HDFS
              │
              ▼
       Apache Hive
              │
              ▼
   Hive / MapReduce Analytics
              │
              ▼
          PySpark
   Data Cleaning & Transformation
              │
              ▼
     Customer–Product Matrix
              │
              ▼
             KNN
      Similar Customer Analysis
              │
              ▼
      Product Recommendations
              │
              ▼
     Results & Visualization
```

### Workflow Stages

**1. Data Storage**

The raw e-commerce transaction dataset is stored in Hadoop HDFS.

**2. Hive Processing**

The dataset is organized using an `ecommerce` Hive database and a `transactions` table.

**3. Data Analytics**

Hive queries are used for transaction analysis, product analysis, country-wise analysis, and revenue analysis.

**4. PySpark Data Engineering**

PySpark is used for cleaning and transforming the transaction data.

**5. Customer–Product Matrix**

Customer purchasing behavior is converted into a matrix where customers represent rows and products represent columns.

**6. KNN Recommendation**

KNN is applied to identify customers with similar purchasing patterns.

**7. Recommendation Generation**

Products purchased by similar customers are used to generate potential recommendations.

**8. Visualization**

The final recommendation scores are visualized using a product-wise bar chart.

---

## 🛠️ Technologies Used

| Technology   | Purpose                                           |
| ------------ | ------------------------------------------------- |
| Python       | Data processing and recommendation implementation |
| Hadoop       | Big Data storage and distributed processing       |
| HDFS         | Distributed storage of transaction data           |
| YARN         | Resource management                               |
| MapReduce    | Distributed data processing                       |
| Apache Hive  | SQL-based Big Data analytics                      |
| PySpark      | Data cleaning and transformation                  |
| Pandas       | Data preparation and DataFrame operations         |
| Scikit-learn | KNN implementation                                |
| Matplotlib   | Data visualization                                |
| Google Colab | PySpark and KNN experimentation                   |
| LaTeX        | Project report preparation                        |

---

## 📊 Dataset

The project uses an e-commerce transaction dataset containing approximately:

* **541,909 transaction records**
* **43.5 MB** of raw data
* **8 attributes**
* **4,070 unique products**
* **5,349 unique customers**

### Dataset Attributes

| Attribute     | Description                    |
| ------------- | ------------------------------ |
| `InvoiceNo`   | Invoice or transaction number  |
| `StockCode`   | Product identification code    |
| `Description` | Product description            |
| `Quantity`    | Quantity purchased             |
| `InvoiceDate` | Date and time of transaction   |
| `UnitPrice`   | Price per unit                 |
| `CustomerID`  | Customer identification number |
| `Country`     | Customer's country             |

---

## 🗄️ Hadoop HDFS

The transaction dataset is stored in HDFS at:

```text
/ecommerce/transactions/data.csv
```

HDFS provides distributed storage for the transaction dataset and forms the initial stage of the Big Data processing pipeline.

The Hadoop environment used in the project includes:

* Hadoop 3.3.6
* HDFS
* YARN
* MapReduce
* Ubuntu Linux

---

## 🐝 Apache Hive

A Hive database named:

```text
ecommerce
```

was created.

The main Hive table is:

```text
transactions
```

### Hive Table Schema

| Column      | Data Type |
| ----------- | --------- |
| InvoiceNo   | STRING    |
| StockCode   | STRING    |
| Description | STRING    |
| Quantity    | INT       |
| InvoiceDate | STRING    |
| UnitPrice   | DOUBLE    |
| CustomerID  | STRING    |
| Country     | STRING    |

Hive was used to perform analytical queries on the transaction data.

### Major Hive Analyses

The project includes:

* Country-wise transaction analysis
* Top-selling product analysis
* Monthly revenue analysis
* Country-wise revenue analysis

---

## ⚡ PySpark Data Engineering

After the Hive analytics stage, PySpark is used for data engineering.

The main processing operations include:

### Data Loading

The transaction dataset is loaded into a PySpark DataFrame.

### Data Cleaning

Records with:

* Non-positive quantities
* Non-positive unit prices
* Missing customer IDs
* Missing product descriptions

are removed from the dataset.

### Revenue Calculation

Transaction revenue is calculated using:

```text
Revenue = Quantity × UnitPrice
```

### Customer–Product Aggregation

The cleaned data is grouped using:

```text
CustomerID + StockCode
```

The total quantity purchased for each customer-product combination is calculated.

---

## 🤖 KNN Recommendation System

The recommendation stage uses **K-Nearest Neighbors (KNN)** as a similarity-based recommendation method.

A Customer–Product Matrix is constructed where:

```text
Rows    → Customers
Columns → Products
Values  → Purchase Quantity
```

For example:

```text
             Product A  Product B  Product C
Customer 1       5          0          2
Customer 2       3          4          0
Customer 3       0          2          7
```

The matrix represents customer purchasing behavior numerically.

KNN is then used to identify customers with similar purchasing patterns.

### Recommendation Process

1. Select a target customer.
2. Obtain the customer's purchasing vector.
3. Compare the customer with other customers.
4. Identify the nearest similar customers.
5. Examine products purchased by similar customers.
6. Remove products already purchased by the target customer where applicable.
7. Calculate recommendation scores.
8. Rank the candidate products.
9. Generate the final recommendation list.

---

## 📈 Recommendation Score

The recommendation score is calculated from the purchasing behavior of similar customers.

Products that receive stronger scores from the similar-customer purchasing patterns are placed higher in the recommendation list.

The final recommendations are stored in a DataFrame containing:

```text
StockCode
Product
Score
```

---

## 📊 Data Visualization

The project includes visualizations for understanding the transaction data and recommendation results.

### Main Visualizations

* Country-wise transaction records
* Top-selling products
* Monthly revenue
* Country-wise revenue
* Customer–Product Matrix
* Final Recommendation DataFrame
* Recommendation Score Visualization

The final recommendation results are represented using a product-wise bar chart.

---

## 📁 Project Structure

A typical project structure is:

```text
E-Commerce-Customer-Behavior-Analytics/
│
├── README.md
│
├── data/
│   └── data.csv
│
├── notebooks/
│   └── ecommerce_recommendation.ipynb
│
├── screenshots/
│   ├── hive_database_screenshot.png
│   ├── country_transaction_output.png
│   ├── top_selling_products.png
│   ├── monthly_revenue.png
│   ├── country_revenue.png
│   ├── pyspark_data_loading.png
│   ├── pyspark_cleaning_output.png
│   ├── pyspark_revenue_output.png
│   ├── customer_product_output.png
│   ├── customer_product_matrix.png
│   ├── recommendation_dataframe.png
│   └── recommendation_visualization.png
│
├── report/
│   └── project_report.pdf
│
└── src/
    └── recommendation.py
```

> The exact folder structure may vary depending on the files included in the repository.

---

## 🚀 How to Run the Project

### 1. Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd E-Commerce-Customer-Behavior-Analytics
```

### 2. Install Python Dependencies

```bash
pip install pyspark pandas scikit-learn matplotlib
```

### 3. Prepare the Dataset

Place the transaction dataset in the required project location.

For the PySpark implementation, the CSV file should be accessible as:

```text
data.csv
```

### 4. Start Hadoop

Ensure that Hadoop services are running before performing the HDFS and Hive stages.

Check Hadoop services using:

```bash
jps
```

The required Hadoop services include components such as:

```text
NameNode
DataNode
ResourceManager
NodeManager
SecondaryNameNode
```

### 5. Upload Dataset to HDFS

The dataset is stored at:

```text
/ecommerce/transactions/data.csv
```

### 6. Start Hive

Create the required Hive database and transaction table.

```sql
CREATE DATABASE ecommerce;
```

Then create the `transactions` table according to the dataset schema and load the transaction data.

### 7. Run Hive Analytics

The Hive stage can be used to perform queries for:

```text
Country-wise transactions
Top-selling products
Monthly revenue
Country-wise revenue
```

### 8. Run the PySpark and KNN Implementation

The PySpark implementation performs:

```text
Data Loading
      ↓
Data Cleaning
      ↓
Revenue Calculation
      ↓
Customer-Product Aggregation
      ↓
Customer-Product Matrix
      ↓
KNN Similarity
      ↓
Product Recommendations
      ↓
Visualization
```

The implementation can also be executed using **Google Colab** with PySpark and the required Python libraries.

---

## 📌 Key Results

The project produced several analytical results from the transaction dataset.

### Dataset Statistics

| Metric              |        Value |
| ------------------- | -----------: |
| Transaction Records |      541,909 |
| Unique Products     |        4,070 |
| Unique Customers    |        5,349 |
| Total Quantity Sold |    5,154,688 |
| Total Revenue       | 9,699,674.37 |
| Average Unit Price  |         4.64 |

### Major Analytical Outputs

The Hive and PySpark stages provide:

* Country-wise transaction statistics
* Product sales analysis
* Monthly revenue analysis
* Country-wise revenue analysis
* Cleaned customer transaction data
* Customer-product purchasing relationships
* Customer similarity results
* Product recommendations

---

## 💡 Applications

The approach demonstrated in this project can be applied to:

* E-commerce recommendation systems
* Customer behavior analysis
* Personalized product suggestions
* Retail analytics
* Customer segmentation
* Large-scale transaction processing
* Business intelligence systems

---

## 🔮 Future Scope

The current project can be extended in several ways:

* Use larger and continuously updated datasets.
* Implement more advanced collaborative filtering methods.
* Compare KNN with other recommendation algorithms.
* Introduce explicit recommendation evaluation metrics.
* Develop a real-time recommendation pipeline.
* Build a web-based recommendation interface.
* Integrate the recommendation system with an actual e-commerce platform.
* Use distributed model training for larger datasets.

---

## 🎓 Academic Information

**Project Title:**
E-Commerce Customer Behavior Analytics and Recommendation System

**Subject:**
Big Data Analytics (PBADT504)

**Department:**
Department of Computer Science and Engineering
Artificial Intelligence and Data Science

**Institution:**
Vimal Jyothi Engineering College, Chemperi

### Project Team

* **Muhammed Fahique** — VML24AD081
* **Ashith V** — VML24AD038
* **Amarnath A** — VML24AD023
* **Manav K** — VML24AD073

### Project Guide

**Soumya Thomas**
Assistant Professor
Department of Computer Science and Engineering
Artificial Intelligence and Data Science

---

## 📜 Conclusion

This project demonstrates a complete Big Data Analytics pipeline for e-commerce transaction data.

The system begins with distributed data storage using **Hadoop HDFS**, followed by SQL-based processing and analytics using **Apache Hive**. PySpark is then used for data cleaning, transformation, revenue calculation, and customer-product aggregation.

The processed data is converted into a Customer–Product Matrix and supplied to a **KNN-based similarity recommendation system**. Similar customer purchasing patterns are identified and used to generate product recommendations.

The final outputs are presented through structured DataFrames and visualizations, demonstrating how Big Data technologies can be combined with machine learning techniques to analyze customer behavior and generate personalized product recommendations.

---

## 👥 Authors

**Muhammed Fahique**
**Ashith V**
**Amarnath A**
**Manav K**

B.Tech Computer Science and Engineering
Artificial Intelligence and Data Science
Vimal Jyothi Engineering College, Chemperi

---

## ⭐ Acknowledgement

This academic project was completed as part of the **Big Data Analytics (PBADT504)** course with the guidance and support of the faculty members of the Department of Computer Science and Engineering (Artificial Intelligence and Data Science), Vimal Jyothi Engineering College, Chemperi.
