# Machine Learning

Improve on Task with respect to Performance metric based on Experience

## Supervised Learning

* Rote Learning
* Decision Tree

> * ID3
> * C4.5
> * CART

* Learning in Bayesian Inference

> $$P(A|B)=\frac{P(AB)}{P(B)}=\frac{P(A)P(B|A)}{P(B)}$$
>
> * Prior Probabilities: $P(A)$
> * Posterior Probability: $P(A|B)$
> * Class-conditional Probability:$P(B|A)$
>
> Models
>
> * Naive Bayesian Classifiers(NBC)
> * Bayesian Belief Network(BBN)
> * Gaussian Mixture Model(GMM)
> * HMM

### Overfitting Problem

* MDL
* Regularization

## Unsupervised Learning

Classical unsupervised learning only input data, but expected output is unknown. The process of dividing the data set into clusters accroding to the similarity between data. Discovering groups and Identifying interesting distributions in the underlying data.

* Partition clustering
* Hierarchical clustering
* Density based clustering
* Grid based clustering

key problems

* How to measure the similarity between data or clusters?

> * Distance: Widely used distance include Euclidean, City block, Chebyishev, Minkowski, and etc.
> * Statistical measure: Represent clusters by using statical models such as Gaussian. The Class-conditinal probability density can be used to measure the degree of a data belonging to the cluster.

* How to divide the data set?
* How to deal with the large dataset and high dimensionality?(scalability)

## K-means algorithm

Represent each cluster using its mean vector

1. Randomly select k data from the set as the initial mean vectors of clusters
2. Other data are partitioned into the closest cluster measured by its distance to corresponding mean vector
3. Update the mean vector of new generated clusters
4. Repeat Step 2-3, untill cluster is stable

Objective function

$$J(X,v)=\sum^n_{i=1}\sum^k_{j=1}(u_{ik})^m\rho(d(x_i,v_j))$$
$$\sum^k_{i=1}u_{ik}=1$$

* Time Complexity: $O(tkn)$
* Local Optimality
* Need to preset the number of clusters(k)
* Sensitive to noises and initial means

Application

* Bag-of-visual-word: Image representation based on local features

1. Build visual words
2. Feature clustering by K-means
3. Represent images by visual words

## K-mediods algorithm

Also called PAM(Partitioning Around Medoids) Use the medoid(representative data), instead of the mean, to represent each cluster

1. Randomly select k mediods
2. Compute total substitution cost for each pair of mediod h and other data i, let it be $TC_{ih}$
3. If the minimum $TC_{ih}<0$, the i is substitued by h
4. Repeat Step 2-3, untill the minimum $TC_{ih}\leq0$
5. Partition other data into the closet cluster measured by its distance to mediods

## CLARA algorithm

1. For i = 1 to m(iteration times), repeat the following steps
2. Random select n(sample size) object from the entire data set, and call PAM to find k medoids of the sample
3. For each object $O_j$ in the entire data set, determine which of the k medoids is the most similar to $O_j$
4. Calculate the average dissimilarity of the clustering obtained in the previous step. If the value is less than the current minimum, use the value as the current minimum, and retain the k medoids found in Step 2 as the best set of medoids obtained so far
5. Return to Step 1 to start the next iteration

## CLARANS algorithm

1. Input parameters numclocal and maxneighbor. Initialize i to i, and mincost to a large number
2. Set current to an arbitary node in $G_{n,k}$
3. Set j to 1
4. Consider a random neighbor S of current, and based on Equation, calculate the cost differential of the two nodes
5. If S has a lower cost, set current to S, and go to Step 3
6. Otherwise, increment j by 1. If j < maxneighbor, go to Step 4
7. Otherwise, the j > maxneighbor, compare the cost of current with minconst. If the former is less than mincost, set mincost to the cost of current, and set bestnode to current
8. Increment i by 1. If i > numlocal, output bestnode and halt. Otherwise, go to Step 2

## Hierarchical clustering

* Bottom-up Agglomerative Nesting. Firstly take each data as a cluster, then combine them gradually
* Top-down Divisive Analysis. Firstly take the whole set as a cluster, then split them gradully

Cluster distance

* Single-Linkage algorithm: distance = minimum distance between data
* Complate-Linkage algorithm: distance = maximum distance between data
* Average-Linkage algorithm: distance = the mean distance between data
* Centroid-Linkage algorithm, Median-Linkage altorithm, Ward algorithm...

Inproved algorithm

* BIRCH(1996): treat the process of hierachal clustering as tree
* CURE(1998): use a set of well-scattered point to represent each cluster
* CHAMELEON(1999): use dynamic model

## BIRCH algorithm

<!-- TODO: Description -->

## Density-Based Clustering

<!-- TODO:  -->

## Grid-based Clustering

<!-- TODO: -->
