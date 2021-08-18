# Exploratory Data Analysis
In this notebook I generate some visualizations and run some statistical tests to better understand the data. Each section below corresponds with a section in the notebook.

## Download/Setup Data

The data is downloaded from the PostgreSQL server, and loaded into a dataframe. From there, I add a new column called `is_dreampop`, which is `True` if the song is dreampop, otherwise it is `False`:

`data['is_dreampop'] = data['genre'].apply(lambda x: True if x == 'dreampop' else False)`

## Describe Data

In this section, I generated some visualizations to help better understand the data. These visualizations can be seen in the notebook. The features that were analyzed include danceability, acousticness, energy, instrumentalness, liveness, loudness, speechiness, tempo, valence, and duration.

First, I created a correlation matrix for both the whole dataset, as well as for only dreampop songs. Both matrices seem to be very similar, so each of the features must correlate similarly regardless of whether the song is dreampop or not. Next, I created boxplots for each feature, comparing dreampop songs to the rest of the dataset. From this it is very clear that the speechiness and instrumentalness differs a lot between dreampop and non-dreampop songs. The rest of the boxplots also present some differences, but nothing as extreme. Finally, I created histograms for each feature, comparing dreampop songs to the rest of the dataset. This confirmed that the distribution of the songs' speechiness and instrumentalness differs a lot between dreampop and non-dreampop songs. It also shows that the distribution of the songs' energy, loudness, valance, and duration are visually different.

## Statistical Tests

We can only gain so much from visualization, so we must confirm our expectations with statistical tests. All three of these tests are used to determine whether a sample came from the same population or not. If they result in a p-value less that 0.05 we can reject our null hypothesis, that the samples came from the same population. In the context of this problem, this would mean that the given feature's distribution is statistically the same whether or not the song is dreampop. Note: t-test generally assumes that the distribution is normal, which is not a given for this data. The other two tests (KS test, Mann-Whitney U test) do not assume this. The results of these tests show that, in fact, all the features are significantly different when comparing dreampop and non-dreampop songs. These results can be viewed in the notebook.

This means that all features should be used when creating models for this dataset.
