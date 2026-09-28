# DSA 4060 — Week 2 Practical Task: Recommendation Data and Popularity Baselines

## Overview

This repository contains the completed Week 3 practical task for DSA 4060. The task works with a movie ratings dataset to practice the core groundwork of recommender systems: loading and inspecting interaction data, cleaning it, exploring it, building a user–item interaction matrix, measuring its sparsity, and building a simple popularity-based recommender.

## Repository Contents


`DSA_4060_Week2_Movie_Ratings.ipynb` The completed Jupyter Notebook with all analysis, code, and Markdown explanations. 
`ratings.csv` The raw movie ratings dataset provided for the task (`user_id`, `movie_id`, `movie_title`, `rating`, `timestamp`). 
`top_10_recommended_movies.csv` Output of the popularity-based recommender: the top 10 movies (with at least 10 ratings) ranked by average rating. 
`README.md` This file. 

## Task Summary

1. **Load and inspect**  Loaded `ratings.csv` (509 raw rows), inspected the first 10 records, checked dimensions/data types, and identified missing values, duplicate rows, and out-of-range ratings.
2. **Clean the dataset**  Removed 3 duplicate records, removed rows with a missing `user_id` or `movie_id`, and removed ratings outside the expected 1–5 scale, leaving **500 clean rows**.
3. **Explore the interaction data**  Calculated total ratings, unique users, unique movies, the most active user, the most-rated movie, and the overall average rating (~3.45 out of 5).
4. **User–item interaction matrix** Built a matrix of **50 users × 24 movies**, with ratings in the cells and blanks where a user hasn't rated a movie.
5. **Sparsity**  Calculated the sparsity of the matrix using:

   Sparsity = 1 (Observed ratings) / (Number of users × Number of movies)

   This came out to roughly **0.58 (≈58%)**, meaning most user–movie combinations have no rating at all — a typical, expected trait of real-world rating data.
6. **Popularity-based recommender** — For each movie, computed the average rating and number of ratings, then selected the top 10 movies with at least 10 ratings, ranked by average rating. Results are saved in `top_10_recommended_movies.csv`.


## Key Findings

- The raw dataset had a small number of data-quality issues (2 rows with a missing ID, 3 duplicate rows, and 3 ratings outside the 1–5 scale), all of which were removed during cleaning.
- The cleaned interaction matrix is fairly sparse (~58% empty), which is expected since each user only rates a small subset of all available movies.
- A simple popularity baseline (average rating, filtered to movies with at least 10 ratings) is enough to produce a reasonable "most people like these" recommendation list, but it cannot personalize to individual tastes and tends to favor a fixed set of already-popular movies.
