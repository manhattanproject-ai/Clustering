# Explain different linkage method 

<img width="545" height="503" alt="image" src="https://github.com/user-attachments/assets/48abca0d-5687-4fc8-8a56-a1da961694ef" />

The choice of a linkage method in Agglomerative Hierarchical Clustering determines how the distance between two existing clusters is measured before deciding which clusters to merge. Different linkage methods lead to 
different cluster shapes and outcomes.

## 🔗 The Linkage Methods
Let A and B be two clusters, and let $x_i$ be a point in A and $x_j$ be a point in B.

### 1. Single Linkage (MIN)

* Definition: The distance between A and B is the minimum distance between any point in A and any point in B.

$\text{Distance}(A, B) = \min_{x_i \in A, x_j \in B} \text{Distance}(x_i, x_j)$

* Intuition: It's the "nearest neighbor" distance. Clusters are merged as soon as their closest points are near each other.
* Effect: Tends to form long, elongated clusters. It is susceptible to chaining, where small bridges of close points connect distant clusters.

### 2. Complete Linkage (MAX)

* Definition: The distance between A and B is the maximum distance between any point in A and any point in B.

$\text{Distance}(A, B) = \max_{x_i \in A, x_j \in B} \text{Distance}(x_i, x_j)$

* Intuition: It's the "farthest neighbor" distance. It forces all points in the merged cluster to be close to one another.
* Effect: Tends to form more compact and spherical clusters. It is less susceptible to chaining than single linkage.

### 3. Average Linkage (AVG)

* Definition: The distance between A and B is the average distance between all possible pairs of points, one from A and one from B.

$\text{Distance}(A, B) = \frac{1}{|A||B|} \sum_{x_i \in A} \sum_{x_j \in B} \text{Distance}(x_i, x_j)$

* Intuition: It's a compromise between single and complete linkage. It considers the entire cluster structure.
* Effect: Tends to produce clusters that are more balanced in size and shape than single or complete linkage.

### 4. Ward's Method

* Definition: The merge criterion is based on the increase in the total Within-Cluster Sum of Squares (WCSS) that would result from combining the two clusters.
* Objective: To minimize the total WCSS for all clusters. It looks for the pair of clusters whose merger results in the smallest increase in variance.
* Effect: Strongly biased towards producing compact, spherical clusters of roughly equal size, similar to the goal of K-means. It is often the preferred default method.

## Simple Numerical Example
Imagine two clusters, A and B, with the following distances between their points:

|Point in A|	Point in B|	Distance|
|--------|---|---|
|$A_1$|  $B_1$|  1.0|
|$A_1$|  $B_2$|  3.0|
|$A_2$|  $B_1$|  2.0|
|$A_2$|  $B_2$|  4.0|

The four distances between the pairs are {1.0,3.0,2.0,4.0}.

|Linkage Method|	Calculation	|Resulting Distance|
|--------|---|---|
|Single Linkage|	min(1.0,3.0,2.0,4.0)|	1.0|
|Complete Linkage|	max(1.0,3.0,2.0,4.0)|	4.0|
|Average Linkage|	  (1.0+3.0+2.0+4.0)/4|  2.5|


## Based on these results:

* Single Linkage would merge these two clusters first if no other cluster pairs had a distance less than 1.0.
* Complete Linkage would wait longer to merge them, only doing so when all other potential cluster pairs are further apart than 4.0.
