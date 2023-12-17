# CryptoClustering
Unsupervised Learning Module 19

# Steps Followed:

Renamed the Crypto_Clustering_starter_code.ipynb file as Crypto_Clustering.ipynb.

Loaded the crypto_market_data.csv into a DataFrame.

Got the summary statistics and plot the data to see what the data looks like before proceeding.

# Prepared the Data
Use the StandardScaler() module from scikit-learn to normalize the data from the CSV file.

Create a DataFrame with the scaled data and set the "coin_id" index from the original DataFrame as the index for the new DataFrame.

The first five rows of the scaled DataFrame should appear as follows:

<img width="979" alt="Screenshot 2023-12-17 at 1 56 21 PM" src="https://github.com/aamanhassan/CryptoClustering/assets/139508376/9f41c52b-b401-40c5-91f2-36e08a0bdf64">

# Best Value for k Using the Original Scaled DataFrame
Use the elbow method to find the best value for k using the following steps:

Created a list with the number of k values from 1 to 11.
Created an empty list to store the inertia values.
Created a for loop to compute the inertia with each possible value of k.
Created a dictionary with the data to plot the elbow curve.
Ploted a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.

<img width="605" alt="Screenshot 2023-12-17 at 1 58 41 PM" src="https://github.com/aamanhassan/CryptoClustering/assets/139508376/b7fcaade-a18f-4bb0-b56b-ba39a50ee90c">


# Question: What is the best value for k?

Answer: The best value for 'k' is 4

# Cluster Cryptocurrencies with K-means Using the Original Scaled Data
Use the following steps to cluster the cryptocurrencies for the best value for k on the original scaled data:

Initialized the K-means model with the best value for k.
Fit the K-means model using the original scaled DataFrame.
Predicted the clusters to group the cryptocurrencies using the original scaled DataFrame.
Created a copy of the original data and add a new column with the predicted clusters.
Created a scatter plot using hvPlot as follows:
Set the x-axis as "PC1" and the y-axis as "PC2".
Color the graph points with the labels found using K-means.
Add the "coin_id" column in the hover_cols parameter to identify the cryptocurrency represented by each data point.

<img width="624" alt="Screenshot 2023-12-17 at 2 01 47 PM" src="https://github.com/aamanhassan/CryptoClustering/assets/139508376/1983950d-d6de-4893-b4ea-583577c23f4e">

# Optimize Clusters with Principal Component Analysis
Using the original scaled DataFrame, perform a PCA and reduce the features to three principal components.

Retrieved the explained variance to determine how much information can be attributed to each principal component and then answer the following question in your notebook:

What is the total explained variance of the three principal components?
Create a new DataFrame with the PCA data and set the "coin_id" index from the original DataFrame as the index for the new DataFrame.

The first five rows of the PCA DataFrame should appear as follows

<img width="401" alt="Screenshot 2023-12-17 at 2 03 10 PM" src="https://github.com/aamanhassan/CryptoClustering/assets/139508376/1fe662bf-c308-4b5a-ba86-bfd82490b6c0">

# Find the Best Value for k Using the PCA Data
Use the elbow method on the PCA data to find the best value for k using the following steps:

Created a list with the number of k-values from 1 to 11.
Created an empty list to store the inertia values.
Created a for loop to compute the inertia with each possible value of k.
Created a dictionary with the data to plot the Elbow curve.
Ploted a line chart with all the inertia values computed with the different values of k to visually identify 

<img width="604" alt="Screenshot 2023-12-17 at 2 05 26 PM" src="https://github.com/aamanhassan/CryptoClustering/assets/139508376/0cfca5d1-fa79-486a-8d1c-a31453ee427f">
the optimal value for k.


Answer the following questions:

# Question: What is the best value for k when using the PCA data?
Answer: Best value for 'k' = 4

# Question: Does it differ from the best k value found using the original data?
Answer: No both values are same.

# Cluster Cryptocurrencies with K-means Using the PCA Data
Use the following steps to cluster the cryptocurrencies for the best value for k on the PCA data:

Initialized the K-means model with the best value for k.
Fit the K-means model using the PCA data.
Predicted the clusters to group the cryptocurrencies using the PCA data.
Created a copy of the DataFrame with the PCA data and add a new column to store the predicted clusters.
Created a scatter plot using hvPlot as follows:
Set the x-axis as "price_change_percentage_24h" and the y-axis as "price_change_percentage_7d".
Color the graph points with the labels found using K-means.
Add the "coin_id" column in the hover_cols parameter to identify the cryptocurrency represented by each data point.

<img width="628" alt="Screenshot 2023-12-17 at 2 07 49 PM" src="https://github.com/aamanhassan/CryptoClustering/assets/139508376/e6269746-08f7-430d-be3e-8d6535d52517">

# Visualize and Compare the Results
In this section, you will visually analyze the cluster analysis results by contrasting the outcome with and without using the optimization techniques.

# Composite plot to contrast the Elbow curves
elbow_plot + elbow_plot_pca

<img width="1010" alt="Screenshot 2023-12-17 at 2 15 37 PM" src="https://github.com/aamanhassan/CryptoClustering/assets/139508376/f5e4f92c-cb98-4803-b1c9-faa79123aab1">


# Composite plot to contrast the clusters
clusters_plot + clusters_plot_pca

<img width="1003" alt="Screenshot 2023-12-17 at 2 16 13 PM" src="https://github.com/aamanhassan/CryptoClustering/assets/139508376/abdf3024-8d2b-476a-9379-79fe8f388ae9">


Answer the following question:
# Question: After visually analyzing the cluster analysis results, what is the impact of using fewer features to cluster the data using K-Means?

Answer: After visually analyzing results, it becomes evident that achieving comparable performance with fewer features is feasible. In both cases, we get four distinct clusters. While reducing features, makes visualization easier and much simpler but there is a 10% data loss tradeoff occurred during the PCA process.



