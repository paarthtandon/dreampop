# Models

In this section, I created both classification and clustering models.

# Classification

One of the major goals of this project was to classify between dreampop and non-dreampop songs. First, I split the data into train and test sets. Then, I trained various machine learning models (listed below) to gauge the performance. Finally, I used KFold (k=5) validation to compare all the models fairly. Here are the results:

| Model                       | Average accuracy over 5 folds |
|-----------------------------|-------------------------------|
| Random Forest               | 0.8245                        |
| Support Vector Machine      | 0.7727                        |
| Decision Tree               | 0.7612                        |
| Stochastic Gradient Descent | 0.6678                        |
| K-Nearest Neighbors         | 0.5975                        |
| Naïve Bayes                 | 0.5455                        |
| Logistic Regression         | 0.5166                        |

As you can see, the random forest model performed very well. Logistic regression performed the worst, pointing towards this problem being non-linear in nature. Naïve bayes also performed poorly, most likely because of the correlation between certain variables, pointing towards some of the variables being non-independent. K-NN's poor performance is probably due to its sensitivity to outliers. Given that this dataset is not perfect, there are many outliers. The SVM and decision tree models also performed well, most likely due to the dimensionality of the problem, as both these models thrive in higher dimensions.

### Feature Importance

We can use the random forest model to determine the importance of each feature. Here are the scores for each feature:

| feature          | importance |
|------------------|------------|
| instrumentalness | 0.1466     |
| speechiness      | 0.0489     |
| danceability     | 0.0482     |
| energy           | 0.0327     |
| valence          | 0.0299     |
| acousticness     | 0.0285     |
| duration_ms      | 0.0266     |
| loudness         | 0.0181     |
| tempo            | 0.0122     |
| liveness         | 0.0043     |
| mode             | 0.0029     |
| key              | 0.0012     |
| time_signature   | 0.0004     |

Seems like instrumentalness was overwhelmingly the most important feature, and liveness, mode, key, and time_signature was very unimportant.

# Clustering

Clustering was attempted, but nothing of value was found. If you are interested in seeing what I did, check out `clustering.ipynb`.
