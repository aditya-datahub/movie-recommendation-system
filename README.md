# 🎬 Movie Recommendation System

A content-based movie recommender that suggests similar movies using **TF-IDF vectorization** and **cosine similarity**, built with `scikit-learn` and `pandas`.

Give it a movie you like, and it finds the closest match in the dataset, then ranks and returns the most similar titles based on genre, keywords, tagline, cast, and director.

## How It Works

1. **Feature selection** — Five text features are pulled from each movie: `genres`, `keywords`, `tagline`, `cast`, and `director`.
2. **Feature combination** — These fields are concatenated into a single string per movie.
3. **Vectorization** — `TfidfVectorizer` converts the combined text into numerical feature vectors.
4. **Similarity computation** — `cosine_similarity` computes pairwise similarity scores between every movie in the dataset.
5. **Matching** — When a user enters a movie name, `difflib.get_close_matches` finds the closest matching title in the dataset (handles typos/partial input).
6. **Ranking** — Movies are sorted by similarity score to the matched title, and the top results are returned.

## Dataset

`movies.csv` contains metadata for ~4,800 movies, including budget, genres, keywords, cast, crew, director, overview, ratings, and more (sourced from TMDB).

## Getting Started

### Prerequisites

```bash
pip install -r requirements.txt
```

### Usage

Open and run `main.ipynb` in Jupyter Notebook / JupyterLab. When prompted, enter the name of a movie you like:

```
Enter your favourite movie name: Avatar
```

The system will output a ranked list of similar movies:

```
Movies suggested for you:

1 _ Avatar
2 _ Aliens vs Predator: Requiem
3 _ Independence Day
4 _ Titan A.E.
...
```

## Tech Stack

- **Python 3**
- **pandas** — data loading and manipulation
- **NumPy** — numerical operations
- **scikit-learn** — `TfidfVectorizer` and `cosine_similarity`
- **difflib** — fuzzy string matching for movie title lookup

## Project Structure

```
movie-recommendation-system/
├── main.ipynb          # Core notebook: data prep, vectorization, similarity, recommendation
├── movies.csv           # Movie metadata dataset
├── requirements.txt      # Python dependencies
├── LICENSE               # MIT License
└── README.md
```

## Future Improvements

- Wrap the recommendation logic in a reusable function/CLI instead of relying on notebook `input()` prompts
- Add a simple web UI (e.g. Streamlit or Flask)
- Incorporate additional signals like `overview` text or `vote_average` weighting
- Add unit tests and input validation for unmatched titles

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.
