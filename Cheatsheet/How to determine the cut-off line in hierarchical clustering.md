# How to determine the cut-off line in hierarchical clustering

The cut-off line in hierarchical clustering, which determines the final number of clusters (K), is typically determined by a combination of visual inspection of the dendrogram and considering the application's specific needs or constraints.

<img width="740" height="405" alt="image" src="https://github.com/user-attachments/assets/d2e99e69-749d-42c9-a9fa-d5058fd8cfe1" />

The primary methods are:

## 1. Visual Inspection of the Dendrogram 🌲
This is the most common and intuitive method, relying on finding the largest gaps in the hierarchy.

* Find the Longest Vertical Lines: Look for the largest vertical distances (dissimilarities) that have not yet been traversed by a horizontal merger line. These gaps represent points where the clusters are most naturally 
separated.
* Set the Cutoff: Draw a horizontal line (the cutoff) that intersects the dendrogram branches within the height of these large gaps.
* Determine K: The number of vertical lines the cutoff line intersects determines the final number of clusters (K).

Example: In the image above , the red dashed line is set at a certain Cluster distance that results in four distinct clusters (Orange, Green, Cyan, Yellow), as it crosses four main branches.


## 2. Using an Absolute Distance Threshold
If you have domain knowledge, you can set a specific distance threshold based on what constitutes "similar" for your application.

* Fixed Threshold: Choose a fixed distance value $D_{cutoff}$ on the vertical axis.
* Interpretation: Any data points or groups merged below this line are considered part of the same cluster, while groups merged above this line remain separate.
* Scenario: If clustering customers based on the distance between their weekly spend and site visits, you might decide that a "distance" greater than 50 units (e.g., D>50) means the customers are fundamentally different, and
you set your cutoff there.

## 3. Defining a Target Number of Clusters (K)
If the business problem requires a specific number of groups, you can work backward from K.

* Target K: If you need exactly K=3 clusters, you simply move the horizontal cutoff line down from the top until it intersects exactly three vertical branches.
* Use the Dendrogram: You use the dendrogram to find the precise distance that yields the required K, allowing you to see which clusters are merged last to form K−1 groups.

In essence, the choice of the cutoff line is a trade-off between having a few large, highly dissimilar clusters (cutting high up) and many small, highly similar clusters (cutting low down).
