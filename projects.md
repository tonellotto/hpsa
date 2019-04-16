# HPSA projects description

The project consists of applying the concepts and tools learned during the course on real use-cases.
The project involves employing a data mining pipeline on real data in a distributed environment.
Six projects are available, although the students can propose (and discuss) new projects to the tutor before May, 4th.

## Rules

The students must work in groups of at most six people and each group must work on a different project.
The groups must be communicated to the tutor before May, 4th.

The students must sent the following files via e-mail (CC to roberto.trani@isti.cnr.it) before 12:00 CET of May, 14th:
- a final report of at most two pages (font-size of at least 11pt and regular margins). The report should contain the following parts: *i*) a brief introduction to the task and the objective; *ii*) a data understanding step and a data preparation step; *iii*) a feature extraction step followed by a modeling step; *iv*) a validation/evaluation step.
- either a script or a jupyter notebook containing the (well commented) source code runnable on the cluster of the course. The raw input files must be placed in our HDFS and the provided code must read them from the HDFS.

## Projects
### 1. Spam classification of SMS
**Objective**: build a SMS spam detection model predicting if a given SMS is spam or not.

**Dataset**:
[https://www.kaggle.com/uciml/sms-spam-collection-dataset](https://www.kaggle.com/uciml/sms-spam-collection-dataset)

### 2. Sentiment analysis of movie reviews
**Objective**: build a sentiment-analysis model of movie reviews predicting if a given review is negative or positive.

**Dataset**:
[https://www.kaggle.com/c/sentiment-analysis-on-movie-reviews/data](https://www.kaggle.com/c/sentiment-analysis-on-movie-reviews/data).
The given dataset (train.tsv) contains 5 classes, discard the neutral class and transform the remaining 4 classes into positives and negatives.

### 3. Identification of beer categories
**Objective**: build a beer classification model predicting if a beer is an *"American IPA"* or not based on its properties.

**Dataset**:
[https://www.kaggle.com/jtrofe/beer-recipes](https://www.kaggle.com/jtrofe/beer-recipes)

### 4. Stock prediction using news
**Objective**: build a stock prediction model predicting if a given stock goes up or down by incorporating news data.

**Dataset**:
[https://www.kaggle.com/aaron7sun/stocknews](https://www.kaggle.com/aaron7sun/stocknews)

### 5. Customer segmentation of bank customers
**Objective**: segment the bank customers based on their credit card usage behaviour to define new marketing strategies.

**Dataset**:
[https://www.kaggle.com/arjunbhasin2013/ccdata](https://www.kaggle.com/arjunbhasin2013/ccdata)

### 6. Customer segmentation of e-commerce customers
**Objective**: segment the e-commerce customers based on their transactions to define new marketing strategies.

**Dataset**:
[https://www.kaggle.com/carrie1/ecommerce-data](https://www.kaggle.com/carrie1/ecommerce-data)
