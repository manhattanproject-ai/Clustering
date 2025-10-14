# Detailed explanation of Hierarchical clustering

## Step 1 -  Initialization  🚀

<img width="1890" height="786" alt="image" src="https://github.com/user-attachments/assets/5006aba6-4518-40fe-8ac9-bb18519228ba" />

The initiation step has two main parts:

### 1. Treating Every Point as a Cluster
   
* The starting point of the algorithm is to treat every single data point in the dataset as its own individual cluster.
* If you have N data points, you begin with N clusters.

### 2. Calculating Initial Distances

* The first step involves calculating the distance (or dissimilarity) between every pair of these individual point-clusters.
* The Euclidean distance is the most commonly used distance metric for this initial calculation.
* The goal of this calculation is to find the two closest points (or clusters) to begin the merging process.

This initialization step prepares the algorithm to move into the iterative merging phase (Step 2), where the two closest clusters will be combined repeatedly until only one cluster remains.

## Step 2 - Iterative Merging (The Core Loop) 🔀

<img width="1872" height="544" alt="image" src="https://github.com/user-attachments/assets/286ad06f-aacd-466e-8462-d24df0f441a5" />

* Objective: The core of the algorithm is a repetitive loop where the two closest clusters are found and merged into a single, larger cluster.
* Distance Measurement (Linkage): To determine which clusters are "closest," a linkage criterion (such as Single, Complete, Average, or Ward's) is used to calculate the distance between clusters.
   * For example, using Single Linkage, the distance between two clusters is defined by the minimum distance between any two points in the respective clusters.
* Merge: The algorithm merges the cluster pair with the minimum distance determined by the linkage method.
* New Cluster: The merged pair now forms a new, single cluster.

## Step 3 - Finalization  🛑
Finalization occurs once the iterative merging process (Step 2) is complete.

<img width="1901" height="808" alt="image" src="https://github.com/user-attachments/assets/9748cf54-5d2a-43be-9a9d-89b0d4185648" />

### 1. Stopping Condition

* The process stops when the stopping condition is met, which, in pure Agglomerative clustering, is when all data points have been merged into a single, comprehensive cluster.
* At this point, the algorithm has a complete hierarchy of clusters, ranging from N individual clusters down to one single cluster.

### 2. Output: The Dendrogram

* The key output of the finalization step is the complete dendrogram.
* The dendrogram visually represents the entire history of the mergers and the distance (height) at which each merger occurred.

### 3. Cluster Determination (Post-Process)

* After the finalization, the actual clusters are determined by cutting the dendrogram at a chosen height (or distance threshold).
* The number of vertical lines intersected by the horizontal cut determines the final number of clusters (K). This allows the user to decide on the appropriate number of clusters after the algorithm has run, based on data
   structure or domain knowledge.

Now that we are done with the inner workings of the algorithm , lets implement it .  
