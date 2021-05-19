# Phase 4 Project

Final phase down -- you're absolutely crushing it! You've made it all the way through one of the toughest phase of this course. You must have an amazing brain in your head!


# Watching Great Movies and Encovering Similar Movies Employing Recommendation Systems

![mainpic.jpg](images/10-Top-Videos-833x540.jpg)

Author: James Stipanowich

## Project Overview

Watching movies can be a lot of fun. When a person watches a movie they often judge the movie they encounter. Often the person categorizes and scores a movie based on information from previous movies the person has watched. The opinions on movies a person has define what someone watches and might determine what someone chooses to watch in the future. What if specific information is desired about what would be great movies to watch in the future based on a current highly enjoyed movie? How can a computer imitate the human task of identifying highly rated movies based on opinions on movies a person has watched and encover other similar movies for a person to watch in the future? The answer is with recommendation systems. Recommendation systems input movie information from movie lovers into a computer algorithm to provide a movie lover with similar movies to watch based on the current movie opinions and information from a movie lover as well as other related sources. The recommendation systems can often take a person's love for a movie and through an algorithm find other popular, similar movies for that person to watch in the future.


## Business Problem

In this project, I am acting as a data scientist in a research lab at the University of Minnesota to build a recommendation system that recommends highly rated movies to people in the University of Minnesota area based on some past information and opinions on great movies expressed by these people. The project contains both modeling and function built-out methods for getting movie recommendations. I want to use a collaborative filtering user-based method to define movie recommendations for the people in this area. That means that the opinions of the movie raters involved in the experiment may affect the resulting recommendations for the other movie raters in the experiment. I plan to encover 5 new movie recommendations of movies for any person to watch involved in my experiment using my specific recommendation system algorithms for them each individually.

## The Data

This project uses data from the MovieLens dataset from the GroupLens research lab at the University of Minnesota. The MovieLens dataset can be found at https://grouplens.org/datasets/movielens/latest/. The dataset covers 100836 ratings of movies from past viewings of movies. There are 610 individual movie raters in the dataset and 9724 unique rated movies in the dataset.

I decided what data from this dataset to use and how to use it. 

## Data Preparation

In order to look at the spread of ratings in the dataset for my analyses in this project, I created a graph of how many ratings were in my dataset and how the movies were rated within the dataset:

![image.png](images/ratingschart.png)

There were 100836 ratings of movies from past viewings of movies in the dataset. The most common movie rating was a '4' rating. However, I choose to look at the most highly rated movies (a '5' rated movie) when making movie recommendations.

Also, I constructed a graph of the number of rated movies for each unique user in the dataset: 

![userchart](images/userchart.png)

There were explicit ratings in my dataset. The most number of ratings a single user provided was over 2500, which provides a lot of information for assembling recommendations in a user-based manner. Some users only provided a couple of ratings so a filling of missing values occurred in some of my recommedation systems creations to get more similarity information to provide predicted recommendations for some users.

I prepared my data for data modeling or function-built procedures.

## Data Modeling

After trying different models including logistic regression and k nearest neighbors, I chose to stick with a tree based model instead of some other model type. My focus was on getting an accurate model that had a lot of interaction terms. A tree based model seemed best for my evaluations.

I started off with a first decision tree classifier model that was very overfit. I decided to use this model to look at possible parameters for a parameter grid and produce another tree model to help improve model performance. I created graphs of max tree depth, minimum samples splits, and minimum samples for a leaf for my next tree model.

I instantiated a new tree-based model. However, that did not do well with the parameters I put into it. I put that model into random forest and grid search models to help prune my tree models further and come up with best parameters for my final tree-based model that used GridSearchCV.

My final model had very close accuracy scores for training and test data of both around 0.57 with the slightest bit of underfitting. The final model had an AUC of 0.7, which compares the false positive and true positive rates effectively. My final recall score shows the true positive rate is starting to get more weight than the false positive rate in comparison to previous models. The trend in "no-shows" is staring to being identified. The f1 score was best for my final model. I wanted to get fairly balanced precision and recall scores for my model. I would rather believe someone was not going to show up for an appointment and have them show up than believe a person was going to show up for an appointment and have them be a "no-show". Recall represents a minimization of false negatives.

I chose to look at the feature importances for my final tree-based model. Age, SMS_received, and DayDifference seemed to be the columns most influential in the results of the data. I decided to include permutation importance because feature importance does not reshuffle the features to create more balanced results. The directions of the feature importance is not obvious by itself. Permutation importance allows for preserving the distribution of the variable of each predictor that influences model performance. The Age, SMS_received, and DayDifference columns still seemed to be the columns that hold the most weight when analyzing the data.

## Conclusions

- Age should be included in future doctor office analyses. The Age column seemed to exhibit high logistic regression importance, random forest feature importance, and permutation importance as well. The average age of a "no-show" was lower than the average age of a person who attended an appointment.  Older people appear to attend appointments more often than younger people on average. Further analysis might help.

- Book less appointments farther out from the actual appointment day. The average number of days 
away from an appointment for a "no-show" was higher than the average number of days away from an appointment of someone who attended their appointment. Also, the DayDifference column seemed to have high logistic regression importance, random forest feature importance, and permutation importance.

- Remind people more frequently of their appointment whether by phone or text. The DayDifference columns and SMS_received columns showed strong relationships with "no-shows". The DayDifference column and SMS _received columns seemed to have high logistic regression importance, random forest feature importance, and permutation importance. Appointment reminders could help decrease the number of "no-show" appointments and increase memory potential of a scheduled appointment before the appointment takes place. 


## Recommendations for Further Analysis

- Consider gender more in future analyses. Gender had slight logistic regression importance, random forest feature importance, and permutation importance.

- Procure a "no-show" analysis based on neighborhood. Some neighborhoods may have stronger correlations with "no-shows" than others.

## For More Information

See the full analysis of my findings in DoctorsAppointment.ipynb

Contact me at jmstipanowich@gmail.com

## Repository Structure

├── images

├── DoctorNoShowPowerpoint1.pdf

├── DoctorsAppointment.ipynb

├── README.md
