# 🎬 Movie Recommendation System

This project builds a complete movie recommendation engine using multiple recommendation strategies on the TMDB 5000 Movies dataset. The goal is to suggest relevant movies to users based on content similarity, user preferences, and a hybrid combination of both approaches.

---

## 🧠 Project Overview

The notebook explores the **TMDB 5000 Movies dataset** to:
- Perform exploratory data analysis on movie metadata
- Build five different recommendation strategies
- Evaluate recommendations using RMSE, MAE and Precision@K
- Provide a unified interface to access all recommendation methods

---

## ⚙️ Features
- 5 recommendation methods in a single unified interface
- Content-Based Filtering using TF-IDF + Cosine Similarity
- Collaborative Filtering using SVD Matrix Factorization
- Hybrid Recommender combining Content-Based and Collaborative scores
- Genre-Based Recommender ranked by IMDB weighted rating
- Top Rated Movies using IMDB weighted rating formula
- Fuzzy title matching for user-friendly search
- Model evaluation: RMSE, MAE, Precision@K

---

## 🧩 Tech Stack
**Language:** Python  
**Libraries:**
- pandas, numpy
- matplotlib, seaborn
- scikit-learn (TfidfVectorizer, TruncatedSVD, cosine_similarity)

---

## 📊 Dataset
- **Source:** Kaggle — TMDB 5000 Movie Dataset
- **Files used:** tmdb_5000_movies.csv, tmdb_5000_credits.csv
- **Size:** ~5000 movies
- **Features include:** genres, keywords, cast, crew, overview, budget, revenue, vote average, popularity
- **Download:** https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata

---

## 📈 Results
- Content-Based Filtering achieves average Precision@10 of ~0.80
- SVD Collaborative Filtering achieves RMSE ~1.2 and MAE ~0.95
- Hybrid Recommender produces more diverse and relevant results than either method alone
- Genres, director, and keywords are the most influential features for content similarity

---

## 🔮 Future Work
- Replace simulated user ratings with MovieLens 100K dataset
- Implement Neural Collaborative Filtering (NCF) using deep learning
- Use BERT-based sentence embeddings for semantic content similarity
- Deploy as a Streamlit or Flask web app with TMDB API integration

---

## 👨‍💻 Author
Baidyanath Kumar Jha  
MCA Graduate, AIML Specialization  
GitHub: [Bkjha1286](https://github.com/Bkjha1286)  
LinkedIn: [baidyanath-kr-jha](https://www.linkedin.com/in/baidyanath-kr-jha-175358287/)
