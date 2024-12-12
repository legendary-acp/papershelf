---
layout: post
title: "MapReduce: Simplified Data Processing on Large Clusters"
date: 2024-12-15
tags: [engineering-systems, big-data]
---

# MapReduce: A Distributed Computing Framework

MapReduce consists of two main components: Map, which converts input data into (key,value) pairs using user-defined functions, and a Reduce function. While this might sound like a simple program, it handles many complex tasks associated with distributed computing, hiding them from the end user and letting them focus on core logic. The system can handle petabytes of data while abstracting details like parallelization, fault-tolerance, data distribution, and load balancing.

## System Overview
The system runs on clusters of hundreds of machines and can be easily configured using a MapReduce specification object. It operates with one master node and several worker nodes, responsible for map or reduce tasks.

## Example Applications
Here are some common use cases of MapReduce:

### Reverse Weblink Graph
- Map: outputs `(target, source)`
- Reduce: outputs `(target, [source])`

### URL Access Frequency
- Map: outputs `(url, 1)`
- Reduce: outputs `(url, total_count)`

### Distributed Grep
- Map: outputs `(word, line)`
- Reduce: identity function

### Inverted Index
- Map: outputs `(word, documentID)`
- Reduce: outputs `(word, [documentID])`

## Implementation Details

### Initial Setup
1. Input data is first split into M pieces, corresponding to M map tasks
2. Each piece of this input makes up one Map task
3. Master node starts assigning these tasks to worker nodes one by one

### Map Phase
4. Worker reads the input, parses key/value pairs from this data, passes them to user-defined map function, gets intermediate keys from this function and buffers them in memory
5. Periodically this buffer is written into local disk as a spill file
6. Data is split into R partitions, each corresponding to a reduce task

### Reduce Phase
7. Location of these pairs are passed back to master node which passes this on to reduce workers
8. Reduce worker uses RPC to read the buffer data from local disk of map workers
9. Once reduce worker reads all data, it sorts these intermediate keys, using external sort if data is too large to fit in memory
10. It iterates over sorted intermediate data, passing each unique key's corresponding set of intermediate values to the reduce function
11. Output is appended to a final output file for this reduce partition
  
## Fault Tolerance

### Worker Failure
Master pings worker periodically, if no response is received from a worker for certain amount of time it is marked as failed. The system handles worker failures in the following ways:
- Map tasks completed or in-progress by failed worker are reset back to idle state
- These tasks become eligible to be rescheduled on other workers
- Reduce tasks that have already read data from failed map task need to re-read it from new worker
- Reduce tasks don't need to be re-executed since output is stored in global file system

### Master Failure
The system handles master node failures through checkpointing:
- Master periodically writes checkpoint of master data structures
- On failure of master node, a new copy can be started from last checkpoint state

## Performance Optimizations

### Task Granularity
The system divides work into configurable pieces:
- Map phase is subdivided into M pieces
- Reduce phase is divided into R pieces
- Master must make O(M+R) scheduling decisions
- Master keeps O(M*R) state in memory

*Note:* R is often constrained by user because the output of each reduce task ends up in a separate output file. M is typically chosen so that individual tasks have roughly 16-64 MB of input data.

### Backup Tasks
The system includes mechanisms to handle stragglers (slow-performing machines):
- A "straggler" is a machine that takes unusually long time to complete one of the last map or reduce tasks
- Stragglers can occur due to various reasons like bad disks or resource competition
- When the program is near completion, master schedules backup execution of remaining in-progress tasks
- Task is marked as complete whenever either primary or backup execution finishes
- This optimization significantly reduces execution time in large MapReduce operations

[Download PDF](/papershelf/assets/papers/marvels/mapreduce_simplified_data_processing_on_large_clusters.pdf)