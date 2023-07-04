# Interchangeability of ngrams models between heterogeneous dataset
Reposotiry beloning to the posterpresentation during DH2023. 

## Introduction

## Method 1: ngram frequency similarity

### Old versus new
'```\n+--------------------------------------------------------------------+\n|ngram type|      version      |  ngram |  metric |pvalue|significant|\n+----------+-------------------+--------+---------+------+-----------+\n|   word   |1584_1883 vs na1947| bigram |frequency|  0.0 |    yes    |\n+----------+-------------------+--------+---------+------+-----------+\n|   word   |1584_1883 vs na1947| trigram|frequency|  0.0 |    yes    |\n+----------+-------------------+--------+---------+------+-----------+\n|   word   |1584_1883 vs na1947|fourgram|frequency| 0.07 |     no    |\n+----------+-------------------+--------+---------+------+-----------+\n|   char   |1584_1883 vs na1947| bigram |frequency| 0.11 |     no    |\n+----------+-------------------+--------+---------+------+-----------+\n|   char   |1584_1883 vs na1947| trigram|frequency| 0.79 |     no    |\n+----------+-------------------+--------+---------+------+-----------+\n|   char   |1584_1883 vs na1947|fourgram|frequency| 0.05 |    yes    |\n+--------------------------------------------------------------------+```'

## Method 2: overlapping ngrams

## Method 3: perplexity

