# OpenLab April, 19th

## List of SSH/SCP/HDFS exercises

1. Download the file ```shakespeare.txt``` from [https://github.com/tonellotto/hpsa/tree/aa1819/data](https://github.com/tonellotto/hpsa/tree/aa1819/data) on your local machine with the browser.
2. Copy the file from the local machine to the server with the command ```scp <local_path> <username>@<server_address>:<remote_path>``` (```winscp``` on windows).
3. Connect to the server with the command ```ssh <username>@<server_address>``` (```putty``` on windows).
4. Check if the file is there with the command ```ls <remote_path>```.
5. Copy the file from the server to the HDFS with the command ```hadoop fs -copyFromLocal <remote_path> <hdfs_path>```.
6. Check if the file is there with the command ```hadoop fs -ls <hdfs_path>```.
7. Read the last rows of the file from the HDFS with the command ```hadoop fs -tail <hdfs_path>```.
8. Copy the file back from the HDFS to the server with the command ```hadoop fs -copyToLocal <hdfs_path> <remote_path>```.
9. Copy the file back from the server to the local machine with the command ```scp <username>@<server_address>:<remote_path> <local_path>``` (on your local machine).

## List of PYSPARK exercises part1
1. Compute the square of a list of numbers created with ```np.random.normal(loc=2.0, scale=10.0, size=100)```.
2. Compute mean and variance of a list of numbers created with ```np.random.normal(loc=2.0, scale=10.0, size=100)```.
3. Compute mean and variance of each column of a matrix of numbers created with ```np.random.normal(loc=2.0, scale=10.0, size=(100, 5))```.
4. Compute the average word length of ```shakespeare.txt```. Read it by using ```sc.textFile("shakespeare.txt")```.

---

# OpenLab May, 2nd

## List of PYSPARK exercises part2
1. Compute the word length distribution of ```shakespeare.txt```.
2. Find the most frequent words of ```shakespeare.txt```.
3. Count the number of words of ```shakespeare.txt``` starting with each letter of the alphabet.
4. Find the words pair most co-occurring next to each other of ```shakespeare.txt```.
