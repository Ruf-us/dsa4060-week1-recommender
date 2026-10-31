# DSA 4060 Week 1 Popularity Recommender

## Student
- **Name:** Rufinus Ogutu
- **Student number:** 670827

## Project overview
This project explores MovieLens user-item ratings and builds two non-personalized movie recommendation baselines: a minimum-rating threshold popularity recommender and a Bayesian weighted-rating recommender. It provides a transparent, non-personalized baseline for movie recommendations, suitable for addressing cold-start scenarios for new platform visitors.

## Dataset
- **Source:** [MovieLens Latest Datasets (small)](https://grouplens.org/datasets/movielens/) provided by GroupLens Research.
- **Files Used:** `movies.csv` (contains `movieId`, `title`, `genres`) and `ratings.csv` (contains `userId`, `movieId`, `rating`, `timestamp`).
- **Date Accessed:** October 2026.

## Methods
1. **Rating-count and average-rating exploration:** Initial data validation, missing value and duplicate checks, and matrix sparsity analysis.
2. **Minimum-rating popularity baseline:** Filtering candidates using a strict minimum threshold ($MIN\_RATINGS = 50$) and sorting by average rating.
3. **Weighted-rating baseline:** Calculating Bayesian weighted scores using the overall mean rating ($C$) and the 90th percentile threshold ($m$) to adjust for rating volume.

## How to run
1. Clone the repository:
   ```bash
   git clone https://github.com/YOUR-USERNAME/dsa4060-week1-recommender.git
   cd dsa4060-week1-recommender
   ```
2. Install packages:
   ```bash
   pip install -r requirements.txt
   ```
3. Place the required CSV files in `data/` if they are omitted.
4. Open `notebooks/week1_popularity_recommender.ipynb`.
5. Run all cells from top to bottom.

## Key findings
- **Dataset Scale:** The MovieLens small dataset comprises 100,836 ratings across 9,742 movies from 610 unique users, exhibiting a matrix sparsity of approximately 98.31%.
- **Rating Behavior:** The rating distribution is skewed towards positive feedback, with integer ratings (4.0 and 3.0) being the most common.
- **Baseline Performance:** Raw average rating is unreliable as it promotes obscure movies with single $5.0$ ratings. The $50$-rating cutoff filters out low-engagement titles, while the Bayesian weighted score offers the most statistically robust ranking by smoothing low-volume items toward the global mean ($C \approx 3.501$).

## Limitations
- **Lack of Personalization:** The recommender is non-personalized; every user receives the exact same Top 10 list regardless of individual taste or historical preferences.
- **Popularity Bias:** Mainstream blockbusters dominate the rankings, creating a feedback loop that disadvantages niche, independent, or foreign movies.
- **Cold-Start Problem:** New movies with zero or very few ratings cannot be recommended until they accumulate sufficient user interactions.
