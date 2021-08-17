# Extract, Transform, Load

In this section, I first download the song data from the Spotify API. Then, I both save the data as a CSV, as well as upload the data to my personal PostgreSQL database. It's split into two notebooks: `ETL_dream.ipynb` and `ETL_other.ipynb`. The first is to load dreampop song data, the second is to load song data from other genres on Spotify.

## `ETL_dream.ipynb`

Since "dreampop" is not an official genre on Spotify, I had to improvise a way to collect data about dreampop songs. I did this by using Spotify's search function. I used the Spotify API to search playlists with the query "dream pop":

`playlists = sp.search(q='dream pop', type='playlist', limit=50, offset=0)`

From there, I generated a set of track IDs from the playlists, resulting in 8,178 dreampop songs. Spotify's API can provide audio features about a track given the ID of the track. This includes sonic features about the track such as loudness, instrumentalness, etc. It is limited by how many tracks you can analyze at a time (100), so I first had to split the tracks into 100 long chunks. Then I retrieved the audio features for each chunk:

`audio_features = sp.audio_features(tracks=chunk)`

Then, the data was saved as a CSV and uploaded to my database.

## `ETL_other.ipynb`

Since one of the goals of this project is to build a model that can classify dreampop songs from other music, I needed data about other music. To do this I retrieved 100 recommended tracks from each genre on Spotify:

`recs = sp.recommendations(seed_genres=[genre], limit=100)`

The API lists 126 genres, not all of which had 100 recommended tracks, so in total 12,526 tracks were retrieved. After that, the audio features were retrieved for each song and the data was saved/uploaded the same way as with the previous notebook.
