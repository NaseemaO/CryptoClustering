# Crypto Clustering, Challenge 19: Unsupervised Machine Learning

# Project Overview
Predict impact on cryptocurrencies with price change percentage using Python and Unsupervised Learning for Data Visualization and Analysis. 
Optimize data clustering by selecting the best value for k using the elbow method. The K-means algorithm is useful for grouping and understanding data. Elbow curve and Scatter Plots used for visualization and analysis. 

The following 5 features from the input data, the Price Change Percentages, were explored: 
  24 hours,
  7 days,
  14 days, 
  30 days, 
  60 days.

Two data sets created using input data to determine the optimal k number/ number of clusters for each, and then were compared to each other visually.
  1. Normalizing the input data.  This is standardization of data using StandardScaler. 
  2. Combining the normalized and the Principal Component Analysis data. 

# Analysis: 
  Composite Elbow Curves: Both Elbow Curves have the similarity where 4 is the optimal value for k      

  Composite Scatter Plots: 
    The Scatter Plot of the Scaled Data by Price Segment with k = 4, revealved that the red data dot and the green data dot are outliers. 
    
    The Scatter Plot of the Scaled data and PCA data with k = 4, revealed the green data dot and the blue data dot are outliers. 
    
    The goal was to find a value for k that corresponds to a measure of inertia that shows minimal change for each additional cluster (or value of k) that is added to the dataset.  In this case the optimal value for k = 4.  The number of clusters are determined by the k value.  This is a reasonable number of clusters.   

    The fewer the clusters, the high the concentration of elements (where elements are tightly grouped together), and they have low inertia value. 
    This means that there is a small standard deviation for the elements in the cluster relative to the cluster mean value.
    The fewer number of clusters, the less 'noise' within the clusters. 

Note that there are limitations in inferring from Scatter Charts as they are visually represented in a 2 dimensional space and in actuality we have 5 features, 5 dimensions, in this study.

  <img src="Images\composite_elbow_plots.png" alt="Composite Elbow Curve Plots" width="800" height="400">

  <img src="Images\composite_scatter_plots.png"alt="Composite Scatter Plots" width="800" height="400">


# Background: 
The most common way to standardize data or scale data is to apply standard scaling, which is a method of centering values around the mean.

The K-means algorithm is the simplest and most common algorithm used to group data points into clusters.

Elbow method is one method for determining the optimal value of k, or the number of clusters in a dataset.
● The elbow method runs the K-means algorithm for a range of possibilities for k, or the number of clusters. 
● The resulting elbow curve plots the number of clusters, x, versus an objective function called inertia

On the elbow curve, the x-axis is the value of clusters, while the y-axis is a metric used to assess the value of k.

The inertia is commonly used as an objective function. It is the sum of the squared distances of samples to their closest cluster center.
A low inertia value means that the data points are tightly clustered around the cluster center. This means that there is a small standard 
deviation for the elements in the cluster relative to the cluster mean value.

There is a k value that after which the inertia is pretty stable.  We find the optimal value for k which has hit a point where the intertia drops at a lower rate and starts to remain quite steady and stable. The goal is to find a value for k that corresponds to a measure of inertia that 
shows minimal change for each additional cluster (or value of k) that is added to the dataset.
 
## Programs and Modules required
Python, Jupyter notebook
Pandas
hvPlot
scikit-learn. sklearn: Cluster / KMeans, sklearn.Preprocessing /StandardScaler, Decomposition / PCA (Principal Component Analysis) 

# Technical Process
DRY (Don't Repeat Yourself) principles applied where possible for creating, maintaining, and reusing code(s).

Input Data 'crypto_market_data.csv' loaded into a Pandas DataFrame 
  Explored the file's summary statistics and plot the data to visualize the data it gets processed.
  hvplot Line Chart plotted 
  Visual finding: While the majority of the cryptocurrencies remained pretty stable and consistent with price changes, there were a few that increased with price changes of 1 year and of 200 days. 
 

Normalizing the input data referred to as Scaled Data:
  StandardScaler() module from scikit-learn used to normalize the data from the input csv file.
  DataFrame created with the scaled data

Cluster Cryptocurrencies with K-means using the Scaled Data:
  Elbow method algorithm used plot the Elbow Curve Line chart with all the inertial values computed with the different values of k
  to visually identify the optimal value for k. k indicates the number of clusters it will segment the data into. 

  'elbow_plot_scaled' elbow curve plotted. 
  4 is the best Value for 'k' identified using the Scaled DataFrame since after that the inertial doesn't drop significantly and has a diminished return.

  K-means model used with the best value for k using the Scaled DataFrame Scaled_df
  Clusters predicted to group the cryptocurrencies. Predicted Clusters added to a copy of the Scaled DataFrame

  Scatter plot 'scaled_data_predictions_plot' created using hvPlot. x="price_change_percentage_24h" and y="price_change_percentage_7d".
  Cryptocurrency name to the hover_cols parameter to identify the cryptocurrency that each data point represents.

 Cluster Cryptocurrencies with K-means Using the PCA Model:
  Clusters optimized with PCA Principal Component Analysis on Scaled DataFrame, and features reduced to three principal components.
  
  Used the explained variance to determine how much information can be attributed to each of the three principal components PC1, PC2 and PC3 
  91% is the total explained variance of the three PC1, PC2, and PC3 

  PCA Data added to the Scaled DataFrame to create a new DataFrame PCA_df
  Repeat the k-means model process to find the optimal k value on a new DataFrame using the PCA data and the Scaled DataFrame data
  'elbow_plot_pca' elbow curve plotted. 
  4 is the best number value for k in this model

  Scatter plot 'pca_predictions_plot' created. x="PC1" and y="PC2"
  Cryptocurrency name to the hover_cols parameter to identify the cryptocurrency that each data point represents

Composite Plots
  Composite Elbow Curve Plots 'elbow_plot_scaled' and 'elbow_plot_pca' created using hvPlot to compare cryptocurrency clusters from the Scaled_df and PCA_df respectively.

  Composite Scatter Plots 'scaled_data_predictions_plot' and 'pca_predictions_plot'created using hvPlot to compare cryptocurrency clusters from the Scaled_df, and PCA_df respectively. 

  Refer to Analysis above for findings. 
















