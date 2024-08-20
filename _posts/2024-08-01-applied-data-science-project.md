---
layout: post
author: Kok Jian
title: "Applied Data Science Project Documentation"
categories: ITD214
---
# The Use of Machine Learning to Track Audience Preferences and Guide the Development of a Good Movie/Show

## Project Background
Investing in the production of movies and television shows demands substantial capital investment and extensive manpower coordination. However, the reality is that not all projects achieve commercial success or profitability. 

Our team hope to leverage machine learning techniques to discern audience preferences and trends. If successful, we can mitigate the risks of production failures. With the wealth of information now available, we aim to showcase how data-driven decisions that align closely with consumer preferences can be made, and subsequently maximise the potential for success.

### Business Goal
To be able to sustainably identify popular topics among audiences and predict the success of prospective films. 

### Business Objectives
1. Train a text classification model to predict the sentiment of a movie review, to automate the labelling of the sentiment for new movie reviews on IMDB.
2. Perform topic modelling on the movie reviews to uncover insights on the topics prevalent in positive reviews and likewise for negative reviews.
3. Train a binary classification model to predict prospective films’ IMDB score and hence its potential popularity level.
4. Train a regression model to predict prospective films’ IMDB votes and hence its potential audience engagement level.

![image](https://github.com/user-attachments/assets/eff8be1a-23ff-481b-9bf3-0a018ec0eee0)

### Success Criteria:
1. To automate the classification of new movie reviews with a 80% accuracy.
2. To identify at least 2 topics that are associated with positive sentiment.
3. Predict for a prospective film, at 60% accuracy rate or a normalised RMSE of 0.2 for its IMDB score and IMDB number of votes.

## Work Accomplished
This repository details the work accomplished for Business Objective #1, i.e. train a text classification model to predict the sentiment of a movie review, to automate the labelling of the sentiment for new movie reviews on IMDB. 

The work accomplished for the other business objectives are detailed in the following sites:

* [Business Objective #2](https://siewlw.github.io/itd214/2024/08/01/applied-data-science-project.html)

* [Business Objective #3](https://xushengchee.github.io/itd214/2024/08/01/applied-data-science-project.html)

* [Business Objective #4](https://jianweigoh.github.io/itd214/2024/08/01/applied-data-science-project.html)

### Data Understanding
We began by collecting data from Stanford University's [Large Movie Review Dataset](https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews), provided in CSV format. This dataset consists of 50,000 movie reviews from IMDb, all of which are complete with no missing data.

![image](https://github.com/user-attachments/assets/a08e296d-a0b4-4755-acbe-39481181a7ad)

### Data Exploration
During the data exploration, we found that although the dataset has an equal distribution of positive and negative sentiment reviews, there were 824 duplicates and only 49,582 unique reviews. 

![image](https://github.com/user-attachments/assets/41fdf856-7168-4986-bf25-c2708563635c)

### Data Cleaning
To ensure data integrity, we removed all duplicated rows. Then, we confirmed that the distribution of positive and negative sentiments remained evenly balanced after cleaning, which is crucial for training an unbiased model.

![image](https://github.com/user-attachments/assets/5601bbe2-b2cd-4fed-96ef-1b8a0522c405) 
![image](https://github.com/user-attachments/assets/dfa95a68-a3ce-40d8-b75a-02ed8600f513)

### Data Preparation and Transformation
In preparing the data, we removed stop words and punctuation, performed lemmatization, and analysed the frequency of the words. 

![image](https://github.com/user-attachments/assets/e5f58ba6-aff5-4799-a89b-ce8b7de2d801)
![image](https://github.com/user-attachments/assets/97c479e3-790c-427b-87ec-22350377acb5)

We found that the word ‘movie’ appeared way more frequently than other words. So, we excluded the word 'movie', as it will not be informative for our analysis.

![image](https://github.com/user-attachments/assets/c33b17da-33ef-4638-9f47-cad7ccb56396)

To facilitate data modelling for business goal #1, we then converted sentiment labels to binary values – positive as 1 and negative as 0.

![image](https://github.com/user-attachments/assets/43808e44-c81f-41d6-afe8-7e570f34b049)

### Data Modelling and Training
Multinominal Naïve Bayes (MNB) is selected for data modelling because it is
*  computationally efficient in handling large datasets;
*  performs well in sparse and high-dimensional data (i.e., large number of text data in movie reviews); and
*  enables additional features to be incorporated to enhance the model performance (i.e., incorporating bi-grams to enhance the model's ability to capture context)


We used 80% of the data for training, and 20% of the data for testing.

![image](https://github.com/user-attachments/assets/ad6fd097-ab21-4c3f-b5a7-85a71f3949e8)

### Model Evaluation
Then, we evaluated the model based on its accuracy, precision and recall values. 

![image](https://github.com/user-attachments/assets/1861c2f9-55bc-4531-b2f7-6b67d24694b4)
![image](https://github.com/user-attachments/assets/63438cd2-3547-416e-bf29-6eb23081bd2d)
![image](https://github.com/user-attachments/assets/7be69512-eddb-469d-a220-5f7a5c36037f)

*  The model achieved an accuracy of 85.27%, surpassing our success criteria of 80%.
*  The model also demonstrated high precision and recall (ranging from 0.84 to 0.86), indicating balanced performance across both positive and negative sentiments, without bias to either sentiment.

### Deploying Model on Unseen Data
To ensure the model's robustness, we deployed it on new movie reviews. 

![image](https://github.com/user-attachments/assets/16f3d47b-3bd3-4ea3-9bed-0f015942f92f)

Shown below are 2 examples of the unseen data. 1 negative review on ‘Catwoman 2004’ and 1 positive review on ‘Inside Out 2’.

![image](https://github.com/user-attachments/assets/05b532f1-7a68-47fb-a380-ee419f8d8066)

The model successfully predicted the sentiment of the 'Catwoman (2004)' review as negative, and the 'Inside Out 2' review as positive. This reinforces our confidence in its ability to predict the sentiments in new movie reviews accurately.

## Recommendation and Analysis
Our efforts have successfully met the business goal of automating the classification of movie reviews with an accuracy that exceeds the 80% target. This achievement not only aids in understanding audience sentiment but also supports our larger objective of predicting the success of future films. 

To further improve the model, we recommend incorporating colloquial language stop words (e.g., Singlish) to enhance the model's effectiveness in specific cultural contexts. We also recommend exploring higher-order n-grams (i.e., tri-grams) and performing hyperparameter tuning. Additionally, experimenting with other deep learning architectures (e.g., LSTM or BERT) that may possibly perform better is recommended. 

## AI Ethics
The dataset used does not contain any personal or confidential information, and the models' failure to accurately predict the success of movies/shows is not expected to cause societal harm. Nonetheless, a human-in-the-loop approach is recommended in view that there could be additional considerations that may not be fully understood and have not been captured by machine learning. Given the significant investment involved in producing movies and shows, it will be prudent to incorporate insights from other sources, and use the model as a tool to support informed decision-making, rather than relying solely on its predictions.

![image](https://github.com/user-attachments/assets/de4042bf-0a2a-4165-bb34-525a3312009b)

## Source Codes and Datasets
[https://github.com/kokjian/itd214_project](https://github.com/kokjian/itd214_project)
