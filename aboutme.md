---
layout: page
title: About me
subtitle: Why you'd want to go on a date with me
---

### Spark Overview
Spark is an open source distributed computing data processing framework. Spark allows for data sharing between processing steps, in contrast to Hadoop's requirement of persisting data to disk at each step. It was started at UC Berkeley in 2009, by Matei Zaharia. Spark was donated to the Apache Software Foundation in 2013 and as of 2015 is one of the most active Apache projects.  

Spark can be used for four styles of data analysis and processing. These are batch, streaming, iterative, and interactive.
* Batch:  
Manipulating large datasets, typically performing map-reduce jobs
* Streaming:  
Processing incoming information in near real-time
* Iterative:  
Used for machine learning algorithms, where data is accessed repetitively
* Interactive:  
Data exploration of large chunks of data  

Spark enables creating complex, multi-stage data processing routines, and provides a high-level API and fault tolerance. It was developed as an alternative to using MapReduce on Hadoop for interactive queries or real-time, low-latency applications. Spark uses a distributed, fault-tolerant, in-memory structure called a Resilient Distributed DataSet (RDD) as an alternative to the persistence of intermediate data to disk between the Map and Reduce processing phases of Hadoop to increase performance.  

Spark is written in Scala and provides support for programming interfaces in Scala, Python, Java, SQL, and R. The tutorial will use Python to demonstrate Spark. Spark can be used through an interactive Shell or through a spark-submit command for a Spark job. The interactive shell is usually used for development and spark-submit is usually used for production.  

Spark is usually used to process data in Hadoop, but can be used with local and network file systems, Object storage like Amazon S3, Relational Databases, NoSQL stores, and messaging systems. Spark interacts with Hadoop through the <em>HDFS</em> (Hadoop Distributed File System) which can be an input source or output target. Hadoop's scheduling subsystem <em>YARN</em> ( Yet Another Resource Negotiator) can schedule resources for Spark.  

Spark operates in three modes: single mode which is standalone on a single machine, distributed on YARN, or distributed on Mesos which is a cluster manager developed with Spark at Berkeley. Spark includes the following libraries:  

* Spark SQL:  
SQL like queries to explore large structured datasets
* Spark Mlib:  
Algorithms and a framework for machine learning
* Spark Streaming:  
Near real-time processing and analysis on streams of data
* Spark GraphX:  
Processing and computation on connected entities and relationships.  

### Hadoop for Spark: HDFS and YARN
#### HDFS  
HDFS is a distributed, fault-tolerant, scalable, high-concurrency supporting, virtual file-system. HDFS maintains an immutability property for data, meaning that data is unable to be updated after it is committed to the filesystem.  

Files consist of blocks which default to 128MB, but are configurable to other sizes. Upon input to HDFS, files are divided into blocks, distrubuted, and replicated. A 400MB file will be divided into 3 blocks of 128MB and a block of 50MB. If a Hadoop cluster contains multiple nodes, blocks are distributed among slave nodes without being shared. Blocks are replicated according to a defined replication factor which is usually set to 3 when there are 3 or more nodes.  

* NameNode:  
The NameNode is the master server that manages file system namespace and regulates access to files by clients. It handles namespace file operations like opening, closing, and renaming files and directors, and determines mapping of blocks to DataNodes.
* DataNodes:  
DataNodes manage storage attached to the nodes that the cluster runs on, serve read and write requests from clients, manage local storage, provide block reports to the NameNode, and perform block creation, deletion, and replication based on instructions from the NameNode.  

#### YARN  
YARN schedules and orchestrates applications, jobs, and tasks in Hadoop.

* NameManagers:  
Worker daemons, processes, or agents that carry out tasks
* tasks:  
An individual unit of work such as a Map task. Each task has at least one task attempt. Tasks can be attempted more than once due to failure, or due to speculative execution. With speculative execution, a task that is running slower relative to other concurrent tasks is started on another NodeManager and the result of the first completed task is used.
* application:  
A complete set of tasks.
* ResourceManager:  
YARN daemon that assigns the ApplicationMaster for an application and keeps track of available resources on the NodeManagers.
* ApplicationsMaster:  
A delegate process for managing the execution and status of an application. It determines required container resources for an application and negotiates for these with the ResourceManager.
* containers:  
Compute and memory resources presented to applications to perform tasks.

### my history

To be honest, I'm having some trouble remembering right now, so why don't you just watch [my movie](http://en.wikipedia.org/wiki/The_Princess_Bride_%28film%29) and it will answer **all** your questions.
