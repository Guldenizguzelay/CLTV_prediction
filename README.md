# CLTV prediction
Customer Lifetime Value (CLTV) Prediction Using BG-NBD and Gamma-Gamma Models

![image](https://github.com/user-attachments/assets/25093759-c629-41e2-8df9-5221307bc3f3)


Dataset
The dataset is sourced from the Online Retail II dataset, which contains sales data from an online retail store in the UK from 01/12/2009 to 09/12/2011.

Data set : https://archive.ics.uci.edu/ml/datasets/Online+Retail+II

# Features:
* InvoiceNo: Unique invoice number (invoices starting with 'C' indicate cancellations).
* StockCode: Unique product code.
* Description: Product description.
* Quantity: Number of units sold.
* InvoiceDate: Date and time of the invoice.
* UnitPrice: Price per unit (in GBP).
* CustomerID: Unique customer identifier.
* Country: Customer's country of residence.

# Steps in Analysis

## 1. Data Preparation
* Data cleaning:
  
  Removed null values.
  
  Excluded canceled transactions (invoices starting with 'C').
  
  Filtered out negative quantities and prices.
  
* New features:
  TotalPrice: Calculated as Quantity * UnitPrice.
  
  Prepared the dataset for CLTV calculation with key metrics:
  
  Recency: Time since the last purchase (in weeks).
  
  T: Customer's age (time since the first purchase, in weeks).
  
  Frequency: Total number of repeat purchases.
  
  Monetary: Average profit per transaction.

## 2. Building the BG-NBD Model
The Beta-Geometric Negative Binomial Distribution (BG-NBD) model predicts the expected number of purchases for each customer over a given time frame:

* Top 10 customers predicted to make the most purchases within 1 week.
* Total expected purchases for the entire customer base over 3 months.

## 3. Building the Gamma-Gamma Model
The Gamma-Gamma model predicts the average monetary value per transaction for each customer:

* Identified the top 10 customers with the highest predicted average profits.

## 4. CLTV Calculation
Combined the BG-NBD and Gamma-Gamma models to calculate CLTV:

* Predicted CLTV for a 3-month period using the customer_lifetime_value function.

## 5. Customer Segmentation
Segmented customers based on their CLTV values into four categories:

* Segment A: Highest CLTV customers.
* Segment B: High CLTV customers.
* Segment C: Medium CLTV customers.
* Segment D: Lowest CLTV customers.
