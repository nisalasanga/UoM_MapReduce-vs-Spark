# MapReduce vs Spark
MapReduce and Spark are two popular technologies used for processing and analyzing large data sets. Both technologies are designed for distributed processing of large data sets. Here we are interested in comparing these Two technologies with fast processing and ease of use.

# MapReduce
The MapReduce is a model consists of several steps that are executed in sequence to process and generate large datasets in a parallel and distributed manner.
The MapReduce process is typically executed in a distributed computing environment, where multiple machines work together to process the input dataset. The framework manages the distribution of the input data, the execution of map and reduce tasks, and the communication between nodes in the cluster.

<p align="center">
  <img src="https://github.com/nisalasanga/UoM_MapReduce-vs-Spark/blob/main/Other/The-Architecture-of-MapReduce.jpg" width="720" height="400">
</p>

As shown in the above figure mapreduce contain 5 steps.

##### Input Splitting: 
The input dataset is divided into smaller chunks, called input splits. Each input split is processed independently by a map task.

##### Mapping: 
Each input split is processed by a map task, which applies a user-defined map function to each record in the input split. The map function transforms the input record into intermediate key-value pairs.

##### Shuffling and Sorting: 
The intermediate key-value pairs generated by the map function are shuffled and sorted based on their keys. The shuffle and sort process groups all the intermediate key-value pairs with the same key and sends them to the same reducer task.

##### Reducing: 
The reducer task processes each group of intermediate key-value pairs with the same key. The reducer applies a user-defined reduce function to the values associated with each key, which generates the final output values.

##### Output: 
The final output values generated by the reducer task are written to the output file or storage system.

# Apache Spark 
Apache Spark is an open-source distributed computing system that is designed to process large amounts of data in parallel across multiple nodes in a cluster. 
Spark provides a unified framework for processing and analyzing data from a variety of sources, including batch processing, streaming data, machine learning, and graph processing. It achieves high performance by keeping data in memory and optimizing data processing across distributed computing nodes.

Spark includes a variety of components, including:



<p align="center">
  <img src="https://github.com/nisalasanga/UoM_MapReduce-vs-Spark/blob/main/Other/5fa7ecda6639f6566345729b_Apache%20Spark%20Ecosystem%20PNG-p-1080.png" width="720" height="400">
</p>

##### Spark Core: 
The basic building block of the Spark platform, which provides the distributed task scheduling and data distribution functionality that underlies all Spark applications.

##### Spark SQL: 
A module that provides a programming interface for working with structured and semi-structured data using SQL queries and data frames.

##### Spark Streaming: 
A module for processing live data streams in real time.

##### MLlib: 
A library of machine learning algorithms for classification, regression, clustering, and collaborative filtering.

##### GraphX: 
A library for graph processing and analysis.

Also, Spark can be used with a variety of programming languages, including Java, Scala, Python, and R. It can run on a variety of cluster managers, including Hadoop YARN, Apache Mesos, and Kubernetes.

# Loading, Processing and Quering data using MapReduce And Spark

## Dataset

The below dataset, contain up to 1.936.758 different internal flights in the US for 2008 and their causes for delay, diversion and cancellation; if any.
https://www.kaggle.com/code/adveros/flight-delay-eda-exploratory-data-analysis/notebook 

However we have used a sample of this dataset for the analysis.

## Analysis
To store the data we used Amazon s3 and for the Analysis, We used a Amazon Emr cluster.

In the cluster configuration we have used hive and spark both for fair evaluation (same resourses). 
Also, In the Hadware configuration section we used one master and two core nodes with both having m4.xlarge.

Then enabled the SSH conection using putty (Note that make sure to edit inbound rules in the security groups) and connected to EMR terminal.

For the Mapreduce we used hive and for spark we used pyspark.
Please find attached codes in the respective folders in this repository.

To connect to hive using Amazon Emr just type 'hive' and to connect spark type 'pyspark' in the EMR terminal.

* In this analysis we ran queries for follwing questions.

  1. Year wise carrier delay from 2003-2010 
  2. Year wise NAS delay from 2003-2010 
  3. Year wise Weather delay from 2003-2010 
  4. Year wise late aircraft delay from 2003-2010 
  5. Year wise security delay from 2003-2010 
  
* Ran queries using Hive and pySpark for 5 times and plot a graph in comparing both methods (running time vs iteration) 

* processed all queries and plot the time-comparison graphs 

* Calculated average time taken by MapReduce and Spark for each query and plot the graph 



## Results

<p align="center">
  <img src="https://github.com/nisalasanga/UoM_MapReduce-vs-Spark/blob/main/Other/Picture1.png" width="720" height="400">
</p>

<p align="center">
  <img src="https://github.com/nisalasanga/UoM_MapReduce-vs-Spark/blob/main/Other/Picture2.png" width="720" height="400">
</p>

<p align="center">
  <img src="https://github.com/nisalasanga/UoM_MapReduce-vs-Spark/blob/main/Other/Picture3.png" width="720" height="400">
</p>

<p align="center">
  <img src="https://github.com/nisalasanga/UoM_MapReduce-vs-Spark/blob/main/Other/Picture4.png" width="720" height="400">
</p>

<p align="center">
  <img src="https://github.com/nisalasanga/UoM_MapReduce-vs-Spark/blob/main/Other/Picture5.png" width="720" height="400">
</p>



Comparison for all the queries with sample data for an iteration

<p align="center">
  <img src="https://github.com/nisalasanga/UoM_MapReduce-vs-Spark/blob/main/Other/Picture6.png" width="720" height="300">
</p>

<p align="center">
  <img src="https://github.com/nisalasanga/UoM_MapReduce-vs-Spark/blob/main/Other/Picture7.png" width="720" height="400">
</p>

# Conclusion

### Ease of use
MapReduce is a batch processing system that requires developers to write code in Java to process data. It requires developers to have a good understanding of distributed systems and programming in Java. It also requires setting up and maintaining a Hadoop cluster, which can be complex and time-consuming.

Spark provides a more user-friendly and flexible programming model, with support for several programming languages including Java, Python, and Scala. It offers a higher-level API. It also includes a built-in cluster manager that simplifies the process of setting up and maintaining a Spark cluster.

Overall, Spark is generally considered to be easier to use than MapReduce, especially for developers who are familiar with programming in languages such as Python or Scala. However, both tools require some level of technical expertise and experience with distributed systems to use effectively.

### Fast Process

From the above analysis we can conclude that Spark is generally faster than MapReduce due to its in-memory computing, DAG execution, caching, and RDDs. However, the performance also depends on the specific use case and the size of the dataset being processed.

# References

Figure 1: https://intellipaat.com/blog/wp-content/uploads/2016/11/The-Architecture-of-MapReduce.jpg

Figure 2: https://www.datamechanics.co/apache-spark




  

