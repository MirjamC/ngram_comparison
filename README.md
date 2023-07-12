# Interchangeability of ngrams models between heterogeneous dataset
Repository beloning to the posterpresentation during DH2023. 

## Introduction
Our research focussed on the research question: How, and to what extent, is an ngram model built upon corpus A interchangeable to measure the quality of corpus B?
We compared corpora from two time periods for which we used a set of ~1.9M words from 1584 to 1883, and ~2M word from 1947 or later. In addition, two Wikipedia corpora with different reading levels were compared. For both the  ‘normal’ and Simple Wikipedia corpora, we used ~7.6M words.
 
We used three methods to compare the corpora and measure their interchangeability: 
* 1) the similarity between ngram frequencies of the corpora was determined using Wilcoxon signed-rank test;
* 2) the percentage of overlapping ngrams between corpora was calculated;
* 3) NLTK ngram models were trained to calculate the perplexity on a test

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

![wordbigram](https://github.com/MirjamC/ngram_comparison/assets/37981069/a555b2be-4604-469a-9325-fc7a6e0c78da)
![wordtrigram](https://github.com/MirjamC/ngram_comparison/assets/37981069/bed319a9-a7a8-4bd6-b94a-3ca0570dd4ca)
![wordfourgram](https://github.com/MirjamC/ngram_comparison/assets/37981069/def72773-5f3d-4163-b179-debf4e44a2a2)

![charbigram](https://github.com/MirjamC/ngram_comparison/assets/37981069/7ef0d8bb-89eb-4fd8-abe4-db005ead852b)
![chartrigram](https://github.com/MirjamC/ngram_comparison/assets/37981069/99342c60-4871-43fc-af0a-a01d8074abc8)
![charfourgram](https://github.com/MirjamC/ngram_comparison/assets/37981069/54839975-7179-4e5e-9419-fab12a47ba34)

### Reading level
| ngram type   | version             | ngram    | % ngrams in intersection    
|:-------------|:-------------------- |:---------|:----------|
| word         | simple            | bigram   | 36% | 
| word         | normal               | bigram   | 29% | 
| word         | simple            | trigram  | 18.1% | 
| word         | normal               | trigram  | 15.7% | 
| word         | simple            | fourgram | 9.6% | 
| word         | normal               | fourgram | 8.8% | 
| char         | simple            | bigram   | 93.3% | 
| char         | normal               | bigram   | 94.9% | 
| char         | simple            | trigram  | 84% | 
| char         | normal               | trigram  | 78% | 
| char         | simple            | fourgram | 78.2% | 
| char         | normal               | fourgram | 70.2% | 


## Method 3: perplexity

Testset: data from 1584_1883
| ngram type   | model            | ngram    | median PPL model 1584_1883    | median PPL model after 1947 |
|:-------------|:-----------------|:---------|:----------|:----------|
| word         | 1584_1883        | bigram   | 13992   | 17862    | 
| word         | 1584_1883        | trigram   | 55319   |  5061 |
| word         | 1584_1883        | fourgram   | 67330   | 57063  |
| char        | 1584_1883        | bigram   | 253   | 136   | 
| char         | 1584_1883        | trigram   | 230   |  122 |
| char         | 1584_1883        | fourgram   | 217   | 117  |


Testset: data from Wikipedia
| ngram type   | model            | ngram    | median PPL simple    | median PPL model normal |
|:-------------|:-----------------|:---------|:----------|:----------|
| word         | simple        | bigram   | 5416   | 8398    | 
| word         | simple       | trigram   | 32042   |  50544 |
| word         | simple        | fourgram   | 57039   | 84169  |
| char        | simple      | bigram   | 267   | 242   | 
| char         | simple        | trigram   | 184   | 166 |
| char         | simple        | fourgram   | 163   | 148  |
| word         | normal        | bigram   | 9818    | 10509    | 
| word         | normal       | trigram   | 52784   | 62735 |
| word         | normal       | fourgram   | 83457   | 102926  |
| char        | normal      | bigram   | 210   | 190   | 
| char         | normal        | trigram   | 150   | 135 |
| char         | normal        | fourgram   | 142   | 128  |



