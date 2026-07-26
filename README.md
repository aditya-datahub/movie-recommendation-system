<div align="center">

# 🎬 Movie Recommendation System

**A content-based recommender that suggests similar movies using TF-IDF + Cosine Similarity**

[![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![pandas](https://img.shields.io/badge/pandas-Data-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

</div>

---

## 📌 Overview

Tell it a movie you like, and it recommends the movies most similar to it — no ratings, no user history, just the content of the movie itself.

This project applies **NLP feature engineering** and **vector space modeling** to build a content-based recommendation engine from scratch on a real-world dataset of ~4,800 TMDB movies, without relying on any pre-built recommendation library.

```
Enter your favourite movie name: Avatar

Movies suggested for you:

1 _ Avatar
2 _ Aliens vs Predator: Requiem
3 _ Independence Day
4 _ Titan A.E.
5 _ Small Soldiers
...
```

## 🧠 How It Works

| Step | What Happens |
|------|--------------|
| **1. Feature Selection** | Pulls five signal-rich text fields per movie: `genres`, `keywords`, `tagline`, `cast`, `director` |
| **2. Feature Fusion** | Concatenates them into one combined text "profile" per movie |
| **3. Vectorization** | Converts text into numerical vectors with `TfidfVectorizer`, weighting rare/distinctive terms higher than common ones |
| **4. Similarity Scoring** | Computes pairwise **cosine similarity** across all ~4,800 movies to build a full similarity matrix |
| **5. Fuzzy Matching** | Uses `difflib.get_close_matches()` so the user's input doesn't need to be an exact title match |
| **6. Ranking** | Sorts and returns the top-N most similar movies to the matched title |

**Why TF-IDF over a simple word count?** TF-IDF down-weights common terms (like "Drama") that appear across many movies and up-weights terms that make a movie's profile *distinctive* — leading to more meaningful similarity scores than raw term frequency.

## 🗂️ Dataset

`movies.csv` — metadata for **4,800+ movies** sourced from TMDB, including budget, genres, keywords, overview, cast, crew, director, revenue, runtime, and vote data.

## 🚀 Getting Started

```bash
# Clone the repo
git clone https://github.com/aditya-datahub/movie-recommendation-system.git
cd movie-recommendation-system

# Install dependencies
pip install -r requirements.txt

# Launch the notebook
jupyter notebook main.ipynb
```

Run the cells, then enter a movie name when prompted — recommendations print instantly.

## 🛠️ Tech Stack

- **Python 3**
- **pandas** & **NumPy** — data loading, cleaning, and numerical operations
- **scikit-learn** — `TfidfVectorizer` for vectorization, `cosine_similarity` for scoring
- **difflib** — fuzzy string matching for title lookup

## 📁 Project Structure

```
movie-recommendation-system/
├── main.ipynb          # Data prep → vectorization → similarity → recommendations
├── movies.csv          # Movie metadata dataset (TMDB)
├── requirements.txt    # Python dependencies
├── LICENSE             # MIT License
└── README.md
```

## 🔭 Roadmap

- [ ] Refactor notebook logic into a reusable Python module / CLI (remove `input()` dependency)
- [ ] Ship a lightweight web app with Streamlit for interactive demos
- [ ] Blend in `overview` text and `vote_average` as additional similarity signals
- [ ] Add unit tests and graceful handling for unmatched/misspelled titles

## 👤 Author

**Aditya Sharma**
Feel free to connect or reach out with feedback!

## 📄 License

Licensed under the [MIT License](LICENSE).
