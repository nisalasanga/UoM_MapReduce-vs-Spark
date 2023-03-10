# MapReduce vs Spark
MapReduce and Spark are two popular technologies used for processing and analyzing large data sets. Both MapReduce and Spark are designed for distributed processing of large data sets. Here we are interested in comparing these Two technologies with run time and ease of use.

# MapReduce
The MapReduce is a model consists of several steps that are executed in sequence to process and generate large datasets in a parallel and distributed manner.
The MapReduce process is typically executed in a distributed computing environment, where multiple machines work together to process the input dataset. The framework manages the distribution of the input data, the execution of map and reduce tasks, and the communication between nodes in the cluster.

<img src="https://github.com/nisalasanga/UoM_MapReduce-vs-Spark/blob/main/Other/The-Architecture-of-MapReduce.jpg" width="720" height="400">

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

<img src="https://github.com/nisalasanga/UoM_MapReduce-vs-Spark/blob/main/Other/The-Architecture-of-MapReduce.jpg" width="720" height="400">

##### Spark Core: 
The basic building block of the Spark platform, which provides the distributed task scheduling and data distribution functionality that underlies all Spark applications.

##### Spark SQL: 
a module that provides a programming interface for working with structured and semi-structured data using SQL queries and data frames.

##### Spark Streaming: 
a module for processing live data streams in real time.

##### MLlib: 
A library of machine learning algorithms for classification, regression, clustering, and collaborative filtering.

##### GraphX: 
A library for graph processing and analysis.

Also, Spark can be used with a variety of programming languages, including Java, Scala, Python, and R. It can run on a variety of cluster managers, including Hadoop YARN, Apache Mesos, and Kubernetes.

# Loading, Processing and Quering data using MapReduce And Spark

## Dataset

The below provided dataset, contain up to 1.936.758 different internal flights in the US for 2008 and their causes for delay, diversion and cancellation; if any.

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

![image](https://user-images.githubusercontent.com/63199917/224236792-2da158c9-6c1b-434c-93d7-ea2b42589df7.png)
![image](https://user-images.githubusercontent.com/63199917/224236805-3a3b3dd3-8b33-46ff-8e04-47f2273c77df.png)
![image](https://user-images.githubusercontent.com/63199917/224236824-c198b003-e0d9-4f61-b4b8-89e6ca1c40e0.png)
![image](https://user-images.githubusercontent.com/63199917/224236849-f3528432-3846-49d7-9d25-ddfc23a1b9e8.png)
![image](https://user-images.githubusercontent.com/63199917/224236877-a721d138-bf19-4a9d-aa55-99531ad09869.png)


Comparison for all the queries with sample data for an iteration
![image](https://user-images.githubusercontent.com/63199917/224237034-606d1ed7-7c5f-445f-b849-166ff45a2250.png)

![image](https://user-images.githubusercontent.com/63199917/224237125-06efbef7-6939-4c4b-a2f2-3040bfbd1bba.png)

# Conclusion


# References

Figure 1: https://intellipaat.com/blog/wp-content/uploads/2016/11/The-Architecture-of-MapReduce.jpg

Figure 2: https://www.datamechanics.co/apache-spark




  

