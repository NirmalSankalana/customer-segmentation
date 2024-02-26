# customer-segmentation

## About the dataset

Dataset has 7 columns. First I got a summery about the dataset
![report](./img//data_report.png)

There is no any null values in the dataset.

## Outlier Removal

Outliers in the Quantity and Sales_Amount columns have been identified and eliminated, as some clustering algorithms, such as K-means, are sensitive to outliers. The **z-score method** was employed for this purpose.

![outliers](./img//outliers.png)

## Feature Engineering

Following features are created in feature engineering:

1. Total amount spent by a customer
2. Number of transactions by a customer
3. Amount spent by the customer for each category
4. Quantity bought by the customer for each productt

Date and transaction IDs seem not useful in customer segmentation Those columns were eliminated. 

After creating the mentioned features, the dataframe contains `5245` features for `22625` customers. Given the high dimensionality of the dataframe, some feature selection and dimensionality reduction methods were applied.

1. **Variency thresholding** Features with a variance lower than 0.05 were considered low-variance and were removed.

2. **Principle Component Analysis(PCA)**: A popular dimensionality reduction method, PCA was employed to reduce the number of features. It is a common practice to apply PCA before a clustering algorithm to improve clustering results by reducing noise.

**Feature scaling** was performed using standardization to ensure a fair contribution of each feature to the clustering process and avoid biased clusters.

## 1. K Means Algorithm

Notebook: [customer-segmentation-k-means](https://www.kaggle.com/code/nirmalsankalana/customer-segmentation-k-means/notebook)

K-means is a distance-based clustering algorithm that segments data into K clusters. Each data point is assigned to a cluster based on the distance to the centroid, which is recalculated as the mean of all data points in the cluster. This process repeats until centroids do not change.

### Finding the optimal number of clusters

Two methods were used to find the optimal number of clusters:

1. **Elbow Method**: Determines the K value where the within-cluster sum of squares (WCSS) exhibits a significant reduction, forming an elbow-like shape in the plot.

2. **Silhouette Method**: Quantitatively measures how well each data point fits its assigned cluster compared to neighboring clusters.

The elbow method suggested K = 4, while the silhouette method suggested K = 2. After clustering the data, it was observed that clusters were not well-separated and interpretable when K = 4. Therefore, K = 2 was chosen.

##### When K=2 Characteristics of the two clusters are like this:

- **Cluster 0**: Customers who generate less revenue and visit the store less frequently.
- **Cluster 1**: Customers who generate more revenue and visit the store more frequently.

or interactive visualizations, please refer to [this notebook](https://www.kaggle.com/code/nirmalsankalana/customer-segmentation-k-means/notebook).

![Clusters 3D](./img//k_means_clsters_3d.png)

![Clusters 2D](./img//k_means_clusters_2d.png)

![Data Distribution](./img//k_means_cluster_data_distribution.png)
