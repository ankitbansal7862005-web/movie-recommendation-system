# 🎬 Movie Recommendation System

A content-based movie recommendation engine that suggests the top 10 most similar movies to a given title, using NLP-based text processing and TF-IDF + cosine similarity. Deployed as an interactive web app with Streamlit.

**🔗 Live Demo:** https://movie-recommendation-system-ankit.streamlit.app/
**📁 Dataset:** ~50,000 movies (metadata: cast, crew, genres, keywords, overview)

---

## 📌 Features

- Content-based recommendations using movie metadata (genres, cast, crew, keywords, overview)
- Genre-based and category-based filtering for more relevant results
- Text preprocessing pipeline: lowercasing, punctuation removal, stop-word removal, tokenization
- TF-IDF vectorization + cosine similarity for ranking similar movies
- Precomputed similarity matrix serialized with Pickle for fast, low-latency inference
- Movie poster fetching via the TMDB API
- Simple, interactive UI built with Streamlit

---

## 🛠️ Tech Stack

- **Language:** Python
- **Data Processing:** Pandas, NumPy
- **NLP:** NLTK
- **ML:** Scikit-learn (TF-IDF Vectorizer, Cosine Similarity)
- **Web App:** Streamlit
- **API:** TMDB API (posters & movie metadata)

---

## 📂 Project Structure

```
├── app.py                  # Streamlit app entry point / UI logic
├── main.py                 # Core recommendation logic
├── movies.ipynb            # Data cleaning, preprocessing & model building notebook
├── movies_metadata.csv     # Raw movie dataset
├── df.pkl                  # Cleaned & processed movie dataframe (pickled)
├── indices.pkl             # Movie title-to-index mapping (pickled)
├── tfidf.pkl                # Trained TF-IDF vectorizer (pickled)
├── tfidf_matrix.pkl        # Precomputed TF-IDF matrix (pickled)
├── requirements.txt        # Python dependencies
├── runtime.txt             # Python runtime version for deployment
└── .python-version         # Python version pin
```

---

## ⚙️ How It Works

1. **Data Cleaning** — Remove null values, drop duplicates, filter out movies with no title, and select relevant columns for prediction.
2. **Feature Engineering** — Extract genres and IDs from nested fields; combine key metadata (genres, cast, crew, keywords, overview) into a single `tags` column.
3. **Text Preprocessing** — Convert text to lowercase, strip punctuation, remove stop words, and tokenize using NLTK.
4. **Vectorization** — Transform the cleaned text into numerical vectors using TF-IDF.
5. **Similarity Computation** — Calculate cosine similarity across the TF-IDF matrix to measure how alike movies are.
6. **Recommendation** — For a selected movie, return the top 10 most similar titles based on similarity scores.
7. **Deployment** — Serialized artifacts (`df.pkl`, `indices.pkl`, `tfidf.pkl`, `tfidf_matrix.pkl`) are loaded at runtime in `app.py` to serve fast recommendations via Streamlit, with posters fetched live from the TMDB API.

---

## 🚀 Getting Started

### Prerequisites
- Python (version specified in `3.11.9`)
- A [TMDB API key](https://www.themoviedb.org/documentation/api)

### Installation

```bash
# Clone the repository
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>

# Create and activate a virtual environment
python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Set up your TMDB API key
Create a `.env` file or set an environment variable:
```
TMDB_API_KEY=your_api_key_here
```

### Run the app

```bash
streamlit run app.py
```

The app will open in your browser at `http://localhost:8501`.

---

## 🧠 Model Notebook

All data cleaning, preprocessing, feature engineering, and model-building steps are documented in `movies.ipynb`. The final processed dataframe and similarity artifacts are exported as `.pkl` files for use in the deployed app.

---

## 📈 Future Improvements

- Add collaborative filtering / hybrid recommendation approach
- Add user rating-based personalization
- Improve UI with movie trailers and cast details
- Add search-as-you-type autocomplete for movie selection

---






