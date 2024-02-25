# customer-segmentation

## About the dataset

Dataset has 7 columns. They are:

1. Date: Date of the purchase
1. Customer_ID: Unique identifier for each customer
1. Transaction_ID: Unique identifier for the transaction
1. SKU_Category: Grouping of SKUs by product type (e.g., clothing, electronics, accessories).
1. SKU: Unique identifier for a product scanned by barcode.
1. Quantity: Number of items purchased.
1. Sales_Amount: Price paid for each item.

There is no any null values in the dataset.

## Outlier Removal

There are some outlier transactions exists in Quantity and Salse_Amount columns. Some clustering algorithms such as K-means is sensitive to outliers. Therefore those enties have been eliminated.

![outliers](./img//outliers.png)

## Feature Engineering
Following features are created in feature engineering:
1. Total amount spent by a Customer
2. Number of transaction by a customer
3. Amount spent by the customer for each category
4. Amount spent by the customer for each product

Date, transaction IDs are seems not useful in customer segmentation.

**Variency thresholding** is used to remove low variace features. Here any feature with a variance lower than 0.01 will be considered a low-variance feature and will be removed.

**Feature scaling** is done using standerdization. It ensures fair contribution of each feature to the clustering process and avoid biased clusters.

**Principle Component Analysis(PCA)** is a popular dimentionality reduction and it is used to reduce the number of features from 3000 to 2798. It is a common practice to apply PCA before a clustering algorithm. It is believed that it improves the clustering results in practice by reducing noise.

## K Means Algorithm
K Means is a distance based clustering algorithm which segment data to K clusters. Each data point is assigned to a cluster based on the distance of the data to the centroid. The centroid is then recalculated based on the mean of all the data points in the cluster. This process is repeated until the centroids do not change.

### Finding the optimal number of clusters
