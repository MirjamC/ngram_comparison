# Interchangeability of ngrams models between heterogeneous dataset
Reposotiry beloning to the posterpresentation during DH2023. 

## Introduction
We research the question: How, and to what extent, is an ngram model built upon corpus A interchangeable to measure the quality of corpus B?
We researched this for both time period and reading level. For time period  we used a set of .... books from period ... and ... books for period ... . For the reading level we used the Wikipedia datsets of ... words and .... words. 

We used three methods to gain insights in this question: we measured the similarity between the ngram frequencies of the set using a Wilcoxon rank sum test. We calculated the percentage of overlapping ngrams between sets and we trained models to calculate the perplexity.

## Method 1: ngram frequency similarity

### Old versus new
|    | ngram type   | version             | ngram    | metric    |       pvalue | significant   |
|---:|:-------------|:--------------------|:---------|:----------|-------------:|:--------------|
|  0 | word         | 1584_1883 vs na1947 | bigram   | frequency | 0            | yes           |
|  1 | word         | 1584_1883 vs na1947 | trigram  | frequency | 2.88716e-292 | yes           |
|  2 | word         | 1584_1883 vs na1947 | fourgram | frequency | 0.0669261    | no            |
|  3 | char         | 1584_1883 vs na1947 | bigram   | frequency | 0.10927      | no            |
|  4 | char         | 1584_1883 vs na1947 | trigram  | frequency | 0.794257     | no            |
|  5 | char         | 1584_1883 vs na1947 | fourgram | frequency | 0.0491289    | yes           |

Samples:
For timepriod 1548 till 1883 the samples for all ngrams had a significant difference according to the wilkonson rank sum test.
For the after 1947 set, the outcomes of the words show no significant difference whereas the chars does. 

### Reading level
|    | ngram type   | version          | ngram    | metric    |       pvalue | significant   |
|---:|:-------------|:-----------------|:---------|:----------|-------------:|:--------------|
|  0 | word         | simple vs normal | bigram   | frequency | 0            | yes           |
|  1 | word         | simple vs normal | trigram  | frequency | 0            | yes           |
|  2 | word         | simple vs normal | fourgram | frequency | 0            | yes           |
|  3 | char         | simple vs normal | bigram   | frequency | 8.56364e-24  | yes           |
|  4 | char         | simple vs normal | trigram  | frequency | 3.66058e-276 | yes           |
|  5 | char         | simple vs normal | fourgram | frequency | 0            | yes           |

## Method 2: overlapping ngrams
### Old versus new
| ngram type   | version             | ngram    | % ngrams in intersection    
|:-------------|:-------------------- |:---------|:----------|
| word         | 1584_1883            | bigram   | 14.3% | 
| word         | na1947               | bigram   | 16.8% | 
| word         | 1584_1883            | trigram  | 5.9% | 
| word         | na1947               | trigram  | 6.4% | 
| word         | 1584_1883            | fourgram | 2.1% | 
| word         | na1947               | fourgram | 2.2% | 
| char         | 1584_1883            | bigram   | 70.5% | 
| char         | na1947               | bigram   | 80.3% | 
| char         | 1584_1883            | trigram  | 71.7% | 
| char         | na1947               | trigram  | 76.6% | 
| char         | 1584_1883            | fourgram | 63.1% | 
| char         | na1947               | fourgram | 68.3% | 

## Method 3: perplexity

