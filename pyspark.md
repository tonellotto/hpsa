# PySpark Notes

## Installation

**Note: these steps are not necessary on the remote machines you already use.**

If not installed, run the following commands to download Spark on you machine (local or remote):

```bash
cd $HOME
wget http://apache.panu.it/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz
tar zxvf spark-2.4.1-bin-hadoop2.7.tgz
mv spark-2.4.1-bin-hadoop2.7 spark
rm spark-2.4.1-bin-hadoop2.7.tgz
```

These commands will download the binary distribution of Spark 2.4.1 in your home folder, will uncompress the distribution, move it in the `spark` subfolder in you home folder, and delete the downloaded and compressed binary distribution.

## Configuration

**Note: these steps are not necessary on the remote machines you already use.**

In order to use Spark correctly, add the following rows at the end of the `$HOME/.bashrc` file, using the command `nano ~/.bashrc`.

```bash
# Set SPARK_HOME
export SPARK_HOME=$HOME/spark
# Set default pyspark environment
# export PYSPARK_SUBMIT_ARGS="--master local[2]"
# Set default pyspark interpreter
declare -x PYSPARK_DRIVER_PYTHON="ipython"
# Add Spark lib to python path if you want to use it from standard python (in this case you need to create the Spa
export PYTHONPATH="$PYTHONPATH:$SPARK_HOME/python/:$SPARK_HOME/python/lib/py4j-0.10.4-src.zip"
# Add Spark bin directory to PATH
export PATH="$PATH:$SPARK_HOME/bin"
```

Press Ctrl+O and press enter, followed by Ctrl+X to exit the editor and save the file.

Close the terminal and open it again, or run the following command `. ~/.bashrc` to apply the previous settings to your current terminal.

## Usage

### Connection to the server

Connect to the remote server using the terminal on your local laptop:

```bash
ssh <student-id>@<host-id>
```

### Your first application

First of all, launch the pyspark interpreter shell on the remote machine using the terminal command:

```bash
pyspark
```

Then, when the interactive interpreter is fully loaded, copy (Ctrl+C) and paste (Ctrl+V) the following code in the pyspark shell, and then press enter.

```python
import numpy as np
# define a reduce function that returns the sum of its two arguments.
# This function will be used the reduce operation.
def reduce_sum(left, right):
    return left+right
# initialize a list of 100000 random points with a normal distribution of mean 0 and std_dev 2
data = np.random.normal(0, 2, 100000)
# parallelize the collection loading it into spark, thus creating an RDD
parallel_data = sc.parallelize(data)
# compute the average summing all the elements and dividing this value by the number of elements inside the collec
average = parallel_data.reduce(reduce_sum) / parallel_data.count()
# create a new rdd containing the squared difference of each element of the collection with respect to the average
parallel_squared_diffs = parallel_data.map(lambda v: (v - average) ** 2)
# sum up all squared differences, divide this value by the number of elements and, lastly, perform the square root
std_dev = (parallel_squared_diffs.reduce(reduce_sum) / parallel_squared_diffs.count()) ** 0.5
print(std_dev)
```

This code compute the standard deviation of a collection of 100.000 elements having a normal distribution. The final result should be a number very close to 2.

### Boot errors?

Errors can happen during the boot of pyspark, for instance because the last time an execution has been stopped suddenly.
In order to launch pyspark, it is necessary to delete some temporary files it created.
You can do this removing the file `derby.log` and the folder `metastore_db`. Assuming the pyspark shell was started in your home folder, the commands to perform these actions are:

```bash
rm $HOME/derby.log
rm -r $HOME/metastore_db
```
### Launching a PySpark application from a script

If you want to use Spark from a Python script, instead of using the interactive python interpreter, it is mandatory to insert the following code at the beginning of your `<script-name>.py` script:

```python
# import spark
from pyspark import SparkContext
# initialize a new Spark Context to use for the execution of the script
sc = SparkContext(appName="MY-APP-NAME", master="local[*]")
# prevent useless logging messages
sc.setLogLevel("ERROR")
```

Now you can launch your script with

```bash
spark-submit <script-name>.py
```

or

```bash
python3 <script-name>.py
```
