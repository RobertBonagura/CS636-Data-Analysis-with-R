# Cloud Computing on Spark

Spark is a fast and general engine for large scale data processing.

You can interact with Spark with Java, Scala, Pythonm and as this article will demonstrate, with R.

Spark is a fast, expressive cluster computing system compatibble with Apache Hadoop, and works with any Hadoop-supported storage system.

## Key Ideas behind Spark

It was designed as an improvement on MapReduce, providing a richer set of verbs to optimizing running code on multiple machines. Loads data both on disc and on-memory which is faster than MapReduces/s on-disc storage methods.
- Improves efficiency: up to 100x faster than Hadoop's MapReduce
- Improves usabliity: Rich APIs in java, python, scala and R, often 2-10x less code 

It is a good fit for tackling problems that can not be done on a single machine - both big data problems and big compute.

RDDs , resilient distibuted datasets - are spread acorss multipoel clusters, abstracting the  complexity of distributed compute
- Arent limited to only Map and Reduce operations, joins and filters are abvailable as well

## Software Cloud Architecture

Spark runs as a library in your program. (one instance per app)

Runs tasks locally or on a cluster

Accesses storage vua Hadoop InputFormat API

## Using spark with R

sparklyr is an R interface to Apoache R that I am going to use in this article, which uses the dplyr package as ites backend.

sparklyr allows you to filter and aggregate Spark datasets and then bring them into R for analysis and visualization.

https://therinspark.com/starting.html

Refer to above link for getting started with sparklyr

## Graph Analytics in R with Spark
Building a basic graph with Spark and graphframe

https://therinspark.com/extensions.html#graphs