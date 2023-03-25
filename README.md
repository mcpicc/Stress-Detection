# Stress-Detection

Creating a Stress Detection Tool using Data From Mental Health Subreddits

## Background
Many people under stress turn to the internet to vent, get feedback, and seek support.  One of the places on the internet that people turn to is Reddit due to the subreddits where users can write to each other on seemingly endless topics.  While some of these subreddits might have to do with cars or home organization, there are many subreddits dedicated to different aspects of mental health as well.  Some users want a place to get things off their chest without judgment, some want to ask for advice, while others use their time to post encouraging words or provide support.  What if comments could be flagged if they show signs that the author might be under emotional stress?  Through natural language processing, there is a way.

## Data
The data I collected came from two sources.  The dreaddit dataset contains comments from Reddit posts across a variety subreddits that have been scored for sentiment analysis.  I added comments from additional subreddits using the Reddit API that all scored positively.

 <br>

## EDA
One of the first things I did in the EDA process was confirm that there was a good balance of 'positive' and 'negative' subreddits represented in the dataset.  With the new data that I combined with the dreaddit dataset, I felt the data was more balanced between positive and negative sources.

 <br>
I also looked at ngrams during the EDA process.  I divided the dataset between 'positive' and 'negative' sentiment, aka 'stress' and 'no stress' in order to find the most common bigram and trigrams for each classificaton.  After normalization, many of the bigrams were common among both categories (for example, 'dont know', 'im going', and 'even though'), but the trigrams began to diverge.  While trigrams for the non-stressed category were essentially useless - even after adding more specific stopwords, it was exceedingly difficult to filter out all of the reddit/subreddit specific language and bot comments - trigrams for the stress category were abundant and generally unique from the no stress category (for example, 'feel like im', 'dont even know', and 'dont know anymore').

<br>

## Pre-processing
I created two train/test sets using two different vectorizers. The first vectorizer I used was the Count vectorizer. As its name implies, this vectorizer counts the occurences of each word and the more frequently a word occurs, the more statistically significant it identifies it as. The second vectorizer I used was tf-idf, or term frequency - inverse document frequency. Like the Count vectorizer, tf-idf also counts the frequency of the words, but tf-idf also calculates a value for how significant each word based on additional factors.

 <br>
 
 ## Modeling
Overall several of the models had good performance.  The logistic regression and naive bayes models both performed well using count vectors and tf-idf, while the decision trees comparitively underperformed in both cases.  The logistic regression model using tf-idf vectors outperformed all of the other models slightly, so I proceeded with that one, creating a function where the user can input a sentence and the model will score it for stress.  The model performed best when similar keywords were used in inputs to the common bigrams and trigrams found in each category and/or tf-idf features of higher importance were used.

<br>

In order to improve the model in the future, I would look to improve the dataset.  This would mean using a larger dataset, possibly trying out using more or less subreddit sources.  I also would like to see the dataset be more balanced between categories of stress and no stress, as well as being able to include confidence values and only using data where the confidence of stress or no stress is high.  Features also could be improved, especially on the side of 'no stress'.


 <br>

