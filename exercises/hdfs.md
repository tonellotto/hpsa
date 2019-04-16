# Working with HDFS from the command line

    hadoop fs -<COMMAND>

Note that all commands are preceded by a `-` char wihtout whitespaces.

### Help

+ `hadoop fs -help [cmd]`: hopefully this is self-describing

### Inspect files

+ `-ls <path>`: list all files in `<path>`
+ `-cat <src>`: print `<src>` on `stdout`
+ `-tail [-f] <file>`: output the last part of the `<file>`
+ `-du <path>`: show `<path>` space utilization

### Create/remove files

+ `-mkdir <path>`: create a directory
+ `-mv <src> <dst>`: move (rename) files
+ `-cp <src> <dst>`: copy files
+ `-rm -r <path>`: remove files and directories (recursively)

### Copy/Put files from a remote machine into the HADOOP cluster

+ `-copyFromLocal <localsrc> <dst>` or `-put <localsrc> ... <dst>`: copy a local file to the HDFS
+ `-copyToLocal <src> <localdst>` or `-get <dst> ... <localsrc>`: copy a file on the HDFS to the local disk

#### Exercises:

1.   Copy from/to HDFS

    ```bash
    hadoop fs -ls /
    hadoop fs -copyFromLocal $HOME/hpsa/data/tragedies.txt tragedies.txt
    hadoop fs -ls
    hadoop fs -cat tragedies.txt
    hadoop fs -put $HOME/hpsa/data/comedies.txt comedies.txt
    hadoop fs -ls
    hadoop fs -cat comedies.txt
    hadoop fs -rm tragedies.txt
    hadoop fs -rm comedies.txt
    ```

2. Create/delete folders

    ```bash
    hadoop fs -mkdir input
    hadoop fs -ls
    hadoop fs -copyFromLocal $HOME/hpsa/data/tragedies.txt input/tragedies.txt
    hadoop fs -rm input
    hadoop fs -ls
    hadoop fs -rm -r input
    hadoop fs -ls
    ```
