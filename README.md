# Project_ 3 Webscraping and NLP
___

### Problem Statement
___

Nate Silver and co. at Fivethirtyeight have agreed to hear my pitch for a story. I have chosen to write a piece on how to create a reddit post that will generate the most user engagement from reddit users. This project explores webscraping and language patterns to help determine popular reddit posts. 

### Data Dictionary
___

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**subreddit**|*obj*|backup_data.csv|The title of the subreddit|
|**title**|*obj*|backup_data.csv|Title of post|
|**num_comments**|*int*|backup_data.csv|Total number of comments on post|
|**upvotes**|*int*|backup_data.csv|Total number of upvotes on post|
|**created_at**|*int*|backup_data.csv|Epoch time of post creation|
|**high_low_count**|*int*|backup_data.csv|Binary column of upper and lower 75th percentile|
|**title_length**|*int*|backup_data.csv|Total characters of post|
|**title_word_count**|*int*|backup_data.csv|total count of words in title column|


### Evaluating the data collected 
___
With reddit being a fairly popular site I decided to scrape my data roughly once every twenty four hours. The goal here was to collect around 10,000 posts. While I was expecting to have some duplicates I found that most of the data I collected was duplicated. It turns out the hot section of reddit is not replaced nearly as quickly as I originally predicted. Fortunately a colleague was able to provide some data collected via reddit's api. In the future for collecting the data live I would suggest scraping the data over a longer period. But in the end API's are almost always the easier solution. 


### Summary of Analysis 
___
Fortunately the data set I received was very clean and thus did not require much cleaning beyond removing apostrophes from my subreddit column and titles column to count vectorize them. I decided to count the 75th percentile of 89 as my high commented posts and anything below as my low commented posts. This is represented by the column 'high_low_count' other columns I engineered are 'title_length' and 'word_count'. 
Looking at the distribution of comments both high and low commented posts are skewed to the right. With the higher posts having outliers around 18 and 17 thousand, and the lower posts staying in a tight pattern and cutting off at around 90 comments. Next I wanted to check what subreddit's were receiving the most and least comments. Askreddit appears the most in my top 10 most interacted with posts. This makes sense as it's a broad subreddit that often gets made into youtube videos which gives it an extra layer of exposure.  For my lowest interacted with posts I'm mostly seeing posts revolving around pictures and videos of people or animals. They don't seem to be receiving many comments as there is nothing to respond to. After charting the most popular words I noticed that both my high and low comment posts shared several words with 2 out of the top three words matching.  After establishing my base model which had an accuracy of 0.747  I created four models, one logistic regression and random forest model to check the titles column and another logistic and random forest model to check the subreddit column. All four models scored similarly with the logistic models returning just above the null model at 75 percent accuracy and my Random Forest models returning an overfit 100 percent accuracy. 


### Conclusion and Recommendations
___
To answer our problem statement I would say based off of my EDA we would want to select either AskReddit or memes as our subreddit to launch our post. From there we could use the logistic regression model I created above with the titles column and feed it a data set of potential posts centered around the topic we are wishing to receive our engagement on. In the future to further improve upon this project there are a multitude of angles I would like to explore. We could perform sentinment analysis on the titles column to see if titles with more positive or negative words receive more interaction. We could also engineer more topic centered features such as binary columns for celebrities or pets.  