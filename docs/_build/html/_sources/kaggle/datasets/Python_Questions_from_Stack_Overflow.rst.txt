
.. questions-clustering documentation master file, created by
   sphinx-quickstart on Tue Oct  2 16:53:05 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. questions-clustering documentation master file, created by
   sphinx-quickstart on Tue Oct  2 16:53:05 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.


.. toctree::
   :maxdepth: 2
   :caption: Contents:


Python_Questions_from_Stack_Overflow 
================================================

This database is pretty similar to the AnyHelper one, and we found some **interesting kernels** about question clustering.

=======
Dataset
=======
Full text of all **questions and answers from Stack Overflow** that are tagged with the python tag. Useful for natural language processing and community analysis. See also the dataset of R questions.

The dataset contains questions all questions asked between August 2, 2008 and Ocotober 19, 2016.

Kernel: LSA analysis for questions clustering
====================================================
This kernel uses the Latent Semantic Analysis to find clusters of questions. You can find a commented version at the `github repo <https://www.kaggle.com/alessandrosolbiati/identifying-clusters-of-related-questions-088d3f>`_ or `Kaggle repo <https://www.kaggle.com/alessandrosolbiati/identifying-clusters-of-related-questions-088d3f>`_, in the comments there are also resources to get familiar with concepts like LSA and tf-idf that will thus not be explained in detail here. 

====
Kernel Overview
====
This is the step implemented in the kernels:

1. **Data Cleaning (I): re**
      First of all the data is cleaned using regular expressions, and combining title and body together
2. **Data Cleaning (II): Stemming and Lemmatizing**
      A second step in data cleaning is Stemming and Lemmatizing, that is trying to reduce inflectional forms and derivations from common base form. This is applied to tokens of the single sentences. This is implemented with an external library WordNetLemmatizer
3. **Frequency vectors computation: TFIDF**
      The tf-idf is a statistic used to evalute the importance of a single word inside the document, it is computed using TfidVectorizer that will return the vectors. A vector represents the 'importance' of a single word.
4. **Dimensionality Reduction: SVD**
      A dimensionality reduction is executed on the tfidf vector to get rid of redundant data, implemented with TruncatedSVD.
5. **Metric computation: cosine similarity**
      This is the most common use text-similarity metrix, is computed on the whole vector dataframe using distance.pdist
6. **Cluster computation: scipy.cluster**
      Now that we computed our metric we can use hierarchical clustering to compute the clusters, hierarchy.linkage from scipy

And that's how you go from the raw question data to your final clusters. You can check-out the kernels on kaggle to see the output at [kaggle.com](the kernel fork page)
