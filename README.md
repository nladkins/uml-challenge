# Cryptocurrency Clusters

## Background

The purpose of this repository is to create a report to determine whether crypto currencies can be grouped to create a classification system for this investment.

Using a set of raw data for cryptocurrency was used including `CoinName` `Algorithm`, `IsTrading`, `ProofType`, `TotalCoinsMined`, and `TotalCoinSupply`, it needed to be processed to fit the machine learning models.  Since there was no known classification system, an unsupervised learning approach was used.   Clustering algorithms were used to explore whether the cryptocurrencies can be grouped together with other similar cryptocurrencies.  Further, data visualation was developed to share some of the findings.  

## Data Preparation

The dataset was obtained from [CryptoCompare](https://min-api.cryptocompare.com/data/all/coinlist).

The first step was to discard all cryptocurrencies that are not being traded by filtering currencies that are `true` for `IsTrading`.  Subsequent to this, the `IsTrading` column was dropped (`df.drop`) from the dataframe.  All rows with any null values were removed and the data was filtered further by identifying cryptocurrencies that have been mined (`TotalCoinsMined > 0`).

In order for the dataset to be comprehensible to a machine learning algorithm, the data was converted to a numeric format. The `CoinName` was also dropped from the original dataframe as it did not contribute toward the analysis.

The next step in data preparation was to convert the remaining features with text values, `Algorithm` and `ProofType`, into numerical data.  This was completed by creating using `get_dummies`.  The dataset was then standardized so that columns with larger values did not influence the outcome.  

## Dimensionality Reduction

Creating dummy variables above dramatically increased the number of features in the dataset.  The next step was to perform dimensionality reduction with `PCA`. Rather than specify the number of principal components when you instantiate the PCA model, it is possible to state the desired **explained variance**.  First step was to create a model that preserved 99% of the explained varience using `PCA(n_components=0.99)`.  Following this, an attempt was made to preserve 90% of the explained variance in dimensionality reduction.  This went from 101.34 to 92.82 for the explained variance of the principal components.

The next step was to further reduce the dataset dimensions with `t-SNE` and visually inspect the results. In order to accomplish this task, run `t-SNE` on the principal components: the output of the PCA transformation. Then create a scatter plot of the `t-SNE` output. Observe whether there are distinct clusters or not.

![alt text](https://github.com/[username]/[reponame]/blob/[branch]/image.jpg?raw=true)

### Cluster Analysis with k-Means

* Create an elbow plot to identify the best number of clusters. Use a for-loop to determine the inertia for each `k` between 1 through 10. Determine, if possible, where the elbow of the plot is, and at which value of `k` it appears.

### Recommendation

* Based on your findings, make a brief (1-2 sentences) recommendation to your clients. Can the cryptocurrencies be clustered together? If so, into how many clusters? 

## Rubric

[Unit 20 - Unsupervised Machine Learning Homework Rubric - Cryptocurrency Clusters](https://docs.google.com/document/d/1zhiC8-PtfMknDxYHagsTukryQAJSdXFRWa-aK3W28Vg/edit?usp=sharing)

- - -

## References

Crypto Coin Comparison Ltd. (2020) Coin market capitalization lists of crypto currencies and prices. Retrieved from [https://www.cryptocompare.com/coins/list/all/USD/1](https://www.cryptocompare.com/coins/list/all/USD/1)

- - -

© 2021 Trilogy Education Services, LLC, a 2U, Inc. brand. Confidential and Proprietary. All Rights Reserved.
