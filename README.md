# anime_rec_systems

# Content-Based Model
1. Data Loading and Preprocessing
    The code loads two datasets: anime.csv (containing anime information) and rating.csv (containing user ratings)

It calls a preprocessing() function (not shown here) to clean and prepare the data

2. Feature Engineering (Genre One-Hot Encoding)
    Extracts all unique genres from the anime data (splitting comma-separated genre lists)

    Creates a feature matrix where:

        Each row represents an anime

        Each column represents a genre

        Values are 1 if the anime has that genre, 0 otherwise

    Handles edge cases (empty genres, NaN values) by adding dummy features if needed

3. Feature Scaling
    Standardizes the features using StandardScaler (mean=0, variance=1)

    This helps with the cosine similarity calculations later

4. Data Splitting
    Splits the rating data into 80% training and 20% test sets

5. Similarity Matrix Calculation
    Computes a cosine similarity matrix between all anime based on their genre features

    Cosine similarity measures the angle between feature vectors (1=identical, 0=orthogonal, -1=opposite)

6. Rating Prediction Function
    The predict_rating() function predicts how a user would rate an anime by:

    Finding the anime's position in the feature matrix

    Looking at other anime the user has rated

    Calculating a weighted average of those ratings, weighted by genre similarity

    If no similar anime are found, returns the user's average rating

7. Model Evaluation
    Makes predictions for all user-anime pairs in the test set

    Calculates RMSE (Root Mean Squared Error) between predicted and actual ratings

    RMSE measures prediction accuracy 

