## Executive Summary

For each subreddit, there are "Flairs" which are the tag of each post in subreddit.

Reddit users can specify flair name when creating new post by selecting from list of provided flair, which is maintained by subreddit moderators. These "Flair" name then used for filtering posts on specific subreddit.

The process of flair selection can cause readers to be confused when it is incorrectly picked. From this problem, we can use classification model to help in tag suggestion, this should reduces the work of moderator and helps users when posting anything on the subreddit.


By using NLP to analyze which flair should the post belongs to on this dataset
|Column|Description|
|---|---|
|title|Title of post on subreddit|
|selftext|Text body of the post|
|tag|"Flair" name (tag name) of subreddit|

Following are flairs to be classfied
* Configuration
* Discussion
* Feature Request
* Guide
* Hot Wasabi
* MEGATHREAD
* Meme / Shitpost
* Meta
* News
* Question
* Tech Support

However, these two flairs will not be included in the model, as another method can be used instead, such as detecting from uploaded file or links 
* Picture
* Video

## Conclusion
After experimenting with various text processing and algorithms, the final model prediction accuracy is about 50% with most errors on "Configuration", "Discussion", "Question" and "Tech Support".

These flairs are difficult to be separated, even with human decision as the posts in these topics are sometimes very similar to each other.
Furthermore, some topics have many posts that are off-topic, for example, "Meme / Shitpost" and "Hot Wasabi" results in quite underperformed model.


To fix this problem, the model will be used to generate top N flairs for the new post instead if it doesn't good enough to pick only one flair.

|Actual|Suggestion|Explanation|
|---|---|---|
|Guide|Meme / Shitpost, News, Guide|Model cannot judge, suggests top 3 possible flairs, one matched|
|Meme / Shitpost|Question, Configuration, Tech Support|Model cannot judge, suggests top 3 possible flairs, no match|
|MEGATHREAD|MEGATHREAD|Model select MEGATHREAD as a predicted result|

Using this approach, percentage of relevant suggestion will go up to almost 80%, which should be enough for the problem.