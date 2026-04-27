AI-Driven Agricultural Region Segmentation Using K-Means Clustering

Project Overview

This project focuses on grouping agricultural regions based on environmental conditions and crop yield characteristics using the K-Means Clustering Algorithm. The objective is to identify hidden patterns among agricultural regions and classify them into meaningful clusters based on similarity.

Since there are no predefined labels such as "high productivity" or "low productivity," this is an Unsupervised Machine Learning problem.

The system uses multiple agricultural and environmental factors such as rainfall, soil nutrients, irrigation, crop diversity, and yield performance to form clusters that help analyze agricultural productivity.


---

Problem Statement

Design and develop a K-Means clustering–based analytical system to group agricultural regions based on crop yield characteristics and environmental factors.

The project includes:

Exploratory Data Analysis (EDA)

Data Preprocessing

Feature Selection

PCA-based Visualization

Elbow Method for optimal K selection

K-Means Clustering

Silhouette Score evaluation

Prediction for new unseen agricultural data



---

Dataset Information

Final Dataset Size

Rows: 1050

Columns: 20 original features


Features Used

1. Rainfall


2. Temperature


3. Soil Moisture


4. Soil pH


5. Nitrogen


6. Phosphorus


7. Potassium


8. Irrigation


9. Crop Area


10. Fertilizer


11. Pesticide


12. Sunlight


13. Humidity


14. Altitude


15. Wind Speed


16. Groundwater


17. Crop Diversity


18. Mechanization


19. Yield Variance


20. Average Yield



Additional columns like Region and Date were removed during preprocessing since they were not useful for clustering.


---

Technologies and Libraries Used

Programming Language

Python


Platform

Jupyter Notebook

Visual Studio Code


Libraries Used

Pandas

NumPy

Matplotlib

Seaborn

Scikit-learn (sklearn)

Statsmodels

Joblib



---

Project Workflow


---

Phase 1: Data Collection

A structured agricultural dataset containing 20 region-level features was collected and prepared.

The dataset includes environmental factors, soil quality indicators, irrigation details, and crop productivity metrics.


---

Phase 2: Exploratory Data Analysis (EDA)

EDA was performed to understand the dataset and identify problems before preprocessing.

EDA Steps Performed

Checked data types using df.info()

Identified missing values using df.isnull().sum()

Generated statistical summaries using df.describe()

Used histograms for feature distribution analysis

Used boxplots for outlier detection

Generated correlation heatmap for relationship analysis

Created scatter plots for important relationships


Key Findings

Missing values were present in multiple columns

Outliers were detected in Rainfall, Crop Area, and Altitude

Strong positive correlation found between:

Rainfall and Soil Moisture

Irrigation and Average Yield

Nitrogen and Average Yield




---

Phase 3: Data Preprocessing

The raw dataset was cleaned and converted into machine learning-ready format.

Steps Performed

1. Removed Unnecessary Columns

Removed:

Region

Date


Reason:

These columns are not useful for K-Means because clustering requires numerical input.


---

2. Text to Numeric Conversion

Columns containing values like:

"8 hours"

"75%"

"7.2 pH"


were converted into pure numeric values.

Example:

8 hours → 8

75% → 75



---

3. Missing Value Handling

Used Mean Imputation to replace missing values.

Reason:

Deleting rows could reduce useful data and weaken clustering quality.


---

4. Duplicate Check

Duplicate rows were checked using:

df.duplicated().sum()

Result:

No duplicate rows found



---

5. Outlier Handling

Used IQR Method for outlier treatment.

Formula:

IQR = Q3 - Q1

Instead of deleting rows, outliers were capped using clipping to preserve useful agricultural observations.


---

6. Feature Scaling

Used:

StandardScaler

Formula:

z = (x - mean) / standard deviation

Reason:

K-Means uses distance calculations, so all features must be on the same scale.

This prevents large-value features like Crop Area from dominating smaller features like Soil pH.

After scaling:

Mean ≈ 0

Standard Deviation ≈ 1



---

Phase 4: Feature Selection

Used:

OLS Regression (Ordinary Least Squares)

for feature selection.


---

Why OLS?

K-Means is an unsupervised algorithm and does not provide feature importance directly.

So, Average Yield was used as a proxy target variable to identify important features.


---

Backward Elimination Rule

If:

p-value < 0.05

→ Feature is important → Keep

If:

p-value > 0.05

→ Feature is weak → Remove


---

Removed Features

Groundwater

Humidity

Altitude

Wind Speed


These had high p-values and weak contribution toward Average Yield.


---

Final Selected Features

1. Rainfall


2. Temperature


3. Soil Moisture


4. Soil pH


5. Nitrogen


6. Phosphorus


7. Irrigation


8. Crop Area


9. Fertilizer


10. Pesticide


11. Sunlight


12. Crop Diversity


13. Mechanization


14. Yield Variance



Final R² Score

R² = 0.826

This means 82.6% of crop yield variation is explained by selected features.


---

Phase 5: PCA Visualization

Used:

PCA (Principal Component Analysis)

Purpose:

To reduce high-dimensional feature space into 2 dimensions for visualization.

Transformation

14 Features → 2 Principal Components

Result

The PCA scatter plot showed visible natural grouping patterns, indicating that meaningful clustering exists in the dataset.

This confirmed that K-Means clustering is suitable.


---

Phase 6: Model Training (K-Means)

Elbow Method

Used to determine the optimal number of clusters (K).

WCSS (Within Cluster Sum of Squares) was plotted against different values of K.

The elbow point indicates the best number of clusters.


---

K-Means Clustering

After selecting the optimal K, the K-Means algorithm is applied to group agricultural regions into clusters.

These clusters represent regions with similar agricultural characteristics.


---

Phase 7: Evaluation and Prediction

Evaluation Metric

Silhouette Score

Used to evaluate clustering quality.

Interpretation:

Closer to +1 → Better clustering

Near 0 → Overlapping clusters

Negative → Poor clustering



---

Prediction for New Data

The trained model can predict cluster labels for new agricultural data.

Workflow:

New Input Data
→ Preprocessing
→ Feature Scaling
→ Load Saved Model
→ Cluster Prediction

This demonstrates real-world practical applicability.


---

Model Saving

Used:

Joblib

Saved:

StandardScaler

K-Means Model


Files:

scaler.pkl
kmeans_agri_model.pkl

This allows future prediction without retraining the model.


---

Conclusion

This project successfully demonstrates how K-Means clustering can be used to segment agricultural regions based on environmental and crop yield characteristics.

By combining preprocessing, feature selection, PCA visualization, and clustering evaluation, the system provides meaningful agricultural grouping and supports decision-making for improved productivity.

The model can also predict cluster labels for new unseen regional data, making it practically useful beyond academic implementation.


---

Authors

Kartikeya Arya

Aayush Rawat

Aashish Singh


B.Tech CSE (AI & ML)

Graphic Era University
