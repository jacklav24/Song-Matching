# Song Recommender using PCA, KMeans Clustering, and Spotify Search

Have you ever wondered how many fantastic songs you're missing out of because they just aren't that popular on Spotify? No? Well, I have. In fact, what if you could be recommended songs that exclusively had little to no streams on Spotify? I'm nearly 100% sure you've never wondered that, and it's a silly question. But, a fun data science project! Who knows- maybe this'll help you find some hidden gems.

This project builds a content-based song recommender system. It combines audio feature engineering, dimensionality reduction with Principal Component Analysis (PCA), unsupervised clustering using KMeans, and cosine similarity matching to recommend sonically (and statistically) similar tracks - specifically ones with hardly any streams. It's cool to see which songs are similar based on these statistics, and the results aren't always what you expect. It's tough to quantify music, especially with limited data like this!

As spotify changed their API a few years ago, we only have databases from 2022 and further in the past to look at. Thus, the songs which you can input are limited by that. But, I've found a pretty good dataset with lots of songs.

However, it should be used and viewed in context. Ultimately no audio comparison is done. That would be the best recommendation system. But, what we can do is use the quantifiable metrics we do have to pick some songs. This means two things- we get objectively similar songs, but they don't always sound the same, seem the same, or fall into the same genre. I considered adding some genre constraints, but then realized- it's more fun if its purely statistical similarities, using KMeans. We're talking about songs with <1000 plays, after all.

The most fun use of this project is inputting a massively famous song, and seeing which completely unknown songs are really quite similar. The results are fun.

## Project Overview

This is a single jupyter notebook, with user input.

The pipeline performs the following steps:
1. **Data Sourcing**
   Kaggle!

3. **Data Cleaning and Feature Normalization**  
   Selected song audio features are scaled using `StandardScaler` to ensure uniform contribution during clustering and similarity calculation.

4. **Dimensionality Reduction**  
   PCA is applied to reduce the high-dimensional feature space to two components for interpretability and visualization.

5. **KMeans Clustering**  
   Songs are grouped into clusters based on their audio profile.

6. **Recommendation Logic**  
   Given a song and artist name, the system:
   - Searches the dataset for the track.
   - Identifies its cluster.
   - Returns a list of similar songs from an "unpopular" track dataset using cosine similarity within the same cluster.

## Features Used

The following audio features are used:

- Danceability  
- Energy  
- Loudness  
- Speechiness  
- Acousticness  
- Instrumentalness  
- Liveness  
- Valence  
- Tempo  

These features were selected for their relevance to sonic similarity and are scaled before PCA and clustering.

## Requirements

```bash
pip install pandas numpy scikit-learn matplotlib rapidfuzz

## Data Sources

kaggle - unpopular spotify songs : https://www.kaggle.com/datasets/estienneggx/spotify-unpopular-songs
kaggle - spotify song stats dataset
