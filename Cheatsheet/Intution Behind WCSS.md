# Intution Behind WCSS

The Within-Cluster Sum of Squares (WCSS) is the primary metric used by Partition-Based Clustering algorithms like K-means to measure the quality of a clustering result.

## 1. Intuition Behind WCSS
WCSS measures the compactness or cohesion of the clusters.

* Goal: The fundamental goal in K-means clustering is to minimize the WCSS. A lower WCSS indicates that the data points within each cluster are very close to their respective centroid (the mean point of the cluster), meaning the clusters are tight and well-defined.
* Calculation: WCSS is calculated as the sum of the squared distances between each data point ($P_i$) in a cluster and that cluster's centroid ($C_k$). This is summed up across all K clusters.
* Distance Metric: Squaring the distance ensures that points further away from the centroid are penalized more heavily, pushing the iterative algorithm to find cluster centers that are central to their assigned points.

The formula for WCSS is : 

$\text{WCSS} = \sum_{k=1}^{K} \sum_{P_i \in \text{Cluster}_k} \text{distance}(P_i, C_k)^2$

<img width="1400" height="617" alt="image" src="https://github.com/user-attachments/assets/217bac1f-ec86-4ba0-b5ef-f6e95b15f7ee" />

## 2. Example
Imagine a dataset that has been clustered into three groups: Cluster 1, Cluster 2, and Cluster 3 .

* Cluster 1 (Red): The algorithm calculates the distance between every red data point ($P_i$) and the red centroid ($C_1$), squares each distance, and sums them up.

   $\sum_{P_i \in \text{Cluster 1}} \text{distance}(P_i, C_1)^2$

* Cluster 2 (Blue): It does the same for the blue data points and the blue centroid ($C_2$).

   $\sum_{P_i \in \text{Cluster 2}} \text{distance}(P_i, C_2)^2$

* Cluster 3 (Green): And the same for the green data points and the green centroid ($C_3$).

   $\sum_{P_i \in \text{Cluster 3}} \text{distance}(P_i, C_3)^2$

The final WCSS is the sum of these three cluster-specific sums:

$\text{WCSS}$ = $\sum_{P_i \in \text{Cluster 1}} \text{distance}(P_i, C_1)^2$ + $\sum_{P_i \in \text{Cluster 2}} \text{distance}(P_i, C_2)^2$ + $\sum_{P_i \in \text{Cluster 3}} \text{distance}(P_i, C_3)^2$

In the K-means algorithm, the iterative steps of reassigning points and recalculating centroids are designed to constantly reduce this WCSS until the best possible clusters are found for the given number of K.

## 3. Numerical Example

Imagine we are trying to cluster users based on two features: Average Weekly Visits and Average Weekly Spend ($). We decide to use K-means to find K=2 clusters.

### Scenario and Initial Setup
We have 5 users (data points $P_1$ to $P_5$) and their feature values:

|User (P)|	Visits (x)|	Spend (y)|	Initial Cluster|
|--------|---|---|---|
|$P_1$| 10|	100|	Cluster 1|
|$P_2$| 12|	110|	Cluster 1|
|$P_3$| 2|	20|	Cluster 2|
|$P_4$| 3|30|	Cluster 2|
|$P_5$| 1|15|	Cluster 2|

### Step 1: Calculate Initial Centroids
Since we are just starting the iteration, we calculate the initial centroid for each of our two groups based on the points currently assigned to them.

* Centroid $C_1$ (Cluster 1) :

$$\begin{align*}
C_{1,x} &= \frac{10 + 12}{2} = 11 \\
C_{1,y} &= \frac{100 + 110}{2} = 105 \\
C_1 &= (11, 105)
\end{align*}$$

* Centroid $C_2$ (Cluster 2) :

$$\begin{align*}
C_{2,x} &= \frac{2 + 3 + 1}{3} = 2 \\
C_{2,y} &= \frac{20 + 30 + 15}{2} = 21.67 \\
C_2 &= (2, 21.67)
\end{align*}$$

### Step 2: Calculate WCSS for the Current Partition
The WCSS is the sum of the squared Euclidean distances from each point to its assigned centroid.

$\text{Distance}^2 = (x_{\text{point}} - x_{\text{centroid}})^2 + (y_{\text{point}} - y_{\text{centroid}})^2$

1. WCSS for Cluster 1 ($WCSS_1$)
   
|User ($P_i$)|	Visits (x)|	Spend (y)|	$C_1$=(11,105)|	$(Dist)^2$ Calculation|	$(Dist)^2$|
|--------|---|---|---|---|---| 
|$P_1$| 10|	100|	(11,105)|	$(10−11)^2$ + $(100−105)^2$=1+25|	26|
|$P_2$| 12|	110|	(11,105)|	$(12−11)^2$ + $(110−105)^2$ =1+25|	26|
|$WCSS_1$|	|		    |                                 |Sum|	52|

2. WCSS for Cluster 2 ($WCSS_2$)

|User ($P_i$)|	Visits (x)|	Spend (y)|	$C_2$=(2,21.67)|	$(Dist)^2$ Calculation|	$(Dist)^2$|
|--------|---|---|---|---|---|
|$P_3$| 2|	20|	(2,21.67)|	$(2−2)^2$ + $(20−21.67)^2$=0+2.79|	2.79|
|$P_4$| 3|	30|	(2,21.67)|	$(3−2)^2$ + $(30−21.67)^2$=1+69.39|	70.39|
|$P_5$| 1|	15|	(2,21.67)|	$(1−2)^2$ + $(15−21.67)^2$=1+44.49|	45.49|
|$WCSS_2$|	|		    |                                 |Sum|	118.67|


Final WCSS
The Total WCSS for this current partition is the sum of the WCSS from all clusters:

Total WCSS = $WCSS_1$ + $WCSS_2$
​ 
Total WCSS=52+118.67=170.67


## Intended Outcome

* In the next iteration of the K-means algorithm, the system would attempt to re-assign points (Step 2 of K-means) and re-calculate the centroids (Step 3 of K-means) to try and find a new partition where the Total WCSS is lower than 170.67.
* A smaller WCSS means the users in Cluster 1 are tightly grouped around (11, 105), representing High-Engagement, High-Value customers.
* The users in Cluster 2 are tightly grouped around (2, 21.67), representing Low-Engagement, Low-Value customers.
* The overall low WCSS confirms that the partitioning is effective at creating compact, homogeneous groups of users.
