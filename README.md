# Hadoop-Practice
## HDFS
### Introduction
HDFS consists of a NameNode and a number of DataNodes. Namenode stores the entire metadata, like file creations and file deletions. Datanodes store data and periodically sends a report of all existing blocks to the NameNode.

HDFS User interface allows users easily access the distributed files as they handle files under a single file system. 

In this practice, I use HDFS CLI to handle files and folders.

### 1.Start up the hdfs cluster
start up the hadoop hdfs cluster through following commands in the terminal <br />
<code>cd hadoop-2.10.0/sbin</code>  <br /> 
<code>./start-dfs.sh</code><br />
I am able to connect to http://devenv:50070/ , this means I sucessfully start up the namenode.
#### Terminal
![image](https://user-images.githubusercontent.com/32606310/108300260-fc061b80-71da-11eb-977e-cbc522866728.png)
#### HDFS CLI (devenv:50070)
![image](https://user-images.githubusercontent.com/32606310/108300956-007f0400-71dc-11eb-8265-1358ca2ca54b.png)

### 2.Upload and Download HDFS files
use <code>-put</code> to upload files from local <br /> 
<code>hadoop fs -put ~/Desktop/hadoop101/mr101/avg_temperature /user/practice</code> :means upload avg_temperature(local path) to /user/practice (HDFS CLI's browse directory)<br />
#### Terminal 
![image](https://user-images.githubusercontent.com/32606310/108302218-800dd280-71de-11eb-9c4e-2abffc14d22f.png)
#### HDFS CLI (devenv:50070)
![image](https://user-images.githubusercontent.com/32606310/108302327-b2b7cb00-71de-11eb-9128-491912df0bf0.png)
#### local 
![image](https://user-images.githubusercontent.com/32606310/108302431-eeeb2b80-71de-11eb-8825-9ff1aba2eb6e.png)

use <code>-get</code> to upload files from local <br />
<code>hadoop fs -get /user/practice/data/200701hourly_small.txt ~/Desktop/practice</code> :means download 200701hourly_small(HDFS CLI's browse directory) to /Desktop/practice (local path)<br />
#### Terminal
![image](https://user-images.githubusercontent.com/32606310/108302733-88b2d880-71df-11eb-953e-98aa1456bb65.png)
#### local 
![image](https://user-images.githubusercontent.com/32606310/108302975-ff4fd600-71df-11eb-8a64-96a726f587e9.png)

