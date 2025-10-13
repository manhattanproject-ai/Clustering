# How Kmeans works ?

K-means is an unsupervised learning algorithm used for partition-based clustering. It is an iterative process that groups n observations into a pre-defined number of k clusters, aiming to minimize the distance between data points and their assigned cluster center (centroid).

The primary objective is to minimize the Within-Cluster Sum of Squares (WCSS), also known as Inertia or the squared error function. WCSS measures the total squared distance between each point and its cluster's centroid.

$\text{WCSS} = \sum_{i=1}^{k} \sum_{x \in S_i} \|x - \mu_i\|^2$

Where $μ_i$ is the centroid of cluster $S_i$ , and x is a data point in that cluster.

## K-Means Algorithm Steps
The algorithm operates through an iterative two-step process (Expectation-Maximization) until convergence is reached.

## Step 1: Initialization (Defining K and Centroids) 📍
* Objective: To define the number of clusters and establish the initial starting points for the cluster centers.
* Process:
  * Choose K: Specify the number of clusters (K) you want the algorithm to find (this is a hyperparameter).
  * Initialize Centroids: Randomly select K data points from the dataset to serve as the initial centroids (cluster centers).
    * Note: The random initialization can sometimes lead to inconsistent results. Methods like K-means++ are often used to select initial centroids that are well-separated to improve the final clustering quality.
   
## Step 2: Assignment Step (Expectation, E-step) 🏷️
* Objective: To assign every data point to its closest, or "most similar," cluster centroid.
* Process: For every data point in the dataset, the algorithm calculates the distance (usually Euclidean distance) between that point and all K centroids.
* Result: Each data point is assigned to the cluster whose centroid has the minimum distance to that point.

## Step 3: Update Step (Maximization, M-step) 🔄
* Objective: To move the cluster centroids to the actual center of the points currently assigned to that cluster, thereby reducing the WCSS.
* Process: For each of the K clusters, the algorithm recalculates the new centroid location by computing the arithmetic mean (average) of all the data points assigned to that cluster.
* The old centroid is replaced by this new mean position.

## Step 4: Convergence (Repeat) 🔁
* Objective: To continue the iterative process (Steps 2 and 3) until a stable and optimized clustering structure is achieved.
* Process: Steps 2 (Assignment) and 3 (Update) are repeated until one of the following stopping criteria is met:
   * The centroids no longer change position significantly.
   * The data points remain in the same cluster assignments.
   * A maximum number of iterations (set by the user) is reached.

The entire process is guaranteed to converge because the total WCSS (error) is non-increasing at every step.
