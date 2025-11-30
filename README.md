#  Student Performance Segmentation using K-Means Clustering

##  Project Overview

This capstone project focuses on applying **unsupervised machine learning (K-Means Clustering)** to a student performance dataset. The goal is to move beyond simple grade analysis and segment students into distinct, holistic profiles based on their academic outcomes, social habits, and family support systems. The resulting segments are intended to provide school administrators with **actionable insights** for targeted intervention programs.

##  Problem Statement and Objectives

**Problem Statement:** How can educational institutions proactively identify different categories of "at-risk" and "high-potential" students, considering complex non-academic factors, to optimize resource allocation?

**Objectives:**

1. To prepare and transform mixed (numerical and categorical) student data for clustering.

2. To use the **Elbow Method (WCSS)** to determine the optimal number of clusters ($K$). 

3. To train a K-Means model on the high-dimensional data set. 

4. To create clear, interpretable **cluster profiles** that describe the defining characteristics of each student segment (e.g., "Supported High Achievers" or "At-Risk Low Engagement").

## 📂 Dataset and Methodology

### Dataset

* **Source:** UCI Machine Learning Repository (Student Performance Data Set - Mathematics Course).

* **Key Features:** Grades (`G1`, `G2`, `G3`), `failures`, `absences`, `age`, parental education (`Medu`, `Fedu`), family support (`famsup`), and social factors (`goout`, `studytime`, `romantic`).

### Chosen Technique: K-Means Clustering

The K-Means algorithm was chosen because the problem requires **discovery** of groups (unsupervised), and its centroid-based output provides readily interpretable average profiles, which is essential for institutional reporting.

### Model Justification (K-Means vs. DBSCAN)

K-Means was compared against DBSCAN. K-Means was selected because it yielded a higher **Silhouette Score** and produced clusters with clearer, more spherical separation, which aligns better with the need for easily defined student segments.

##  Key Project Steps

1.  **Data Preprocessing:**

    * **Encoding:** Applied **One-Hot Encoding** to nominal variables (`Mjob`, `guardian`) and **Label Encoding** to binary variables (`schoolsup`, `romantic`).

    * **Scaling:** Applied **StandardScaler** to the entire feature set (30+ dimensions) to ensure distance calculations are fair and unbiased by feature magnitude.

2.  **Model Optimization:**

    * The **Elbow Method** (WCSS) was used to identify the optimal $K$, which was determined to be $K=4$.

3.  **Cluster Profiling:**

    * The model was trained with $K=4$.

    * The final interpretation relied on calculating the mean of every original feature within each cluster, providing a rich, actionable description of each segment.

##  Key Findings and Implications

The K-Means model successfully identified four key student segments (names below are illustrative, based on typical profile means):

| Cluster | Profile Summary | Academic Status | Actionable Recommendation |
| :--- | :--- | :--- | :--- |
| **Cluster 1** | **At-Risk & Highly Absent** | Lowest average G3, highest failures, highest absences. | Immediate mandatory academic tutoring and family counseling. |
| **Cluster 2** | **Resilient High Achievers** | Highest G3, low failures, high parental education. | Recruit as peer mentors; challenge with advanced coursework. |
| **Cluster 3** | **Average & Highly Social** | Moderate G3, low study time, high `goout` score. | Implement time-management workshops and stress counseling. |
| **Cluster 4** | **Struggling but Diligent** | Low G3, high study time, high `schoolsup`. | Indicates high effort but possible learning disability; requires specialized intervention. |

**Implication:** The project provides a data-driven system for allocating scarce resources where they are most needed, ensuring tailored support for each student's unique challenges.

##  Future Work

* Train a **supervised classification model (e.g., Logistic Regression)** using the generated cluster labels to predict which segment a *new* student will fall into based on their enrollment data.

* Conduct time-series analysis to track student transitions between clusters over successive academic years.

* Integrate the model into a dashboard interface (e.g., using Streamlit) for administrators and teachers.

##  Technologies Used

* Python (3.x)

* Pandas (Data Manipulation)

* NumPy (Numerical Operations)

* Scikit-learn (`KMeans`, `StandardScaler`, Encoders)

* Matplotlib & Seaborn (Data Visualization)
