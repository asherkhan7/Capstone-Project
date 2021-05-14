# NLP Analysis of Youtube Tags

Datasets were taken from Kaggle

## Business Case

I will use different machine learning methods to predict how many views a YouTube video will render based on the tags used.

## Datasets

The datasets were taken from Kaggle, entitled "Trending YouTube Video Statistics''. Datasets from the United States, Canada, and Great Britain were joined together to train this model.

## Exploratory Data Analysis

I started cleaning the dataset by removing all rows with no tags and dropping unneeded columns. I then removed outliers by limiting the dataset to a maximum of 1 million views.

I then examined the distribution of the views count through the following histogram: 
![histogram](/figures/views_hist.png)

It's clear from the histogram that the number of videos increase as the number of views decrease, which is expected.

Next I assigned category names to the videos based on the category ID's in the dataset using the json files provided with the data. I then plotted the number of videos in each category:
![bar-graph](/figures/counts_by_category_bg.png)

Based on the analysis, the most number of videos are in the Entertainment category by far, and the remaining categories count descending quite consistently.

I then defined likes, dislike and comment rate based on views by dividing the number of likes, dislikes, and comments by views. I then produced a heatmap comparing the rates of likes and dislikes with comments:
![heat-map](figures/comment_rate_heatmap.png)

Based on the heat map above, there is a 47% chance for a person to comment on a video they liked and a 23% chance to comment on a video they disliked.

I then viewed the 35 most common tags used in videos, the word cloud below shows this analysis:
![word-cloud](/figures/tags_wordcloud.png)

## Modeling

For modeling, I began by defining the tags as the data and views as the target variables. I used two methods for creating a predictive model:

1. Countvectorizer
2. TF-IDF

After I fit transformed the data, I used Random Forest Regression to visualize the results. I then used GridSearch to further optimize my Mean Squared Error.

## Conclusions

Following are the Random Forest results from the two NLP methods. There was not much of a difference in the results of the two methods, CountVectorizer had a slightly better r-squared and about 5,000 views better for the mean squared error. An r-squared of .344 is pretty decent considering a text analysis. I also optimized using GridSearch, however the results didn't improve so I decided to go with the CountVectorizer results. 

### CountVectorization-

Train:
R Squared =  0.344
Mean Sqrd Error =  188782.54

Test:
R Squared =  0.182
Mean Sqrd Error =  212470.83

### TF-IDF-

Train:
R Squared =  0.341
Mean Sqrd Error =  189268.34

Test:
R Squared =  0.173
Mean Sqrd Error =  213632.30

Below is the feature importance for both NLP models:

### CountVectorization-
![bar-graph](/figures/feature_imp_countvec.png)

### TF-IDF-
![bar-graph](/figures/feature_imp_tfidf.png)

## Limitations

Although tags are a factor in affecting views, it is not the only factor or even the primary one. Other factors that affect the number of views are the Youtube channel itself and its popularity, shares, the time the video was posted, etc.

## Recommendations



