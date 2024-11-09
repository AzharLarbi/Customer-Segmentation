# Customer Segmentation Project

This project focuses on segmenting automobile company customers into predefined categories (`A`, `B`, `C`, `D`) using clustering techniques. The goal is to analyze customer data, group customers into segments based on behavioral and demographic features, and map predicted segments for new customer data.

## Project Overview

Customer segmentation is an essential tool for identifying distinct groups within a customer base, allowing businesses to tailor marketing efforts, product offerings, and customer service to the unique needs of each segment. This project uses clustering algorithms to segment customers, helping businesses better understand and serve their customer base.

## Data

Data was sourced from [Kaggle-Customer Segmentation](https://www.kaggle.com/datasets/vetrirah/customer)

## Project Structure

The project is organized into the following stages:

1. **Data Preparation and Exploration**
2. **Feature Engineering and Scaling**
3. **Clustering and Model Selection**
4. **Segment Mapping and Prediction**

## Data Description

- **train_df**: The training dataset includes labeled customer data with a `Segmentation` column, containing segment labels (`A`, `B`, `C`, `D`) representing different customer groups.
- **test_df**: The test dataset contains unlabeled customer data for segmentation predictions. Note that it does not include the `Segmentation` column but has the same features as the training data.

### Key Columns:
- **Age**: Customer's age (important for segmentation)
- **Income**: Annual income level
- **SpendingScore**: A measure of customer spending behavior
- **FamilySize**: Size of customer's family
- Other relevant features influencing customer segmentation

## Approach and Methodology

### 1. Data Preparation and Exploration
   - Explored the dataset to understand feature distributions, detect outliers, and identify missing values.
   - Visualized the relationships among features to assess potential clusters.

### 2. Feature Engineering and Scaling
   - Scaled relevant features to ensure that different feature scales do not bias clustering.
   - Dropped the `Segmentation` column in `train_df_scaled` to allow the clustering algorithm to group data without prior labels.

### 3. Clustering and Model Selection
   - Experimented with several clustering algorithms to find the best method for segmenting customers:
   
     - **K-Means Clustering**:
       - Silhouette Score: **0.35**
       - K-Means performed well in terms of speed but resulted in less distinct clusters, as observed in the silhouette score.
   
     - **Agglomerative Hierarchical Clustering**:
       - Silhouette Score: **0.45**
       - Hierarchical clustering performed the best overall, providing better separation between clusters. It was able to capture more meaningful customer segments compared to K-Means.

     - **DBSCAN**:
       - Silhouette Score: **0.28**
       - DBSCAN was less effective due to its sensitivity to outliers, which affected its ability to form distinct clusters.

   - Based on these evaluations, **Agglomerative Hierarchical Clustering** was selected as the best model for customer segmentation due to its superior silhouette score and its ability to group customers into more meaningful segments.

### 4. Segment Mapping and Prediction
   - Predicted segments for `test_df` using the chosen clustering model.
   - Mapped cluster labels back to the original categories (`A`, `B`, `C`, `D`) using a label mapping dictionary to ensure consistency with the training labels.

## Model Performance and Insights
- **Evaluation Metrics**: Evaluated clustering quality using metrics like silhouette score and examined cluster characteristics.
- **Insights**: Derived insights from each segment’s unique characteristics, such as age distribution, spending behavior, and income levels.


## Files and Directories

- **train_df.csv**: Training dataset with labeled customer segments.
- **test_df.csv**: Test dataset for prediction.
- **notebooks/**: Jupyter notebooks with data exploration, clustering, and visualization steps.

## Future Work
- **Feature Selection**: Consider testing additional demographic or behavioral features for better segmentation.
- **Model Optimization**: Experiment with other clustering techniques, such as DBSCAN, and evaluate their effectiveness.
- **Dimensionality Reduction**: Use PCA or t-SNE for high-dimensional data visualization and potentially improve clustering accuracy.

## Conclusion

This segmentation project demonstrates the use of clustering for understanding customer segments, which can inform targeted marketing and customer relationship management strategies.
