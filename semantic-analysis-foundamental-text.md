# Semantic Analysis Intro - Text

Note of semantic analysis. Most of the info here is summary of a [blog on semantic analysis](http://www.flickering.cn/ads/2015/02/%E8%AF%AD%E4%B9%89%E5%88%86%E6%9E%90%E7%9A%84%E4%B8%80%E4%BA%9B%E6%96%B9%E6%B3%95%E4%B8%80/).

**My reflection:** There are three scales to form a hierarchy of semantic analysis. They are:

- 1 From **character** to **word** (Word segmentation, Term weights).
- 2 From **word** to **sentence**, and sentence to **documents** (Word vector, sentence vector, pLSA, LDA, CNN, RNN/LSTM).

## Part I: From character to word

[The blog](http://www.flickering.cn/ads/2015/02/%E8%AF%AD%E4%B9%89%E5%88%86%E6%9E%90%E7%9A%84%E4%B8%80%E4%BA%9B%E6%96%B9%E6%B3%95%E4%B8%80/) introduced several applications and algorithms for text pre-processing.

- **Word segmentation** and **Part-of-speech** (N-gram, HMM,CRF, NN, RNN, LSTM). These 2 tasks can be done in sequence in a pipeline. They also can be trained jointly (more accurate with higher computational/time cost).
- **Term-weights**: This is important for (1) information extraction/retrieval and (2) similarity evaluation. The weights mainly consist of 3 parts: _Local_, _Global_, and _Normalization_. Algorithms: **Tf-Idf** (L:FREQ, G:IDFB, N:None). The weights can be done in a un-supervised learning or supervised learning (extract term weights from large amount of data, instead of manual labeling).
- **Extract key terms, and their features**: After obtain the term-weights, one can extract key words by setting thresholds of the weights. One can also extract features of these key terms to prepared for text classification and analysis.

## Part II: From word to sentence, and to documents

A widely applied analysis for document is **LDA** (Latent Dirichlet Allocation). Several key technologies in LDA:

- (1) [Conjugate prior](https://en.wikipedia.org/wiki/Conjugate_prior). Assume $X_1$ = $A X_2$, where A is likelihood function, $X_1$ is prior distribution, and $X_2$ is posterior distribution. If $X_1$ and $X_2$ are in the same family, they are called a **conjugate distributions**. And the _prior_ is called a _conjugate prior_ for the _likelihood_ function $A$. A table of conjugate distributions are listed in [wiki](https://en.wikipedia.org/wiki/Conjugate_prior).

- (2) [Dirichlet distribution](https://en.wikipedia.org/wiki/Dirichlet_distribution.) Dir($\alpha$) and also _Symmetric Dirichelt distribution_. In practice it is recommended to set the hyperparameter $\alpha$ < 1, so that Dir($\alpha$) the probability distribution can provide several peaks (recall that our aim is to extract key features to reduce dimension - to select several words or topics that have the highest probability).

- (3) Model training: Gibbs sampling and updating.

- (4) LDA assumptions: In LDA model, it is assumed that under each topic, each word are conditional independent and shares the same parameter.

- (5) Industrial application: Parallelization of pLSA, LDA. Sampling-base inference.
