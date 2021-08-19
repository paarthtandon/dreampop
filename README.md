# Dreampop, uncovering a hidden genre using Data Science.

Project goals:
* Determine which aspects of dreampop music make it what it is.
* Build a model that can classify between dreampop music and other music.

## What is dreampop?

Wikipedia defines "dreampop" as "a subgenre of alternative rock and neo-psychedelia that is characterized by its preoccupation with atmosphere and sonic texture as much as pop melody, including characteristics such as guitar effects like reverb and echo, breathy vocals, and dense productions."

Personally, I think the easiest way to understand dreampop is by listening to it. Check out [Only In My Dreams by The Marías](https://www.youtube.com/watch?v=qrqywuDWz_Q)!

## Project Structure

Each section folder contains its own README that goes further in depth. Here is an overview of the project structure:

**ETL (Extract, Transform, Load):** Download data using the Spotify API, upload it to personal PostgreSQL database.\
**EDA (Exploratory Data Analysis):** Visualize features using descriptive statistics to understand the data better.\
**Models (Classification, Clustering):** Create models that can help us determine whether a song is dreampop.

## Playlist

I created a playlist for all the dreampop songs that were collected (9,315)! Note, that this is an autogenerated list, so not all the songs will really be dreampop, but so far I have not found many non-dreampop songs.

Here is the link: [Dreampop (Generated)](https://open.spotify.com/playlist/0gXnKF7IfnEpeuqYAgUimy?si=8b530514acc14353)

Check out `playlist.ipynb` to see how I generated it.

## Results

For detailed results check out the [models](https://github.com/paarthtandon/dreampop/tree/master/models) folder. Here are the result tables:

Classification:
| Model                       | Average accuracy over 5 folds |
|-----------------------------|-------------------------------|
| Random Forest               | 0.8245                        |
| Support Vector Machine      | 0.7727                        |
| Decision Tree               | 0.7612                        |
| Stochastic Gradient Descent | 0.6678                        |
| K-Nearest Neighbors         | 0.5975                        |
| Naïve Bayes                 | 0.5455                        |
| Logistic Regression         | 0.5166                        |

Feature Importance:
| Feature          | Importance |
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
