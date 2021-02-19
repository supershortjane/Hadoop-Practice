## Spark
## Introduction 
In this practice, I works on a weather dataset to calculate daily average temperature.
Similar to pyspark, I use spark-submit to run my python program this time. 


### command
<pre>#start HDFS
<code>cd hadoop-2.10.0/sbin</code>
<code>./start-dfs.sh</code>  </br>
<code>cd spark-2.4.5-bin-hadoop2.7</code></br>
#start spark
<code>./start-all.sh</code></br>
#go to the location of your python program
<code>cd pythonprojects/proj_spark101</code> </br>
#Before you run the command, replace the path of the data in HDFS as yours.
<code>spark-submit --master spark://devenv:7077 avg_temperature.py</code>  </br>  </pre>
### Terminal
![image](https://user-images.githubusercontent.com/32606310/108470259-a73ecf80-72c4-11eb-810a-b86cc1ed32c6.png)
### outcome 
-   The outcome shows the date and the average temperature.</br>
![image](https://user-images.githubusercontent.com/32606310/108470294-b7ef4580-72c4-11eb-93a2-e1140ef7b546.png)

### RDD's methods in python program:
The following are the snapshot of the outcome at each phases
    <code>sc.textFile("hdfs://devenv/user/practice/data/200701hourly_small.txt")</code>:read the data file from HDFS</br>
   <code>filter(is_good)</code>:return a new RDD that satisfy the function:is_good</br>
![image](https://user-images.githubusercontent.com/32606310/108473115-942dfe80-72c8-11eb-8220-30797d0962d9.png)</br>
   <code>map(lambda x: (x.split(",")[1], int(x.split(",")[10]))</code>: only return two columns: date, temperature</br>
![image](https://user-images.githubusercontent.com/32606310/108473183-aa3bbf00-72c8-11eb-9dc6-1d31f7756464.png)</br>
   <code>mapValues(lambda x: (x, 1))</code>: transform all the RDD's value into (value,1) format so that we could use it to count the number of the date</br>
![image](https://user-images.githubusercontent.com/32606310/108473243-bde72580-72c8-11eb-9d8f-d97527ef8b3e.png)</br>
  <code>reduceByKey(lambda x, y: (x[0] + y[0], x[1] + y[1]))</code>: count the number of the date and sum up all the temeparature by the date</br>
![image](https://user-images.githubusercontent.com/32606310/108473339-dc4d2100-72c8-11eb-9e1b-c090ed930a32.png)</br>
  <code>map(lambda x: (x[0], x[1][0] / x[1][1]))</code>: calculate the average temparature by the date</br>
![image](https://user-images.githubusercontent.com/32606310/108473383-ed962d80-72c8-11eb-990d-9daee670f3f9.png)</br>
