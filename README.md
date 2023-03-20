# Stress-Detection

Creating a Stress Detection Tool using Data From Mental Health Subreddits

## Data
The data I collected came from two sources.  The dreaddit dataset contains comments from Reddit posts across a variety subreddits that have been scored for sentiment analysis.  I added comments from additional subreddits using the Reddit API that all scored positively.
 <br>
![Screenshot 2023-03-08 094616](https://user-images.githubusercontent.com/109488204/223744302-22f453aa-c9c1-43aa-845d-8656c143fbd4.png)
 <br>

## EDA
One of the first things I did in the EDA process was confirm that there was a good balance of 'positive' and 'negative' subreddits represented in the dataset.  With the new data that I combined with the dreaddit dataset, I felt the data was more balanced between positive and negative sources.  <br>
![download](https://user-images.githubusercontent.com/109488204/223739442-698ba7e9-b8f4-436e-b20f-e445f1ed4697.png)

 <br>
I also looked at ngrams during the EDA process.  I divided the dataset between 'positive' and 'negative' sentiment, aka 'stress' and 'no stress' in order to find the most common bigram and trigrams for each classificaton.  Common ngrams for the stressed category included words like 'feel,' 'know,' and 'panic attack.'  Bigrams for the non-stressed category varied a bit more, but surprisingly included a lot of 'dont's.  Trigrams for the non-stressed category were essentially useless - even after adding more specific stopwords, it was exceedingly difficult to filter out all of the reddit/subreddit specific language and bot comments.

## Pre-processing
I created two train/test sets using two different vectorizers. The first vectorizer I used was the Count vectorizer. As its name implies, this vectorizer counts the occurences of each word and the more frequently a word occurs, the more statistically significant it identifies it as. The second vectorizer I used was tf-idf, or term frequency - inverse document frequency. Like the Count vectorizer, tf-idf also counts the frequency of the words, but tf-idf also calculates a value for how significant each word based on additional factors.
 <br>
 
![download](https://user-images.githubusercontent.com/109488204/223743810-bc40aacf-2c8b-45db-b6e3-17bd37d74e10.png)

 <br>
 
 ## Modeling
Overall several of the models had good performance.  The logistic regression and naive bayes models both performed well using count vectors and tf-idf, while the decision trees comparitively underperformed in both cases.  The logistic regression model using tf-idf vectors outperformed all of the other models slightly, so I proceeded with that one, creating a function where the user can input a sentence and the model will score it for stress.  The model performed best when similar keywords were used in inputs to the common bigrams and trigrams found in each category.  In order to improve the model in the future, I would look to improve the dataset.  This would mean using a larger dataset, possibly trying out using more or less subreddit sources.  I also would like to see the dataset be more balanced between categories of stress and no stress, as well as being able to include confidence values and only using data where the confidence of stress or no stress is high.


 <br>
 
![Screenshot 2023-03-08 094551](https://user-images.githubusercontent.com/109488204/223744397-b7af0ef0-0e9a-4ef5-b365-1c91fc39b71c.png)

