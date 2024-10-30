# Song Recommender Project
Given an input playlist, output a playlist of new song recommendations! This is a project that I did a few years ago when I was first getting into data science. But I wanted to add this project now to be an example of  some of the things I worked on in my data science journey.


## Song Recommender Project Overview
This project processes Spotify track data to generate feature vectors for songs and playlists. It uses a combination of audio features (like danceability, energy, and tempo) to recommend songs that are similar to a given playlist. Some key tasks include:
- Scaling audio features using StandardScaler.
- Calculating cosine similarity between playlists and songs.
- Filtering out duplicate songs when creating new playlists.
- Verifying if specific artists or songs exist in the dataset.

## The Idea and Thought Process
In this project, I analyze Spotify track features which I use their float values to calculate a similarity between songs and playlists. Specifically, we are trying to use the power of cosine similarity, which is usually used to measure how similar two vectors (or sets of features which actually will represent a single song) are in terms of their direction as well as feature space.

Clustering is an Unsupervised Learning technique used to group similar data points together. We will have each point representing a song vector in N-dimensional Euclidean space (where N represents the number of featurees). We want to essentially plot every song in our dataset in this space and find the k-number of songs that are closest in space to the vector that represents our input playlist. Note: Even though our input playlist will have multiple songs, we will aggregate it such that we can create a vector to represent the entire thing. Songs that are more similar will form clusters.

We wouldn't use other techniques like regression or classification because we are not working with continuous values or have predefined categories (for classification) where we would attempt to label our clusters in this scenario.

## Dataset
The dataset used in this project contains various audio features for Spotify tracks, such as:
- `danceability`, `energy`, `loudness`, `speechiness`, `acousticness`, `instrumentalness`, `liveness`, `valence`, `tempo`
- Metadata like `song id`, `artist`, `artist id`, `popularity`, and `release date`.

> **Note:** The dataset (`tracks.csv`) is not included in this repository due to its large size. There are over 500,000 songs , but you can download the dataset from [https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset], or use your own Spotify dataset with similar features.

### Key Functions:
- **`scale_playlist(df)`**: Scales the audio features of a playlist using `StandardScaler`.
- **`generate_playlist_feature()`**: Generates a feature vector for an entire playlist by summing up its features.
- **`cosine_sim1(pl1, pl2)`**: Calculates cosine similarity between two feature vectors.
- **`songs_table_with_similarity()`**: Finds and ranks songs by their similarity to a given playlist.
- **`generate_complete_playlist()`**: Generates a new playlist by finding the most similar songs from a larger dataset.

# Example usage in a Jupyter notebook:
taylor_playlist = renamed_scaled[renamed_scaled["artist"].str.contains('Taylor Swift')]
generate_complete_playlist(renamed, taylor_playlist, 10)
