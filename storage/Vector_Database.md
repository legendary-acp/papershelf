# Report on A Comprehensive Survey on Vector Database: Storage and Retrieval Technique, Challenge

## Table of Contents
1. [Introduction](#1-introduction)
2. [Paper Summary](#2-paper-summary)
3. [Key Concepts](#3-key-concepts)
4. [Learnings](#4-learnings)
5. [Conclusion](#5-conclusion)
6. [Paper](#6-paper-link)

## 1. Introduction
This paper attempts to consolidate all the information regarding vector databases including algorithms for solving ANN and NNN problem using hash-based, tree-based & graph-based approaches. 
It also mentioned what challenges are faced while developing vector databases.
It also touched upon use cases of combining Large Language Models with Vector Database and vice versa, how they can help each other in generating value.
At last it introduced Retrieval-Based LLM which is enhancement of LLMs and hot topic of research. 

## 2. Paper Summary
- **Title & Authors** 
A Comprehensive Survey on Vector Database: Storage and Retrieval Technique, Challenge by Yikun Han, Chunjiang Liu and Pengfei Wang
- **Abstract Summary**
The abstract of the paper gave a clear idea of what to expect from it. The paper tries to review existing algorithms and the architecture of vector databases and how they solve problems like storing high-dimensional data, the nearest neighbor search problem, etc. It also touches on how it can be used with LLMs to open new possibilities. 

## 3. Key Concepts
- **Vector Databases->** are the type of databases that store data as high-dimensional vectors, which are mathematical representations of features or attributes.
- **Sharding->:** is a technique that distributes databases across multiple machines or clusters called shards.
- **Partitioning->** is a technique that divides a database into smaller, and more manageable pieces based on some criteria, such as geographic location, category, or frequency. 
- **Replication->** is a technique that creates multiple copies of the vector data and stores them on different nodes or clusters.
- **Nearest Neighbour Search->** is an optimization problem of finding the point in a given set that is closest to the given point.
- **Approximate Nearest Neighbour Search->** improves over Exact Nearest Neighbor Search by reducing memory footprint and search time through the comparison of binary codes instead of original vectors.
- **Large Language Models->** are advanced artificial intelligence systems designed to process and generate human-like text based on vast amounts of data.
- **Retrival Based LLM->** is language model which retrives from external datastore. This enhances their ability to provide contextually relevant responses or information based on the input query or context.

## 4. Learnings

### Nearest Neighbour Search (NNN)
From this paper, I was introduced to this problem. I was familiar with basic search algorithms like linear search and binary search, but I realized how inefficient they would be for searching datasets with a very large number of data points, in the billions. There were several ways in which this problem could be solved, each with its own trade-offs. This paper discussed different algorithms in detail.

### Approximate Nearest Neighbour Search (ANNN)
Although Exact Nearest Neighbor Search (NNN) can solve the problem, it comes at the cost of a higher memory footprint and even higher search times. To improve upon this, Approximate Nearest Neighbor Search (ANNS) algorithms were introduced. This paper discusses various approaches to solving the ANNS problem, such as tree-based, graph-based, hashing-based, and quantization-based methods, providing deeper insights into these algorithms.

### Combining LLMs with Vector Database
Although vector databases (vector DBs) and large language models (LLMs) are individually powerful tools, combining them opens the door to a whole new level of possibilities. LLMs can leverage the storage capabilities provided by vector databases to deliver more efficient responses. Additionally, using LLMs on top of vector databases can enhance search efficiency by adding context to queries, thereby optimizing the performance of vector DBs. Numerous possibilities arise from this combination that can be further explored.

## 5. Conclusion
Research paper gave really great insight on vector databases, underlying algorithms for NNN problem. I would highly suggest this paper to someone who want to start in this field. This paper might open new doors for you. Additionally this paper also leaves you with a interesting topic to research about i.e. Retrieval-Based LLM. I would definetly continue reading about this further. Hoping you will too. 

## 6. Paper link 
[A Comprehensive Survey on Vector Database: Storage and Retrieval Technique, Challenge](../PDF/A%20Comprehensive%20Survey%20on%20Vector%20Database_%20Storage%20and%20Retrieval%20Technique,%20Challenge.pdf)
