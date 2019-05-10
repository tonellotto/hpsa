# High Performance & Scalable Analytics (A.A. 2018/2019)

Web site of the course "High Performance & Scalable Analytics", 2nd level master degree in "Big Data Analytics & Social Mining" of the University of Pisa.

* Responsible: [Nicola Tonellotto](http://pomino.isti.cnr.it/~khast)
* TA: Roberto Trani
* Hours: 20
* Period: from 17/04/2019 to 16/05/2019
* Language: english
* Email: nicola [dot] tonellotto [at] isti [dot] cnr [dot] it, roberto [dot] trani [at] isti [dot] cnr [dot] it

## Exam

The final exam is composed of a software project ([described here](./projects.md)) and a written examination test.

## Notes

* [Here](./pyspark.md) you can find some quick and dirty notes to install [Spark 2.4.1](https://spark.apache.org/docs/2.4.1/) on your laptop or local machine (*nix only).
* [Here](./exercises/ssh.md) you can find some warmup exercises on SSH and SCP.
* [Here](./exercises/hdfs.md) you can find some notes and quick exercises on HDFS.

## Lectures

|Date|Time|Topics|Slide|
|:--:|:----:|---------|:---:|
|17/04|9-13|Introduction, administrative stuff, projects discussion. Parallel and distributed computing concepts: Flynn taxonomy, shared memory and distributed message passing. Big data processing: problems with code and data. Map Reduce: design ideas, typical applications, basic model, wordcount example, image example. SSH and SCP crash course and exercises. |[PDF](./slides/lezione1.pdf)|
|19/04|9-13| Hadoop Distributed File system, namenodes, datanodes, architecture. Exercises. Spark introduction: architecture, applications, driver, executors, context. Resilient Distributed Datasets: introduction, creation, transformation, actions. Spark actions (all). Spark transformations: distinct, filter, sample, map. |[PDF](./slides/lezione2.pdf)|
|02/05|9-13| Spark transformations: flatMap, sortBy, union, intersection, keyBy, lookup, reduceByKey, sortByKey, join and cartesian. Exercises: word count and bigram count. Data Analytics Process. Machine Learning and Spark: MLLib, Vectors, LabeledPoints, Models data types.|[PDF](./slides/lezione3.pdf)|
|04/05|9-13| MLLib: basic statistics. TF-IDF, scaler, normalizer. Train, validation and test sets. KMeans, linear regression, logistic regression, decision trees and random forests. |[PDF](./slides/lezione4.pdf)|
|09/05|9-13| Project Walkthrough |[MD](./slides/lezione5.md) [Notebook](./solutions/Project%20Walkthrough.ipynb)|

