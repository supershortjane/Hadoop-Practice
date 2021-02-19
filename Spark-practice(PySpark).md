## Spark
## Introduction
**Spark** plays similar role like hadoop MapReduce, its driver asks the master for resource in **spark standalone**(similar to Yarn) first,
then master allocates tasks to slaves. **Spark programming models** provide instructions for the slaves to do execution. 
When the program recieve the RDD's transformation methods, which are lazy instrution, it would do nothing until it receives RDD's action method, which trigger real execution. 
Compared to Hadoop MapReduce, Spark run programs much more faster than MapReduce. Also, We could write programming models easily thourgh spark API for python. 

**RDD** is Resilient Distributed Dataset. It is an immutable distributed collection of objects.
There are two main types of RDD operation: Action and Transformation.</br>
Example of RDD Action:</br>
-   saveAsTextFile()
-   saveAsHadoopFile()
-   reduce(f)
-   collect()
-   take()</br>

Example of RDD Transformation:
-   map(f)
-   flatMap(f)
-   reduceByKey(f)
-   groupByKey(f)</br>

In this practice, I run a spark program in spark standalone to calculate word count of the file:"war_and_peace.txt".

## 1.Start HDFS and Spark standalone cluster
start HDFS </br>
<code>cd ~hadoop-2.10.0/sbin/</code>
<code>./start-dfs</code>
start spark standalone </br>
<code>cd ~spark-2.4.5-bin-hadoop2.7/sbin</code>
<code>./start-all.sh</code>
connect to http://devenv:8080 to see if the spark standalone cluster is running.
### Spark standalone
![image](https://user-images.githubusercontent.com/32606310/108331986-45219400-720a-11eb-8320-2de03f66bc39.png)

## 2. Use PySpark to run spark program
Since we run spark program through spark API for python. We start pyspark with the following commands.
<code>pyspark --master spark://devenv:7077</code>
### terminal 
![image](https://user-images.githubusercontent.com/32606310/108333374-d9402b00-720b-11eb-818d-8c4deea6e5b5.png)
### HDFS CLI
![image](https://user-images.githubusercontent.com/32606310/108333480-f248dc00-720b-11eb-9d34-ba68b4d4aaad.png)



