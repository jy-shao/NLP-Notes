# Semantic Analysis Intro - Text

Note of semantic analysis. Most of the info here is summary of a [blog on semantic analysis](http://www.flickering.cn/ads/2015/02/%E8%AF%AD%E4%B9%89%E5%88%86%E6%9E%90%E7%9A%84%E4%B8%80%E4%BA%9B%E6%96%B9%E6%B3%95%E4%B8%80/).

**My reflection:** There are three scales to form a hierarchy of semantic analysis. They are:

- 1 From **character** to **word** (Word segmentation, Term weights).
- 2 From **word** to **sentence**, and sentence to **documents** (Word vector, sentence vector, LDA, PLSA, CNN, RNN/LSTM).

## Part I: From character to word

[The blog](http://www.flickering.cn/ads/2015/02/%E8%AF%AD%E4%B9%89%E5%88%86%E6%9E%90%E7%9A%84%E4%B8%80%E4%BA%9B%E6%96%B9%E6%B3%95%E4%B8%80/) introduce semantic analyis from 4 aspects. They are:

- 1 Text pre-processing

  - **Word segmentation** and **Part-of-speech** (N-gram, HMM,CRF, NN, RNN, LSTM). These 2 tasks can be done in sequence in a pipeline. They also can be trained jointly (more accurate with higher computational/time cost).
  - **Term-weights**: This is important for (1) information extraction/retrieval and (2) similarity evaluation. The weights mainly consist of 3 parts: _Local_, _Global_, and _Normalization_. Algorithms: **Tf-Idf** (L:FREQ, G:IDFB, N:None). The weights can be done in a un-supervised learning or supervised learning (extract term weights from large amount of data, instead of manual labeling). After obtain the term-weights, one can extract key words by setting thresholds of the weights.

## Part II: From word to sentence, and to documents
