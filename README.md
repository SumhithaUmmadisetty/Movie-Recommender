# Movie-Recommender

## Overview
This project implements a simple movie recommendation system using the k-Nearest Neighbors (k-NN) algorithm. The dataset used is the **MovieLens 100K** dataset, which contains user ratings for movies. The system recommends movies to users based on the preferences of similar users.

## Dataset
The code loads data from the MovieLens 100K dataset:
- **Ratings file (`u.data`)**: Contains user ratings for movies.
- **Movies file (`u.item`)**: Contains movie titles and corresponding movie IDs.

## Installation & Requirements
Ensure you have the required Python libraries installed before running the code:
```bash
pip install pandas scipy scikit-learn
```

## Code Explanation
### 1. Import Required Libraries
The following libraries are used:
- `pandas`: For data manipulation and loading CSV files.
- `scipy.sparse`: To create a sparse matrix representation of user ratings.
- `sklearn.neighbors`: For implementing the k-NN algorithm.

### 2. Load and Preprocess Data
- The ratings and movies data are read using Pandas.
- The datasets are merged on `movieId` to associate ratings with movie titles.
- Duplicate ratings (same user rating the same movie multiple times) are identified and removed to maintain data integrity.
- A **user-movie rating matrix** is created using `pivot()`, with users as rows, movies as columns, and ratings as values.
- Missing ratings are filled with 0 to create a sparse matrix.

### 3. Implement k-Nearest Neighbors (k-NN)
- A sparse matrix representation is created using `csr_matrix` to optimize memory usage.
- A k-NN model is trained using **cosine similarity** as the distance metric.

### 4. Movie Recommendation Function
The function `recommend_by_user(user_id, n=5)` works as follows:
1. Retrieves the input user's rating vector from the matrix.
2. Finds the `n` most similar users using k-NN.
3. Averages the ratings of similar users to recommend the top `n` movies.

### 5. Example Usage
To get movie recommendations for a specific user, call:
```python
print("Recommendations for user 5:")
print(recommend_by_user(5))
```

## Future Improvements
- Implement content-based filtering using movie genres.
- Use collaborative filtering techniques like **Matrix Factorization (SVD, ALS)**.
- Add a web interface for user interaction.


