Apache Spark is an [[open-source]], distributed computing system that provides a fast and general-purpose cluster-computing framework for [[big data]] processing and analytics.

## Key aspects

1. **Speed**: Spark is designed for speed and can perform in-memory data processing, making it faster than traditional [[big data]] processing tools like [[Apache Hadoop]]. It achieves this through in-memory computation and efficient fault recovery.
2. **Ease of Use**: Spark offers high-level APIs in [[Java]], [[Scala]], [[Python]], and [[R]], making it accessible to a wide range of developers. It also provides built-in libraries for diverse tasks, such as [[SQL]], machine learning (MLlib), graph processing ([[GraphX]]), and stream processing ([[Spark Streaming]]).
3. **Versatility**: Spark can handle various data processing tasks, including batch processing, iterative algorithms, interactive queries, and streaming. Its unified platform makes it easier to integrate diverse processing workloads.
4. **Distributed Computing**: Spark distributes data across a cluster of machines, enabling parallel processing and improved scalability. The core abstraction in Spark is the [[Resilient Distributed Dataset (RDD)]], which allows data to be distributed across nodes in a fault-tolerant manner.
5. **[[Fault Tolerance]]**: Spark achieves fault tolerance through lineage information, which allows it to reconstruct lost data partitions due to node failures. This ensures that Spark jobs can continue execution even in the presence of failures.
6. **Spark SQL**: Spark includes a module for structured data processing called Spark SQL. It allows users to query structured data using [[SQL]], as well as integrate [[SQL]] queries with Spark programs.
7. **Machine Learning with MLlib:** MLlib is a scalable [[machine learning]] library included in Spark. It provides a set of machine learning algorithms for classification, regression, clustering, and collaborative filtering, among others.
8. **Graph Processing with [[GraphX]]**: Spark comes with [[GraphX]], a graph processing library that enables the processing of graph-structured data. This is particularly useful for applications like social network analysis and fraud detection.
9. **[[Spark Streaming]]**: [[Spark Streaming]] allows for real-time processing of data streams. It processes data in small time windows, providing near-real-time analytics capabilities.
10. **Community Support**: Apache Spark has a large and active community, contributing to its development and providing support through forums, mailing lists, and other channels.

### Operations of Apache Spark

1. **Transformations**
    - Transformations are operations that create a new Resilient Distributed Dataset (RDD) from an existing one.
    - They are _lazily evaluated, meaning that they do not compute the results immediately_. Instead, they build up a logical execution plan that Spark will execute when an action is called.
    - Examples of transformations include `map`, `filter`, `flatMap`, `union`, and `groupByKey`.
    - Transformations are the building blocks for defining the sequence of data processing steps.
2. **Actions**
    - Actions are operations that trigger the execution of the logical execution plan and return a value to the driver program or write data to an external storage system.
    - Actions are the operations that initiate the actual computation of data and materialize the results.
    - Examples of actions include `count`, `collect`, `saveAsTextFile`, `reduce`, and `foreach`.
    - Actions are the culmination of a series of transformations, causing Spark to execute the entire computation plan.

## PySpark

PySpark combines Python's learnability and ease of use with the power of Apache Spark to enable processing and analysis of data at any size for everyone familiar with [[Python]].

PySpark supports all of Spark's features such as [[SparkSQL]], DataFrames, Structured Streaming, Machine Learning (MLlib) and Spark Core.

> More is on the [official documentation](https://spark.apache.org/docs/latest/api/python/)

### Usage Example

``` python

# Unless you didn't install PySpark yet, follow the installation guide -> https://gist.github.com/graphy-young/6875146cc34ef6960970f3af40974557

from pyspark.sql import SparkSession

spark = SparkSession.builder.getOrCreate()

# Create Spark DataFrame with collection object
sdf = spark.createDataFrame([
    Row(a=1, b=2., c='string1', d=date(2000, 1, 1), e=datetime(2000, 1, 1, 12, 0)),
    Row(a=2, b=3., c='string2', d=date(2000, 2, 1), e=datetime(2000, 1, 2, 12, 0)),
    Row(a=4, b=5., c='string3', d=date(2000, 3, 1), e=datetime(2000, 1, 3, 12, 0))
])
sdf # returns DataFrame[a: bigint, b: double, c: string, d: date, e: timestamp]

# print DataFrame as text-formatted output
sdf.show() 
# DataFrame.show(n: int = 20, truncate: Union[bool, int] = True, vertical: bool = False)

# Show DataFrame's schema
sdf.printSchema()

```

> [PySpark Code Snippets](https://gist.github.com/graphy-young/6875146cc34ef6960970f3af40974557)
