# Book Recommender System

## Introduction
This is a book recommender system based on collaborative filtering. It suggests books to users based on their past ratings and reviews, leveraging the wisdom of the crowd to make recommendations.

## Requirements
This system requires the following Python libraries:
- `numpy` as `np`
- `pandas` as `pd`
- `seaborn` as `sns`
- `matplotlib.pyplot` as `plt`

Make sure to have these libraries installed in your Python environment before running the system.

## Collaborative Filtering System
The collaborative filtering system operates as follows:

1. **Filter Users**: Users who have provided over 200 ratings/reviews are considered for recommendations. This threshold helps ensure that recommendations are based on users who have actively engaged with the system.

```python
x = ratings_with_name.groupby('User-ID').count()['Book-Rating'] > 200
idx = x[x].index
filtered_rating = ratings_with_name[ratings_with_name['User-ID'].isin(idx)]
```

2. **Filter Books**: Books with over 50 reviews are considered as popular books. This step helps in focusing on books that have received a significant amount of feedback from users.

```python
y = filtered_rating.groupby('Book-Title').count()['Book-Rating'] > 50
famous_books = y[y].index
```

3. **Final Ratings**: The ratings dataset is filtered to include only the ratings of famous books by active users.

```python
final_ratings = filtered_rating[filtered_rating['Book-Title'].isin(famous_books)]
```

## Usage
To use the book recommender system, ensure you have the required libraries installed and import them into your Python environment. Then follow the collaborative filtering steps outlined above to filter your dataset and obtain recommendations.

## Note
- Adjust the thresholds (200 ratings for users and 50 reviews for books) based on the specific requirements and characteristics of your dataset.
- This system assumes the existence of a dataset named `ratings_with_name` containing user ratings with associated book titles. Adjust variable names accordingly if your dataset differs.
- Ensure your dataset is preprocessed and structured appropriately for compatibility with the provided code.

## References
- [NumPy Documentation](https://numpy.org/doc/)
- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [Seaborn Documentation](https://seaborn.pydata.org/)
- [Matplotlib Documentation](https://matplotlib.org/stable/contents.html)
