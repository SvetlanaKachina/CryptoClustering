# CryptoClustering #
## Using knowledge of Python and unsupervised learning to predict if cryptocurrencies are affected by 24-hour or 7-day price changes. ##
### Prepared Data ###
+ Used the StandardScaler() module from scikit-learn to normalize the data from the CSV file.

+ Created a DataFrame with the scaled data and set the "coin_id" index from the original     DataFrame as the index for the new DataFrame.

+ The first nine rows of the scaled DataFrame should appear as follows:
 ![image](https://github.com/user-attachments/assets/7db57738-5709-4155-a424-6360ce4e8947)


### Found the Best Value for k Using the Scaled DataFrame ###
Used the elbow method to find the best value for k using the following steps:
+ Created a list with the number of k values from 1 to 11.
+ Created an empty list to store the inertia values.
+ Created a for loop to compute the inertia with each possible value of k.
+ Created a dictionary with the data to plot the elbow curve.
+ Plotted a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.
+ The beast value for k is 4

### Clustered Cryptocurrencies with K-means Using the Scaled DataFrame ###
Used the following steps to cluster the cryptocurrencies for the best value for k on the scaled DataFrame:
+ Initialized the K-means model with the best value for k.
+ Fitted the K-means model using the scaled DataFrame.
+ Predicted the clusters to group the cryptocurrencies using the scaled DataFrame.
+Created a copy of the scaled DataFrame and add a new column with the predicted clusters.
+ Created a scatter plot using hvPlot as follows:
+ Set the x-axis as "price_change_percentage_24h" and the y-axis as "price_change_percentage_7d".
+ Colored the graph points with the labels found using K-means.
+ Added the "coin_id" column in the hover_cols parameter to identify the cryptocurrency represented by each data point.

### Optimized Clusters with Principal Component Analysis ###
+ Using the original scaled DataFrame, performed a PCA and reduced the features to three principal components.
+ Retrieved the explained variance to determine how much information can be attributed to each principal component and then answered the following question in your notebook:
    + The total explained varience of the three principal components is 0.90(with round ups)
+ Created a new DataFrame with the scaled PCA data and set the "coin_id" index from the original DataFrame as the index for the new DataFrame.
     + The first five rows of the scaled PCA DataFrame appeared as follows:
 ![image](https://github.com/user-attachments/assets/4cd64dd7-05a3-4c6f-8be6-6ef1b6ce0f71)

### Found the Best Value for k Using the PCA DataFrame ###
Use the elbow method on the scaled PCA DataFrame to find the best value for k using the following steps:
+ Created a list with the number of k-values from 1 to 11.
+ Created an empty list to store the inertia values.
+ Created a for loop to compute the inertia with each possible value of k.
+ Create a dictionary with the data to plot the Elbow curve.
+ Plotted a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.
+ Answered the following question in your notebook:
+ What is the best value for k when using the scaled PCA DataFrame? - The best value for k using PCA is 4
+ Does it differ from the best k value found using the original scaled DataFrame? - No, it does not differ from the original data.

### Clustered Cryptocurrencies with K-means Using the PCA DataFrame ###
Use the following steps to cluster the cryptocurrencies for the best value for k on the PCA DataFrame:
+ Initialized the K-means model with the best value for k.
+ Fit the K-means model using the scaled PCA DataFrame.
+ Predicted the clusters to group the cryptocurrencies using the scaled PCA DataFrame.
+ Created a copy of the scaled PCA DataFrame and add a new column to store the predicted clusters.
+ Created a scatter plot using hvPlot as follows:
+ Set the x-axis as "PC1" and the y-axis as "PC2".
+ Colored the graph points with the labels found using K-means.
+ Added the "coin_id" column in the hover_cols parameter to identify the cryptocurrency represented by each data point.
+ Answered the following question:
+ What is the impact of using fewer features to cluster the data using K-Means?
-	After visually analyzing the cluster analysis results, using fewer features through Principal Component Analysis (PCA) positively impacts K-Means clustering by enhancing cluster separation and interpretability. In the original feature space, clusters appear more dispersed and overlapping, but after dimensionality reduction, they become more compact and distinct. The elbow curve also shows that inertia decreases more sharply with PCA, making it easier to identify the optimal number of clusters. Overall, PCA reduces noise and redundancy, resulting in clearer and more efficient clustering, though it may lead to some loss of detailed information present in the original data.
