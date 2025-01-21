# Clustering_Model_MFG_Use-case_Aescape

# Project: Identifying and Clustering Similar Manufacturing Issues/Defects

## Overview
This project aims to identify and group similar issues or defects in a manufacturing context. By leveraging a combination of natural language processing (NLP) for text data and machine learning techniques for clustering, we can categorize and analyze defects that have been reported in manufacturing systems. The goal is to automate the detection of similar issues, which will help improve response times, troubleshooting, and defect analysis.

## Dataset
The dataset consists of 961 records related to manufacturing issues. The columns include:

System (Level 1): The broad category of the system where the issue was observed (e.g., "Headrest Assembly").
Subsystem (Level 2): The more specific component or subsystem involved.
Component (Level 3): The exact part of the subsystem that encountered the defect.
Summary: A brief summary of the issue.
Description: A detailed explanation of the issue.
Failure Mode: The specific failure mode associated with the defect.
Root Cause: The underlying cause of the defect.
Environment: The conditions under which the issue occurred.
FFF Framework: Framework classification related to the defect.

## Steps Involved in the Project
#### 1. Handling Missing Values
Missing values in the dataset were handled using appropriate strategies:
Mode Imputation for categorical columns (System (Level 1), Subsystem (Level 2), Component (Level 3)).
Placeholder Imputation for text columns (Description, Root_Cause, Environment, FFF Framework).
Dropping Missing Target Values (Failure_Mode), as this is the target variable for clustering.
#### 2. Feature Engineering
Three new features—System (Level 1), Sub-system (Level 2), and Component (Level 3)—were added to enrich the dataset for better performance. The text features (Summary, Description, Failure_Mode, Root_Cause) were combined and vectorized using the TF-IDF technique. Categorical columns were processed using Label Encoding. The combined text and encoded categorical data provided a comprehensive representation of each issue.
#### 3. Vectorization
The text data (summarized and descriptive features) was converted into numerical vectors using TF-IDF vectorizer. This helps capture the importance of each term in relation to the entire dataset.
Categorical data was converted into numerical values using encoding techniques (e.g., One-Hot Encoding for categorical features and Label Encoding for ordinal features).
#### 4. Clustering (K-Means Algorithm)
The K-Means clustering algorithm was applied to group similar defects based on both the text features and encoded categorical data. The number of clusters was set to 5, but this can be adjusted based on the dataset's characteristics.
Each record in the dataset was assigned to one of the clusters, facilitating easy identification of similar issues.
#### 5. Similarity Measure
Cosine Similarity was used to compare a new issue with existing issues in the dataset. By calculating the cosine similarity between the new issue’s vector and the dataset’s vectors, we could identify the top 5 most similar issues.
#### 6. Dimensionality Reduction (PCA)
Principal Component Analysis (PCA) was applied to reduce the high-dimensional feature space and make it easier to visualize the clustering results.
The reduced dimensions were plotted on a 2D scatter plot, where the points are colored by cluster labels.
#### 7. Visualization
A PCA-based scatter plot was generated to visually explore the clustering results. This helps in understanding how the clusters are distributed in the 2D feature space and aids in visualizing similarities between different issues.
Key Features:
Automatic Similarity Detection: By clustering and measuring similarity, the system can automatically identify similar defects/issues from a new input.
Scalability: The approach can be easily scaled to handle larger datasets in manufacturing settings, offering a tool for automatic defect analysis.
Text & Categorical Data Handling: The project efficiently integrates both unstructured text data (issue descriptions) and structured categorical data (system, component, environment) into the analysis.
Future Improvements:
Hyperparameter Tuning: Experiment with different numbers of clusters in the K-Means algorithm to improve clustering quality.
Advanced Text Vectorization: Consider using more advanced NLP techniques like Word2Vec, GloVe, or Transformer-based models (e.g., BERT) to capture deeper semantic relationships in the text data.
Interactive Dashboard: Build an interactive dashboard to visualize clusters, trends, and explore defects based on user inputs.
Conclusion
This project demonstrates how we can use machine learning and natural language processing to automatically identify and group similar defects/issues in a manufacturing environment. By clustering similar issues, manufacturers can speed up defect resolution and gain insights into common failure modes, ultimately improving product quality and manufacturing efficiency.

#### Libraries in the Project:
Python Libraries: pandas, numpy, scikit-learn, matplotlib
Machine Learning: K-Means, PCA
NLP: TF-IDF vectorization
