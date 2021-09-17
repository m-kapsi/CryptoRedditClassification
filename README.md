# Classification of 'CryptoCurrency' and 'Stocks' Subreddits

### Background

CryptoGo is a FinTech startup that sells cryptocurrency products. They are looking to expand their customer base by running an online marketing campaign on the social media platform, Reddit. With a limited budget, CryptoGo wants to target their advertisements to all users on Reddit who have already expressed some interest in cryptocurrency and would therefore be more likely to invest in cryptocurrency products.

CryptoGo would like to leverage on Reddit's subreddit targeting model to ensure they are getting the relevant ads to the communities most interested in cryptocurrency. CryptoGo has already identified the "CryptoCurrency" subreddit as one of the subreddits they are looking to target. The "CryptoCurrency" subreddit is an active subreddit with over 3 million members posting news and discussions on cryptocurrency.

In order to identify similar posts across Reddit, CryptoGo has tasked its Data Science team to build a classification model that can predict whether or not a post belongs to the CryptoCurrency subreddit with at least a 90% sensitivity and F1 score. The team will build a binary classification model to identify whether a post belongs to the "CryptoCurrency" or "Stocks" subreddit. The "Stocks" subreddit is another active subreddit with over 2.8 million members. As the "Stocks" subreddit is also related to a popular financial product, training the model to predict whether a post belongs to "CryptoCurrency" or "Stocks" will allow CryptoGo to identify more relevant, cryptocurrency affiliated posts across Reddit than if the model was trained using a non-financial subreddit. This model can then be used to identify other posts on Reddit with a similar interest in cryptocurrency so CryptoGo can expand their marketing to other subreddits.

Additionally, CryptoGo is looking to identify key words and phrases that people use when discussing cryptocurrency on social media, which will help them understand the market sentiment and develop their marketing campaign more effectively.

---

### Problem Statement

The goal of this project is to build a binary classification model to predict if a post on reddit belongs to the "CryptoCurrency" or "Stocks" subreddit. The model will be considered successful if both the F1 score and sensitivity are above 90%.

Additionally, the project aims to provide insights on the key words and phrases that people use when discussing cryptocurrency on reddit, which could be used to develop a more effective marketing campaign for cryptocurrency.

---

### Summary of Analysis

Because the goal of this project was to be able to predict whether a post belonged to r/CryptoCurrency or not, I identified posts from r/CryptoCurrency as "True" and posts from r/stocks as False. This means that:
  * True Positives are posts that my model correctly predicts are from r/CryptoCurrency
  * True Negatives are posts that my model correctly predicts are from r/stocks
  * False Positves are posts that my model incorrectly predicts are from r/CryptoCurrency (but are actually from r/stocks)
  * False Negatives are posts that my model incorrectly predicts are from r/stocks (but are actually from r/CryptoCurrency)

For this project, I trained multiple models including a baseline model, Random Forest Classifier, Multinomial Naive Bayes, and Support Vector Classifier. I evaluated the models using the following metrics:
  * F1 score: I compared the F1 scores of my train, test, and cross validation sets in order to assess if my models were overfitted or underfitted
  * Recall: I tuned my hyperparameters for each model using recall to minimize the false negative rate. The purpose of minimizing the false negative rate is to ensure that the final model will capture all posts that may be related to cryptocurrency, even if it means marketing to some posts that are not interested in cryptocurrency.
  * ROC AUC, Recall, and F1 score: I used the three metrics to compare the performance of my test data on each model so that I could see how well each model performed on new data

The model I used as my final production model was a votinng classifier that used the Random Forest Classifier, Multinomial Naive Bayes, and Support Vector Classifier models. This model had an F1 score of 97% and a recall score of 98%.

---

### Conclusion

CryptoGo will be able to use this model to show their advertisement on posts that are most relevant to cryptocurrency. If CryptoGo wants to spend 2000 dollars on its reddit advertising campaign and every advertisement placement on reddit costs 1 dollar, ideally they would want to spend 2000 dollars on posts that users interested in cryptocurrency would see. If they were to target random posts in the r/Stocks and r/CryptoCurrency, they would spend approximately 1000 dollars on the correct audience, and approximately 1000 dollars on the wrong audience. Instead, if CryptoGo used this model to only target posts they predicted are interested in cryptocurrency, they would spend 1,915 dollars on the correct audience, and only 85 dollars on the wrong audience (the false positive rate is 4.2%). This would save 915 dollars that was being allocated incorrectly to target the wrong audience.

### Business Recommendations

In addition to classifying posts for targeted marketing, the sentiment analysis can also be used to identify posts that have a higher positive polarity score and may therefore be more receptive to advertisements related to cryptocurrency products. For example, many of the posts with a high positive polarity score in r/CryptoCurrency are related to free money, or happiness, or see high potential in investing in cryptocurrency. Showing advertisements alongside such posts would bring in more customers than showing advertisements with posts that have high negative polarity scores, where many posts are concerned about being scammed or losing money through investing in cryptocurrency. This may also be useful to note when planning the marketing strategy for CryptoGo - while the target audience is interested in earning “free” money or getting high returns, there is a concern that cryptocurrency products are high risk and maybe scams, so it would be important to assure potential customers through marketing that CryptoGo is a trustworthy company.

CryptoGo also wanted to know key words and phrases that are unique among people interested in cryptocurrency when compared to other financial products such as stocks. Some of these key phrases are ‘hardware wallet’, ‘bitcoin mining’, and ‘smart contracts’. It is also worth noting that two of the most frequent phrases in r/CryptoCurrency are “Saylor Academy” and “National Paralegal College”. Both institutions provide free online courses for people who are interested in learning more about cryptocurrency. As people who either post about or read posts about these courses are looking for resources to begin their cryptocurrency journey, it could be a good strategy to target marketing towards posts mentioning these institutions.

### Further Steps

The purpose of this model in production is to be able to identify posts that are similar to posts in r/CryptoCurrency across other subreddits. This will help CryptoGo to target their marketing to other active subreddits that have a similar interest in cryptocurrency, and would therefore be more likely to invest with CryptoGo. In order to make the model more robust, it would be good to train the model on other (both financial and non-financial) subreddits as well, so that the model is better at predicting cryptocurrency related posts against a variety of other posts. Depending on how the marketing campaign on Reddit is received, the model could also be trained on other social media platforms to expand CryptoGo’s marketing to platforms such as YoutTube or Instagram. Additionally, training the model on cryptocurrency related news articles may help the model to identify posts linked to current events that are also relevant to cryptocurrency.
