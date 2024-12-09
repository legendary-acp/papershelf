---
layout: post
title: "MapReduce: Simplified Data Processing on Large Clusters"
date: 2024-12-15
tags: [engineering-systems, big-data]
---

MapReduce has 2 main components, Map that converts given set of input data into (key,value) pairs using user define function and a Reduce function that merge (keys, [values]). Although this might sound simple program but handles many complex tasks assosicated with this hiding them from end user and letting him focus on core logic. It can handle PB's of data and hide details like parallelization, fault-tolerance, data distribution and load balancing. 

The system runs on cluster of 100s of machine and can be easily configured using mapreduce specification object. Some example usage of this include:
- Reverse weblink graph -> map - outputs (target, source) | reduce - output (target, [source])
- Count URL access frequency -> map - output (url, 1) | reduce - output (url, total_count)
- Distributed Grep -> map - output (word, line) | reduce - identity function
- Inverted Index -> map - output (word, documentID) | reduce - output (word, [documentID])

    [Download PDF](/papershelf/assets/papers/marvels/mapreduce_simplified_data_processing_on_large_clusters.pdf)