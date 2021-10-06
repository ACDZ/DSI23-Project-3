# ![](https://camo.githubusercontent.com/0eda51f0022b0f98c7050bc3b449b4977d480acf2b8682b086424ccb5361c700/68747470733a2f2f692e696d6775722e636f6d2f5873655855384a2e706e67)

# Project 3 - Web APIs and NLP
---
## Problem Statement
We are a data science team working in GG (a PC building company like AfterShock) and graphics card problems are the number one issue users have. It was shown that most users have graphics card problems after office hours and management had asked the IT team to build a bot to direct customers with graphics card problems to relevant subreddits incase they need help after office hours. The software engineers requested our assistance to help classify keywords for the bot to direct customers to subreddits albeit with accuracy.

And thus, our aim is to build a classifier that identifies keywords for the bot to determine relevant subreddits accurately (90%).

---
## Background
PC building companies like Aftershock PC and GG (our pseudo company) build powerful computers. The company allows users to customize their computers as well as recommend different computer builds. One of the critical components of the computer includes the graphics card, which unfortunately has the highest customer requests and inquiries.

Graphics cards also known as the graphics processing unit is a piece of graphics rendering accelerating hardware used in powerful computers.

There are two types of graphics card used in computers, integrated and discrete.

Discrete graphic cards are preferred for cryptocurrency mining, media development and intense gaming uses.

The graphics card industry is dominated by two main manufacturing companies, namely:
1. **AMD**
2. **NVIDIA**

As we are a PC building company, we provide discrete graphics cards from both companies.

---

## Executive Summary

The following subreddits were scraped using PushShift API from https://api.pushshift.io to scrape the title and selftext from the following subreddits: **AMD and NVIDIA**.

This is a classification problem and it is approached by using **Count Vectorization** and **TF-IDF Vectorization** with 2 classifier models.  

Grid Search CV was utilized to find the optimal hyperparamters for each classifier model.  
The models chosen are :  
    1. **Logistic Regression**  
    2. **Multinomial Naive Bayes**  

The train, test scores and area under curve of the models were used to gauge the classifier performance.

The criteria for selecting the models are the following:

- High Accuracy
- Minimize False Positives (High Sensitivity)
- Good Generalization

High sensitivity is required as we want to direct customers to the correct subreddit and not the wrong ones.

All models provided similar accuracy of 90% and similiar sensitivity of 0.9.

In summary, **multinomial naive bayes** with **Count Vectorization** was picked as the chosen classifier with the least score difference with 0.90 train and 0.89 test as it had the best generalization with the other considerations being the same.

---

## Data Dictionary
#### Dataframes used: unvectorized_gpu.csv


|        Variable Name        |    Data Type   |        Description         |
|:---------------------------:|:--------------:|:--------------------------:|
|         subreddit           |      str       |name of subreddit       |
|         author              |      str       |name of poster of subreddit post|
|         num_comments        |    int         | number of comments per subreddit post|
|         score               |    int         | subreddit upvotes - subreddit downvotes |
|         word_count          |    int         | count of words after lemmatization |
|         content_            |     str        | subreddit post title + subreddit post content lemmatized |

---

# Recommendation and Conclusion

The completion of the classifier is only stage 1 of the entire project.  
The IT team can already start testing their bot with this classifier.  

As the top 5 words include the brand of the graphics cards, it is recommended that the IT Team requests user inputs for the **brand** and **model** of the graphics card as well as a **problem keyword** so that the classifier can assist with more accuracy, and not the user just typing randomly in their problems.

![image](https://drive.google.com/uc?export=view&id=1seSmLZH2Mc_-l9z_a5iW2JRyCGYryk7t)

The wordcloud above shows the top 150 words with the highest coefficients in helping the model classify.

Nevertheless, the model has worked exceptionally well, especially for general data, in classifying which subreddit with specific keywords required.

We recommend that the software engineering team requests for customer ID then match product ID when a customer wants to ask a question so that brands and models are automatically imputed. As customers may now known what is inside and may just want to ask a random question.

We also recommend that the bot forces the customer to search by type of problem first and before allowing them to type their question.

Going forward, in stage 2, the team will work together to identify subreddits and manufacturer forums with keywords and list the links in a dictionary to assist the IT team with direct problem solutions.

This method can also be applied for troubleshooting for other components of the computer such as cpu, motherboard and so on in the future. And hope that the IT Team and work together with us to build a full AI solution for all customer component and troubleshooting inquiries.

W also hope to increase accuracy by trying other models such as SVM and also continue tuning our hyperparameters to try and improve accuracy.
