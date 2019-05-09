# IMDB - Sentiment Analysis of movie reviews

**Objective**: build a sentiment-analysis model of movie reviews predicting if a given review is negative or positive.

**Dataset**: [https://www.kaggle.com/iarunava/imdb-movie-reviews-dataset](https://www.kaggle.com/iarunava/imdb-movie-reviews-dataset)

**Small Dataset**: [https://github.com/tonellotto/hpsa/raw/aa1819/data/aclImdb.zip](https://github.com/tonellotto/hpsa/raw/aa1819/data/aclImdb.zip)

In this lecture, we see how to perform sentiment analysis using the IMDB Movie Reviews Dataset. We will classify reviews into positives (label 1) and negetives (label 0). We will encode the data using tf to feed a Logistic Regression Model.

## Steps

- [Download](https://github.com/tonellotto/hpsa/raw/aa1819/data/aclImdb.zip) the small dataset locally
- Load the zip file into the server (`scp`)
- Unzip the file (`unzip`)
- Put the file into the HDFS (`hadoop fs -put`)
- Open a notebook at [https://masterbig-<SERVER_ID>.itc.unipi.it:7777/](https://masterbig-<SERVER_ID>.itc.unipi.it:7777/)

## Steps into the notebook

- Create a spark context using
```
# import spark
from pyspark import SparkContext
# initialize a new Spark Context to use for the execution of the script
sc = SparkContext(appName="MY-APP-NAME", master="local[*]")
# prevent useless logging messages
sc.setLogLevel("ERROR")
```
- Load the files using `sc.wholeTextFiles('hdfs://masterbig-1.itc.unipi.it:54310/user/student<STUDENT_ID>/folder/', use_unicode=True)`
- Compute the number of examples of training and test
- Compute the number of positive/negatives of training and test
- Compute the length distribution (number of words) of the training reviews
- Compute the most frequent words of the training reviews
- Remove the stopwords from the reviews
- Transform the reviews using a `HashingTF()` transformer
- Train a `LogisticRegressionWithLBFGS` model
- Print some of the test reviews and the predicted labels
- Compute the accuracy
