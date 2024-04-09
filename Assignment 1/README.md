# Assignment 1

I used ChatGPT 3.5 to help with the solution derivation, and here are the prompts I used:

I have been connecting with the Wolf server and uploaded two pdf files and two txt files into SFTP, so now the four files exist in the Wolf server that also exists in ssh, please now help me:

3. Create a new folder in Hadoop (not in the local filesystem)

4. Move one file that you have just uploaded to Wolf to the new folder in Hadoop

5. Rename this file in Hadoop

6. Copy this file from Hadoop to the local filesystem

7. Create a second folder in Hadoop. Copy two small text files to it. Then extract from Hadoop a single file that is going to be the concatenation of the two files, i.e., appending one file to the other one. (use getmerge)

8. Take a different file on your local filesystem, move it to Hadoop, and then within Hadoop copy the same file to Tucker’s folder (/user/ml057868)


Here are the Linux shell scripts for Tasks 3 - 8 which is almost derived from ChatGPT 3.5's answers:

## Task 3: Create a new folder named **hw1** in Hadoop

```
hdfs dfs -mkdir hw1
```

## Task 4: Move one file that you have just uploaded to Wolf to the new folder in Hadoop

```
hadoop fs -put MLDS_RealTimeAnalysis_1.pdf hw1/
```

## Task 5: Rename this file in Hadoop

```
hdfs dfs -mv hw1/MLDS_RealTimeAnalysis_1.pdf hw1/realtime.pdf
```

## Task 6: Copy this file from Hadoop to the local filesystem

```
hadoop fs -copyToLocal hw1/realtime.pdf /nfs/home/lvf7916/upload
```

## Task 7: Create a second folder in Hadoop named **hw1_2**. Copy two small text files to it. Then extract from Hadoop a single file that is going to be the concatenation of the two files, i.e., appending one file to the other one

```
hdfs dfs -mkdir hw1_2
cd upload_2
hadoop fs -put test_file.txt  text_file.txt hw1_2/
hdfs dfs -getmerge hw1_2/ concatenation.txt
```

## Task 8: Take a different file on your local filesystem (named syllabus.pdf), move it to Hadoop, and then within Hadoop copy the same file to Tucker’s folder

```
hdfs dfs -mkdir hw1_3
hadoop fs -put Syllabus.pdf hw1_3/
hadoop fs -cp /user/lvf7916/hw1_3/Syllabus.pdf /user/mtl8754/Syllabus.pdf
```
