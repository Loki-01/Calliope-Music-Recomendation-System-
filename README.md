# Music Recommendation System

A machine learning project that recommends songs based on audio features using K-Means clustering and cosine similarity, built with Python and the Spotify dataset.

---

## Dataset

The dataset used is the [Spotify Dataset](https://www.kaggle.com/datasets/vatsalmavani/spotify-dataset) from Kaggle.

| File | Description | Size |
|------|-------------|------|
| data.csv | Main song dataset | 170,653 songs |
| data_by_genres.csv | Songs grouped by genre | 2,973 genres |
| data_by_year.csv | Songs grouped by year | — |
| data_by_artist.csv | Songs grouped by artist | — |

---

## Project Structure

```
music-recommendation-system/
│
├── data.csv
├── data_by_genres.csv
├── data_by_year.csv
├── data_by_artist.csv
│
├── part1_exploration.py        # Data loading and exploration
├── part2_visualization.py      # EDA and visualizations
├── part3_clustering.py         # K-Means clustering
├── part4_recommendation.py     # Recommendation engine
│
└── README.md
```

---

## Project Phases

### Part 1 — Data Loading and Exploration
- Loaded all 4 datasets using pandas
- Displayed first rows, column info, and missing values
- Created a new `decade` column from the `year` column

### Part 2 — Data Visualization
- Count plot of tracks per decade
- Line charts of sound features and loudness over time
- Grouped bar chart of top 10 genres
- Word clouds for genres and artists
- Top 10 artists by song count and popularity score

### Part 3 — Clustering
- Applied K-Means with 12 clusters on genre data
- Applied K-Means with 25 clusters on song data
- Visualized genre clusters using t-SNE
- Visualized song clusters using PCA
- Validated results using the Elbow Method and Silhouette Score

### Part 4 — Recommendation System
- Built a cosine similarity based recommendation engine
- Input: a list of songs with their release year
- Output: top 10 most similar songs from the dataset

---

## How the Recommendation Works

```
Input songs
    ↓ Fetch audio features for each song
    ↓ Calculate mean feature vector (average taste profile)
    ↓ Scale features using StandardScaler
    ↓ Compute cosine similarity with all 170,653 songs
    ↓ Sort by similarity score
    ↓ Return top N recommendations
```

---

## Audio Features Used

| Feature | Description |
|---------|-------------|
| acousticness | How acoustic the song sounds |
| danceability | How easy it is to dance to |
| energy | Intensity and loudness |
| instrumentalness | Amount of vocals |
| liveness | Sounds like a live performance |
| loudness | Overall loudness in dB |
| speechiness | Amount of spoken words |
| tempo | Speed in beats per minute |
| valence | Musical happiness (0=sad, 1=happy) |
| popularity | Spotify popularity score (0-100) |

---

## Installation

```bash
pip install pandas numpy scikit-learn plotly seaborn matplotlib wordcloud spotipy
```

---

## How to Run

1. Download all 4 CSV files from Kaggle
2. Upload them to Google Colab or place them in the project folder
3. Run each part in order from Part 1 to Part 4

---

## Example Usage

```python
my_songs = [
    {"name": "Shape of You",    "year": 2017},
    {"name": "Blinding Lights", "year": 2019},
    {"name": "Dance Monkey",    "year": 2019}
]

results = recommend_songs(my_songs, n_songs=10)
print(results)
```

```
                        name                    artists  year  popularity  similarity
    The Weekend Funk Wav Remix    SZA, Calvin Harris     2017          76      0.9884
                  If I Know Me         Morgan Wallen     2018          72      0.9823
                        Closer  The Chainsmokers, Halsey 2016         84      0.9671
```

---

## Clustering Results

| Task | Method | Result |
|------|--------|--------|
| Genre clustering | K-Means K=12 | 12 groups assigned to 2,973 genres |
| Song clustering | K-Means K=25 | 25 groups assigned to 170,653 songs |
| Silhouette Score | — | 0.143 |

> The low Silhouette Score is expected. Music genres overlap by nature in audio feature space since genre is a cultural label, not a purely sonic boundary.

---

## Technologies Used

- Python 3
- Pandas
- NumPy
- Scikit-learn
- Plotly Express
- Seaborn
- Matplotlib
- WordCloud
- Spotipy

---

## Author

Abderrahim Nait Ali Mohamed — Data Science Student
