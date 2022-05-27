# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Web APIs & NLP


### Problem Statement

Our company, twitch, offers a video streaming service that focuses on video games, music, and sports. We have recently created a beta forum where gamers can post comments about games of their interest. We are currently testing this beta forum with selected users. Considering the growing volume of game posts, it is challenging for the marketing and business development team to understand the users and design sales and marketing campaigns that best meet the users' needs, since the posts are not currently organized by games. Additionally, the team indicated that users may lose interest in this brand-new forum if they are unable to find and navigate to the games that interest or are relevant to them, and that we may not be able to launch the feature because of poor user experience.

Thus, the marketing and business development teams have requested that the data scientist team categorize the content according to its respective game. Dota 2 and League of Legends are currently the two most popular games among our users. Our goal is to use Reddit posts from Dota 2 and League of Legends to build a text classifier that has at least 85% accuracy, and to identify the top 5 features of each game. By categorizing the current content for both games, we will make it easy for our users to navigate and enhance their user experience. The top 5 features will give the marketing team some insight into their sales and marketing strategy.

### Executive Summary

Dota 2 and League of Legends are the top 2 popular games posted by our twitch users in the newly created beta forum. To make it easier for our users to navigate the posts that interest or are relevant to them and enhance their user experience, the marketing and business development teams have requested the data scientist team to look into categorizing the game content into its respective game. The goal for this project is to use Reddit comments from Dota 2 and League of Legends to build a text classifier of at least 85% and identify the top 5 features for each game. We will also identify the top 5 features that will help the marketing team review their marketing plan. 

In this project, we will be scraping data using Pushshift for the 2 subreddits, r/DotA2 and r/leagueoflegends (Notebook 1). Data cleaning, text preprocessing (removing URLs / punctuations/stopwords, text tokenizing, and lemmatizing and stemming the text), and visualization of popular words will be done (Notebook 2). For the modeling, we will train and analyze 3 classification models, Multinomial Naive Bayes, Logistic Regression, and K-Nearest Neighbors with different vectorizers (CountVectorizer and TfidfVectorizer) and hyperparameters (Notebook 3). As this is a classification problem, the below 5 evaluation metrics will be used.

- Accuracy Score
- AUC Score
- Precision Score
- Recall Score
- F1 Score

### Data Dictionary

|Feature            |Type    |Description                           |
|-------------------|--------|--------------------------------------|
|**subreddit**      |*object*|DotA2 or League of Legends            |
|**title**          |*object*|The title of the post                 | 
|**selftext**       |*object*|The text in the post                  |
|**text**           |*object*|Combine title and selftext            |
|**text_length**    |*int64* |Length of text                        |
|**subreddit_int**  |*int64* |0 for DotA2 or 1 for League of Legends|
|**cleaned_text**   |*object*|Cleaned text after preprocessing      |
|**text_lem**       |*object*|Text after lemmatizing                |
|**text_stem**      |*object*|Text after stemming                   |
|**word_count_lem** |*int64* |Count of lemmatized text              |
|**word_count_stem**|*int64* |Count of stemmed text                 |
|**text_lem_sen**   |*object*|lemmatized text sentence              |
|**text_stem_sen**  |*object*|stemmed text sentence                 |
 

### Popular Words Analysis

- Words like 'hero', 'major', and 'valve' are observed to be popular in DotA2 posts while words like 'challenge', 'champion', and 'riot' are popular in League of Legends posts.

- The differences in the popular words for lemmatized and stem words are not significant. Lemmatized word is more meaningful as the lemmatizer analyzes the word as a term as compared to stemmed words.

- There are a few differences in the popular words retrieved using CountVectorizer and TfidfVectorizer. This is expected since both vectorizers work differently. CountVectorizer counts the number of word occurrences while TfidfVectorizeris a count vectorizer that includes some consideration for the length of the document, and also how common the word is across other text messages.

- We will adopt using lemmatized text for the modeling as the text is more meaningful as compared to stemmed text.


### Model Analysis

**a) Models Comparison and Findings**
- The model evaluation score is summarized in the table below:

|Model|Optimal Parameter|Train score|Test score|AUC score|Recall score|Precision score|F1 Score
|--|--|--|--|--|--|--|--|
|Multinomial Naive Bayes 1|vec': TfidfVectorizer(max_df=0.9, max_features=5000, min_df=2, ngram_range=(1, 2), stop_words='english')|0.9664|0.8916|0.8917|0.9159|0.8728|0.8939
|Multinomial Naive Bayes 2|{'nb__alpha': 0.5, 'vec': TfidfVectorizer(max_df=0.9, max_features=4000, min_df=3, stop_words='english')}|0.9734|0.8934|0.8935|0.9104|0.8799|0.8949
|Logistic Regression 1|{'vec': TfidfVectorizer(max_df=0.9, max_features=4000, min_df=2, ngram_range=(1, 2))}|0.9746|0.8834|0.8833|0.8592|0.9021|0.8801
|Logistic Regression 2|{'lr__penalty': 'l2', 'vec': TfidfVectorizer(max_df=0.9, max_features=4000, min_df=2, ngram_range=(1, 2))}|0.9746|0.8834|0.8833|0.8592|0.9021|0.8801
|K-Nearest Neighbors 1|{'vec': CountVectorizer(max_df=0.9, max_features=2000, min_df=3, stop_words='english')}|0.6988|0.6375|0.6364|0.3163|0.8782|0.4651
|K-Nearest Neighbors 2|{'knn__n_neighbors': 20, 'knn__weights': 'uniform', 'vec': TfidfVectorizer(max_df=0.9, max_features=5000, min_df=2)}|0.6168|0.6129|0.6115|0.2267|0.9841|0.3685

