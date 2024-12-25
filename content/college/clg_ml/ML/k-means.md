# K-Means Clustering Working

1. Select the number K to decide the number of clusters.
2.  Select random K points or centroids. (It can be other than the input dataset).
3. Assign each data point to their closest centroid, which will form the predefined K clusters.
4. Calculate the variance and place a new centroid of each cluster.
5. Repeat the third step, which means reassigning each datapoint to the new closest centroid of each cluster.
<<F5>.If any reassignment occurs, then go to step 4 else go to FINISH.
- Step 7: The model is ready.

# highrarilcal clustering
- Hierarchical clustering is a type of unsupervised learning algorithm
- It groups data into a hierarchy of clusters, often visualized as a tree or dendrogram.
- Unlike K-means clustering, it doesn’t require a predefined number of clusters.
Dendrogram:
- A tree-like structure showing the hierarchy of clusters; the height represents the distance at which clusters are merged. The number of clusters can be decided by cutting the dendrogram at a specific level.
##  Agglomerative
- Agglomerative is a bottom-up approach, in which
- Here algorithm starts with taking all data points as single clusters and merging them until one cluster is left.
1. Create each data point as a single cluster. Let's say there are N data points, so the number of clusters will also be N.
2. Take two closest data points or clusters and merge them to form one cluster. So, there will now be N-1 clusters.
3. Again, take the two closest clusters and merge them together to form one cluster. There will be N-2 clusters.
4. Repeat Step 3 until only one cluster left. So, we will get the following clusters.
5. Once all the clusters are combined into one big cluster, develop the dendrogram to divide the clusters as per the problem.

## Divisivee
- Start with One Cluster
    - Begin with all data points in a single cluster.
- Split into Two Sub-clusters
    - Divide the cluster into two smaller groups based on dissimilarity   (using methods like K-means).
- Repeat Splitting
    - Continue dividing each new cluster until you reach the desired number of clusters or no meaningful splits remain.
- Stop When Satisfied
        End when clusters are distinct or meet a set condition (e.g., number of clusters).
- Visualize with Dendrogram (Optional)
 Optionally, use a dendrogram to show the split hierarchy.

# Measure the distance between 2 Clusters
1. Complete Linkage
----
- It is the farthest distance between the two points of two different clusters.
- It is one of the popular linkage methods as it forms tighter clusters than single-linkage.
----

2. Centroid Linkage
----
- It is the linkage method in which the distance between the centroid of the clusters is calculated.
----

3. Single Linkage:
----
- It is the Shortest Distance between the closest points of the clusters.
----

4. Average Linkage
----
- to calculate the average distance between two clusters
- Here the distance between each pair of datasets is added up and then divided by the total number of datasets.
- It is also one of the most popular linkage methods.
----


