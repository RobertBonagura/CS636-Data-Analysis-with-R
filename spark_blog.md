# Cloud Computing on Spark

Spark is a fast and general engine for large scale data processing.

You can interact with Spark with Java, Scala, Pythonm and as this article will demonstrate, with R.

Spark is a fast, expressive cluster computing system sompatibble with Apache Hadoop, and works with any Hadoop-supported storage system.

It improves efficiency throught In-memory computing primitives and general computation graphs.

It also imporoves usability though Rich APIs in the languages metnioned above, as well as wtih an itneracive shell.

## Key Ideas behind Spark

Utilizes functional programming. IT allows you to ship the data subset and function objects to each node 

RDDs

Allows you to perform operations across distributed datasets.
- There are two operations in MapReduce: map and reduce.

The map operation provides an arbitrary way to transform each dataset into a new dataset.

The reduce operation combined two datasets.

nboth oerations require custom computer code, but the MapReduce framework takes care of automatically executing them across many computers at once.

## Software Cloud Architecture

Spark runs as a library in your program. (one instance per app)

Runs tasks locally or on a cluster

Accesses storage vua Hadoop InputFormat API

## Using spark with R

sparklyr is an R interface to Apoache R that I am going to use in this article, which uses the dplyr package as ites backend.

sparkly allows you to filter and aggregate Spark datasets and then bring them into R for analysis and visualization.

It uses Spark's distributed machine learning library from R

Create extensions to call Spark API and provide interfaces to SPark packages.

First step: SparkContext

Creating RDDS

Allows you to use dplyr functions on remote data, as well as data I/O operations

## Graph Analytics in R with Spark
Building a basic graph with Spark and graphframe



sources: 
https://therinspark.com/intro.html#intro-background