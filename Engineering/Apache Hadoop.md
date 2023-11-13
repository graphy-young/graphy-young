An open-source [[framework]] designed for [[distributed storage]] and processing of large data sets using a simple programming model. It is part of the [[Apache Software Foundation]] and is widely used in handling [[big data]] and performing distributed computing tasks

## Key components
---
1. **[[Hadoop Distributed File System (HDFS)]]**
    - HDFS is the primary storage system used by Hadoop. It is designed to store vast amounts of data across multiple machines. Data is distributed across the cluster, providing fault tolerance and high throughput.
2. **[[MapReduce]]**
    - MapReduce is a programming model and processing engine for distributed data processing. It allows developers to write programs that process large amounts of data in parallel across a Hadoop cluster. [[MapReduce]] consists of two phases: the Map phase, where data is processed and transformed, and the Reduce phase, where the processed data is aggregated.
3. **[[YARN (Yet Another Resource Negotiator)]]**
    - YARN is the resource management layer of Hadoop. It allows multiple data processing engines such as [[MapReduce]], [[Apache Spark]], and [[Apache Flink]] to run on the same Hadoop cluster, enabling more flexible and efficient resource utilization.
4. **[[Hadoop Ecosystem]]**
    - Hadoop has a rich ecosystem of tools and projects that extend its capabilities. Some notable components include:
        - **[[Apache Hive]]**: A data warehousing and [[SQL]]-like query language for Hadoop.
        - **[[Apache HBase]]**: A distributed, scalable, and [[NoSQL]] database that runs on top of HDFS.
        - **[[Apache Spark]]**: A fast and general-purpose cluster computing system that can run data processing workloads.
        - **[[Apache Pig]]**: A high-level platform for creating [[MapReduce]] programs.
        - **[[Apache ZooKeeper]]**: A distributed coordination service for managing and synchronizing distributed systems.
5. **scalability**
    - Hadoop is designed to scale horizontally, allowing organizations to add more commodity hardware to their Hadoop clusters as data volumes grow. This makes it suitable for handling large-scale data processing tasks.
6. **[[Fault Tolerance]]**
    - Hadoop provides fault tolerance by replicating data across multiple nodes in the cluster. If a node fails, the data can still be retrieved from other nodes where copies are stored.
7. **Community and Open Source:**
    - Being part of the [[Apache Software Foundation]], Hadoop is developed and maintained by a large community of contributors. It is open source, which means the source code is freely available for modification and redistribution.
Hadoop has played a crucial role in the [[big data]] landscape, providing a cost-effective and scalable solution for organizations to store, process, and analyze vast amounts of data.