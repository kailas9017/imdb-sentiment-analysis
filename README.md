# IMDB Sentiment Analysis Django Project

Classifies movie reviews as `positive` or `negative` using NLP preprocessing, TF-IDF vectorization, and a Naive Bayes classifier. Optional scripts are included for Word2Vec + LSTM and BERT.

## Project Features

- Text preprocessing: HTML cleanup, lowercasing, stop-word removal, stemming.
- Vectorization: TF-IDF for the main deployed model.
- Models: Naive Bayes, plus optional LSTM and BERT training scripts.
- Django frontend: paste a review and get sentiment, confidence, and preprocessing details.

## Setup

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

## Train the TF-IDF + Naive Bayes Model

The script defaults to the dataset path you provided:

`C:\Users\Kaila\OneDrive\Desktop\SentimentAnalysisProject\sentiment_project\dataset\imdb_reviews.csv`

```powershell
python sentiment_app\ml\train_naive_bayes.py
```

You can also pass another CSV:

```powershell
python sentiment_app\ml\train_naive_bayes.py --data dataset\imdb_reviews.csv
```

For a quick classroom demo run:

```powershell
python sentiment_app\ml\train_naive_bayes.py --limit 5000
```

## Run the Django App

```powershell
python manage.py migrate
python manage.py runserver
```

Open `http://127.0.0.1:8000/`.

## Optional Advanced Models

These require heavier dependencies and more compute:

```powershell
python sentiment_app\ml\train_word2vec_lstm.py --data dataset\imdb_reviews.csv
python sentiment_app\ml\train_bert.py --data dataset\imdb_reviews.csv
```

The web app uses the trained Naive Bayes model at `models/naive_bayes_tfidf.joblib`. If that file is not available yet, it falls back to a small lexicon-based demo predictor so the UI can still be tested.
