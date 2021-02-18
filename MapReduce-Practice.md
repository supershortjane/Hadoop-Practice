## MapReduce
## Introduction

**Yarn** is responsible for cluster resource allocation and works on Master/Slave architecture. 
To run a mapreduce program, driver, a main component of mapreduce program, would ask the master for resource first.
Then the master would allocate the tasks to slaves to execute the program.

**MapReduce program** is a distributed program that process big data analysis on multiple machines.
To write a MapReduce program, the script should follow three phases: mapping, shuffling and reducing.

In this practice, I run mr program in yarn to calculate word count of the file:"war_and_peace.txt".

## 1.start yarn

<code>./start-yarn.sh</code>
connect to https:devenv:8088/cluster to check if yarn sucessfully started.
### terminal
![image](https://user-images.githubusercontent.com/32606310/108317383-236be100-71f9-11eb-9a07-74d97f990261.png)
### Yarn (resource manager)
![image](https://user-images.githubusercontent.com/32606310/108317435-3ed6ec00-71f9-11eb-9f0b-d617047425d1.png)

## 2.upload data to HDFS
<code>hadoop fs -put ~/Desktop/hadoop101/mr101/wordcount/data/war_and_peace.txt /user/practice/data/</code>
### terminal
![image](https://user-images.githubusercontent.com/32606310/108318580-06d0a880-71fb-11eb-84cb-4e558bfc672f.png)
### HDFS CLI
![image](https://user-images.githubusercontent.com/32606310/108318740-47c8bd00-71fb-11eb-8b49-e2f8cde2056c.png)

## 3.Run the MR program
<code>cd /home/spark/IdeaProjects/proj_mr101/out/artifacts/mr101</code> : go the directory which .jar file is placed at</br>
<code>hadoop jar mr101.jar com.iii.mr101.WordCount hdfs://devenv/user/practice/data/war_and_peace.txt hdfs://devenv/user/practice/output</code> : provide the path of the file that just uploaded to HDFS and the path that want to save for the output file in HDFS.
### terminal
![image](https://user-images.githubusercontent.com/32606310/108320326-a2631880-71fd-11eb-9207-1ade3c4ede28.png)
### HDFS CLI
![image](https://user-images.githubusercontent.com/32606310/108320187-6c259900-71fd-11eb-9722-9fe640f38ba9.png)
### Yarn (resource manager)
![108321404-105c0f80-71ff-11eb-93e5-7ebf868a7458](https://user-images.githubusercontent.com/32606310/108321466-2a95ed80-71ff-11eb-83a8-44539357f1d4.png)

## 4.Download the file from HDFS to see the outcome
![108320970-75633580-71fe-11eb-870c-321626496804](https://user-images.githubusercontent.com/32606310/108321095-a6436a80-71fe-11eb-843b-1e3a8c6da392.png)</br>

## 5.Wrong messages when I do the practice
![image](https://user-images.githubusercontent.com/32606310/108317629-878ea500-71f9-11eb-8d19-16408c8ba4d6.png)</br>
solution:The message means that other tasks are using the resource. 
so I run <code>kill 6241</code> and <code>kill 6044</code> to kill the job.

