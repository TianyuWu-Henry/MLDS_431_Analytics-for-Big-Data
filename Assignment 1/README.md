Here are the Linux shell scripts for Tasks 3 - 8.

Task 3: Create a new folder named **hw1** in Hadoop

```
hdfs dfs -mkdir hw1
```

Task 4: Move one file that you have just uploaded to Wolf to the new folder in Hadoop

```
hadoop fs -put MLDS_RealTimeAnalysis_1.pdf hw1/
```

Task 5: Rename this file in Hadoop

```
hdfs dfs -mv hw1/MLDS_RealTimeAnalysis_1.pdf hw1/realtime.pdf
```

Task 6: Copy this file from Hadoop to the local filesystem

```
hadoop fs -copyToLocal hw1/realtime.pdf /nfs/home/lvf7916/upload
```

Task 7: Create a second folder in Hadoop named **hw1_2**. Copy two small text files to it. Then extract from Hadoop a single file that is going to be the concatenation of the two files, i.e., appending one file to the other one

```
hdfs dfs -mkdir hw1_2
cd upload_2
hadoop fs -put test_file.txt  text_file.txt hw1_2/
hdfs dfs -getmerge hw1_2/ concatenation.txt
```

Task 8: Take a different file on your local filesystem (named syllabus.pdf), move it to Hadoop, and then within Hadoop copy the same file to Tucker’s folder

```
hdfs dfs -mkdir hw1_3
hadoop fs -put Syllabus.pdf hw1_3/
hadoop fs -cp /user/lvf7916/hw1_3/Syllabus.pdf /user/mtl8754
```
