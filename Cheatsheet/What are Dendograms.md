# What are Dendograms ?

A Dendrogram is a tree-like diagram that is the primary output of Hierarchical Clustering algorithms. It illustrates the sequence of mergers (in Agglomerative/bottom-up clustering) or splits (in Divisive/top-down clustering) 
that occurred and the distance at which these operations took place.

<img width="740" height="405" alt="image" src="https://github.com/user-attachments/assets/619723c1-b543-4cd3-b2c4-d28d9457e015" />

## Key Components of a Dendrogram
The image above is a classic example of a dendrogram:

* Horizontal Axis (X-axis): This axis represents the individual data points (labeled 'a' through 'n' in the image) and the final clusters.
* Vertical Axis (Y-axis): This axis, labeled "Cluster distance," represents the dissimilarity or distance between the clusters when they were joined.
    * The height of the horizontal line connecting two clusters indicates the distance (or dissimilarity) between them at the moment of their merger.
    * Short vertical lines indicate that very similar data points or clusters were merged (e.g., merging 'a' and 'b').
    * Tall vertical lines indicate that the two clusters being merged were very different from each other (e.g., the top-most horizontal bar merging the orange/green block with the cyan/yellow block).
 

## How to Determine Clusters (Cutting the Tree)
The dendrogram allows you to decide on the final number of clusters (K) by choosing a cutoff distance on the vertical axis.

* The Cutoff Line: In the image, the dashed red horizontal line acts as a cutoff.
* Counting Clusters: The number of times this cutoff line intersects a vertical line (the branches) determines the number of clusters (K).
* Result: By cutting the dendrogram at the level of the red dashed line, the data is partitioned into four main clusters corresponding to the colored branches below the line:
    * Orange Cluster: {a,b,c,d,e}
    * Green Cluster: {f,g,h}
    * Cyan Cluster: {i,j,k,l}
    * Yellow Cluster: {m,n}

If you had chosen a lower cutoff distance, you would get a higher number of smaller, more similar clusters. If you chose a higher cutoff distance (closer to the top), you would get fewer, larger, and more dissimilar clusters.
