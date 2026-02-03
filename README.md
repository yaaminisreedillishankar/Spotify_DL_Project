## Spotify Track Popularity Prediction

##  Introduction
Music streaming platforms like Spotify rely on understanding user engagement to improve recommendations, playlist curation, and promotional strategies. One of the strongest indicators of engagement is **track popularity**, measured on a scale from **0 to 100**.

This project focuses on predicting the popularity of a Spotify track using its available metadata, framed as a **supervised regression problem**.


##  Project Objective
The main goal is to predict **track popularity** using:
- Track characteristics
- Artist attributes
- Album information
- Temporal features

The project compares **traditional machine learning models** with a **deep learning approach (ANN)** to evaluate performance on structured tabular data.


##  Why This Problem Matters
- Real-world business relevance (recommendation systems, music marketing)
- Excellent example of tabular regression
- Enables comparison between ML models and deep learning
- Highlights the importance of **feature engineering** and **model explainability**


##  Dataset Overview

### Data Source
Spotify track metadata collected from the Spotify platform.

### Target Variable
- **`track_popularity`** (continuous, range: 0–100)

### Feature Types

| Feature Type | Examples |
|-------------|----------|
| Numerical | Track duration, artist popularity |
| Categorical | Artist genre, album type |
| Temporal | Release year |

Each row represents a single track, making the dataset suitable for supervised learning.


##  Data Preprocessing

The dataset underwent extensive preprocessing to ensure modeling reliability.

### Preprocessing Steps
- ✔ Missing values handled
- ✔ Duplicate records removed
- ✔ Date fields parsed correctly
- ✔ Invalid numeric ranges filtered
- ✔ Categorical values cleaned and standardized

### Outcome
A clean, high-quality dataset with no data leakage or structural issues, ready for EDA and modeling.


##  Exploratory Data Analysis (EDA)

### Target Variable Distribution
**Key Observations**
- Popularity distribution is right-skewed
- Most tracks fall into low to medium popularity
- Very popular tracks are rare

**Implication**
This imbalance increases prediction difficulty and penalizes models that fail to capture non-linear patterns.


### Correlation Analysis
**Findings**
- Artist popularity has the strongest positive correlation with track popularity
- Track duration shows weak correlation
- No severe multicollinearity detected

**Implication**
Linear models are safe to apply but may struggle with non-linear dependencies.


### Genre Frequency Analysis
**Observations**
- Dataset is genre-imbalanced
- Mainstream genres dominate

**Implication**
Predictions may be biased toward popular genres, limiting generalization to niche styles.


##  Feature Engineering (Critical Section)

### Feature Selection (Bias & Leakage Control)
Removed non-predictive and leakage-prone features:
- Track name
- Artist name
- Album identifiers
- Raw release date fields

**Rationale**
- Prevents memorization
- Improves generalization
- Ensures fair modeling


### Feature Creation – Track Age
```text
track_age = 2025 − release_year
