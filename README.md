# Spotify Recommendation System

This algorithm implements a **content-based recommendation engine** by using the [Spotify dataset from Kaggle](https://www.kaggle.com/yamaerenay/spotify-dataset-19212020-160k-tracks) and the user's data from retrieved from their Spotify account by leveraging [spotipy](https://spotipy.readthedocs.io/en/2.18.0/) -- a python library for [Spotify Web API](https://developer.spotify.com/documentation/web-api/). 

The algorithm uses the following steps: 
1. Spotify data from Kaggle is cleaned and pre-processed to create a 30-dimensional vector space containing ~500,000 vectors (each vector represents a track/song)
2. A connection is made to the user's Spotify account to retrieve their listening history
3. User's data is cleaned, pre-processed, and fed through a feature engineering process to add temporal information to the user's data
4. The engineered user data is used to create a "user persona" which represents the user's current musical taste by aggregating features of all the songs the user has recently heard. This step results in a singular vector representing the user persona. 
5. **Cosine-similarity** is used to calculate the angle between the user persona vector and all of the song vectors. The smaller the angle, the higher the similarity. Top **n** songs with the highest cosine-similarity are recommended to the user

This recommendation system only takes into account musical features of a song (bass, treble, mids, etc.) that can be retireved from Spotify using their [Get Audio Features API Reference](https://developer.spotify.com/documentation/web-api/reference/#endpoint-get-audio-features). 
It doesn't take into account meta-data like: 
1. Year of release
2. Genre
3. Artist
4. Popularity
5. Length of a song etc. 

This was primarily an experiement for me to see if I could expand my musical taste/preferences by solely focusing on "how" a song sounds and feels, instead of "what" genre or artist it belongs to. I liked the recommendations my system gave me. 
