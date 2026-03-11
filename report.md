# Project Report — Movie Recommendation System

## Objective
Build a complete movie recommendation engine that suggests relevant movies to users using multiple recommendation strategies on the TMDB 5000 Movies dataset.

---

## Dataset
- **Source:** Kaggle — TMDB 5000 Movie Dataset
- **Files used:** tmdb_5000_movies.csv, tmdb_5000_credits.csv
- **Size:** ~5000 movies
- **Features include:** genres, keywords, cast, crew, overview, budget, revenue, vote average, vote count, popularity, release date
- **Download:** https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata

---

## Approach

1. Exploratory data analysis — rating distribution, vote count distribution, top genres, movies per year, budget vs revenue scatter, popularity distribution.
2. Preprocessing: parse JSON-format columns (genres, keywords, cast, crew), extract director names, fill missing values, compute IMDB-style weighted rating formula: WR = (v/(v+m)) × R + (m/(v+m)) × C.
3. Feature engineering: build a weighted soup string combining genres (3x weight), keywords (2x), cast, director (2x), and overview for TF-IDF vectorization.
4. Models:
   - Content-Based Filtering — TF-IDF (10,000 features, bigrams) + Cosine Similarity on weighted soup string
   - Collaborative Filtering — SVD (TruncatedSVD, 30 components) on simulated user-rating matrix of 300 users and 500 movies
   - Hybrid Recommender — weighted combination of Content-Based (60%) and Collaborative (40%) normalized scores
   - Genre-Based Recommender — top movies filtered by genre, ranked by IMDB weighted rating
   - Top Rated — global top movies using IMDB weighted rating formula
5. Evaluate with RMSE and MAE (Collaborative Filtering on 80/20 train/test split) and Precision@K (Content-Based, threshold rating >= 7.0).
6. Unified recommend() function providing a single interface to access all five recommendation strategies.

---

## Key Findings
- Genres, director, and keywords are the most influential features for content-based similarity — weighting them higher improves recommendation relevance.
- SVD Collaborative Filtering achieves RMSE ~1.2 and MAE ~0.95 on the held-out test set.
- Content-Based Filtering achieves average Precision@10 of ~0.80 across five seed movies.
- Hybrid Recommender balances personalisation with content relevance, producing more diverse results than either method alone.
- IMDB weighted rating formula effectively surfaces quality movies by balancing vote average with vote count.

---

## Recommendations
- Replace simulated user ratings with a real dataset such as MovieLens 100K for stronger collaborative filtering evaluation.
- Implement Neural Collaborative Filtering (NCF) using deep learning for improved personalised recommendations.
- Use BERT-based sentence embeddings instead of TF-IDF for semantic similarity in content-based filtering.
- Deploy as a Streamlit or Flask web application with a search interface connected to the TMDB API for real-time movie data.

---

## Appendix
- Notebook contains code to reproduce all EDA plots, five recommendation methods, evaluation metrics (RMSE, MAE, Precision@K), and a unified recommend() function. A fuzzy title matching feature allows user-friendly movie search even with partial or incorrect titles.