- The Multinomial Naive Bayes 2 has the best result given that the model is a simple classification algorithm based on the Bayes Theorem which assumes that every word in a sentence is independent of the other ones.

- KNN has the worst performance. KNN model works by finding its nearest neighbor for the words in the posts. As the vocabulary of the words may not be large enough, the model may have its limitation to perform the search effectively.

**b) Misclassification of posts**

- From the top 20 words extracted, the reasons why the posts are classified wrongly are:
    - Overlapping of the keywords for both posts (e.g. ping, champion).
    - Generic words (e.g. seen, view, tried, add) may be used in both posts.

- To reduce the number of misclassification (i.e. improving the accuracy), further analysis of the key and generic words is required. Overlapping of the keywords for both posts should be reduced. We can also consider adding generic words to the stopwords list.

**c) Top 5 feature importance**
- The below table summarizes the top 5 features based on their coefficients. 

|Model                  |Post             |Top 5 Features                        |
|-----------------------|-----------------|--------------------------------------|
|Multinomial Navie Bayes|DotA2            |valve, hero, underlord, stockholm, esl|
|Multinomial Navie Bayes|League of Legends|msi, riot, challenge, champion, token |
|Logistic Regression    |DotA2            |hero, valve, major, ti, steam         |
|Logistic Regression    |League of Legends|riot, champion, msi, challenge, champ |

- Based on the Multinomial Naive Bayes model:
    - Words like valve, hero, underload, Stockholm, and esl are likely to belong to the DotA2 topic.
    - Words like msi, riot, challenge, champion, and token are likely to belong to the League of Legends topic.

- Based on the Logistic Regression model:
    - Words like hero, valve, major, ti, and steam are likely to belong to the DotA2 topic.
    - Words like riot, champion, msi, challenge, and champ are likely to belong to the League of Legends topic.

- The top 5 features for both models have some similarities. So the words obtained are significant features that differentiate the two topics.

### Conclusions

In this analysis, the best model obtained is the Multinomial Naive Bayes classifier with Tfidf Vectorizer. The model has proven to be able to distinguish the words for the two topics with an accuracy of 89.3%. Hyper-tuning the alpha parameter improved the score by 0.14%.
The best model scores are summarized below:
- Accuracy: 89.3%
- Recall: 91.0%
- Precision: 88.0%
- AUC Score: 89.3%
- F1 Score: 89.5%

The reasons for misclassified posts are the overlapping of keywords and generic words used for both posts and generic. To reduce the number of misclassification (i.e. improving the accuracy), further analysis of the key and generic words is required. Overlapping of the keywords for both posts should be reduced. We can also consider adding generic words to the stopwords list.

From our analysis, we have identified the top 5 keywords like `valve`, `hero`, `underload`, `stockholm`, and `esl` for DotA2. League of Legends has keywords `msi`, `riot`, `challenge`, `champion`, and `token`. Post with these keywords means it has a higher possibility that it belongs to that topic. The Marketing team can use these keywords for insights when they brainstorm for their campaigns.


### Limitations

We have yet to analyze the set of words for both posts which resulted in some posts being misclassified. In addition, the current set of words obtained may not be represented as the dataset is considered relatively small. To further improve, we should analyze on:
a) the overlapping/generic keywords and consider removing them.
b) consider getting more data from Reddit or other social media platforms. 

### Recommendations

We have successfully developed a text classifier to categorize the top 2 popular games and identify the top 5 features.

Although we have obtained a model with an accuracy of 89%, we can try to further improve the model accuracy to above 90%. To achieve this, we can consider to:
- Increase the dataset size by scrapping more posts.
- Expand the scope of scrapping using other websites / social platforms (e.g. Twitter) to increase the word vocabulary for better accuracy.
- Experiment with other classifiers and boosting techniques (e.g. Random Forest, Gradient Boosting).

To reduce the misclassification rate for our models, analysis of the overlapping and generic words is recommended. The words identified should be removed during the text preprocessing stage.

With the top keywords, the Marketing team can think of using them to create meaningful topics to engage the users in the forum.

### Future Actions

Moving forward, we will explore doing sentiment analysis for these 2 top popular games and make recommendations to the marketing / business development team to consider for their sales & marketing plans.