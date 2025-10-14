# How Hierarchical Clustering Works ?

## 1. Initialization 🚀

* Start with Individuals: The process begins by treating every single data point in the dataset as its own cluster. If you have N data points, you start with N clusters.
* First Distance Calculation: The first step involves calculating the distance between every pair of individual points to find the two closest points to begin the merging process.

## 2. Iterative Merging (The Core Loop) 🔀

* Objective: The core of the algorithm is a repetitive loop where the two closest clusters are found and merged into a single, larger cluster.
* Distance Measurement (Linkage): To determine which clusters are "closest," a linkage criterion (such as Single, Complete, Average, or Ward's) is used to calculate the distance between clusters.
   * For example, using Single Linkage, the distance between two clusters is defined by the minimum distance between any two points in the respective clusters.
* Merge: The algorithm merges the cluster pair with the minimum distance determined by the linkage method.
* New Cluster: The merged pair now forms a new, single cluster.

## 3. Continuation and Termination 🛑

* Repeat: The process of calculating distances between all current clusters and merging the closest pair repeats.
* Hierarchy Built: Each merge is recorded, building the tree structure known as the dendrogram.
* Termination: The iterative merging continues until the stopping condition is met, which is typically when all data points have been merged into a single, comprehensive cluster.

The final output is the dendrogram, which can then be cut at a specific distance to yield the desired number of clusters.
