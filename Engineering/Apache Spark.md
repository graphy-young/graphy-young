In-memory computing framework origin by [[MapReduce]]
It can be simply combined with [[Apache Hadoop Ecosystem]]


- 오픈소스이며, 범용적인 목적을 지닌 **분산 클러스터 컴퓨팅 프레임워크**으로 Fault Tolerance & Data Parallelism을 가지고 클러스터들을 프로그래밍할 수 있게 도와준다.
- RDD, Data Frame, Data Set의 3가지 API를 제공하는데, 이러한 데이터를 바탕으로 **In-memory 연산**을 가능하도록 하여 디스크 기반의 Hadoop에 비해 성능을 약 100배 정도 끌어올렸다.
- Spark는 Cluster들을 관리하는 Cluster Manager와 데이터를 분산 저장하는 Distributed Storage System이 필요하다. 자주 사용되는 Cluster Manager로는 [[Apache Hadoop]]의 [[YARN]]이나 [[Apache Mesos]] 등이 있다. 또한 Distributed Storage System으로는 [[HDFS (Hadoop Distributed File System)]], MapR-FS(MapR File System), [[Apache Cassandra]], [[OpenStack Swift]], [[Amazon Simple Storage Service (S3)]], Kudu, custom solution 등을 적용할 수 있다. 가장 많이 사용되는 Storage System는 Hadoop인데, zlib and Bzip2와 같은 압축 알고리즘을 지원하며, Spark와 같은 머신에서 구동가능하기 때문이다.
### Operations of Apache Spark

- Transformation: Query plan만 생성되며, 실제 메모리에 올리지 않음
	- Narrow Transformation: Partition 간의 데이터의 이동이 일어나지 않음 — `map()`, `flatMap()`, `filter()`, `union()` 등
	- Wide Transformation: Partition 간 데이터 이동 발생 — `groupByKey()`, `aggregate()`, `aggregateByKey()`, `join()`, `repartition()` 등
- Action: Spark는 Lazy Evaluation의 특성을 가지고 있어 Action 시점 전까지 실제 연산을 수행하지 않음. 이는 네트워크 비용을 감소시킴

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
