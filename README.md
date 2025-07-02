# Netflix-Show-Clustering-Group
It groups similar shows using K-Means based on genre, rating, and duration. Tech Stack: Python, Pandas, Scikit-learn, Seaborn

## Data Preprocessing

🔹 1. Understand Your Raw Dataset
Start by checking:

Are there any missing values?

Are column names and types as expected?

How is genre represented? (Single/multiple genres per show?)

What units is duration in? (minutes? seasons?)

Use .info(), .head(), .describe(), .isnull().sum() to inspect the data.

🔹 2. Handling Missing Data
Drop rows or fill missing values based on their importance.

For instance, shows with no duration or rating may be dropped.

Genres could be filled with “Unknown” if needed.

🔹 3. Preprocessing Features
✅ Genre (Categorical, possibly multi-label)
If a show has multiple genres (e.g., "Action, Drama"):

Split the genre string.

Use multi-hot encoding (e.g., one row: Action = 1, Drama = 1, Romance = 0, etc.)

Use str.get_dummies() or manual one-hot logic.

✅ Rating (Numerical or Categorical)
If it's a numeric rating (e.g., 7.8), normalize it.

If it’s a category (like “TV-MA”, “PG-13”), one-hot encode or assign ordinal values based on strictness.

✅ Duration (Text or Numeric)
Clean it:

E.g., “90 min”, “1 Season”, “2 Seasons” — extract the number.

Decide how to treat movies vs. series. You may convert seasons to minutes roughly, or use different feature encodings for them.

🔹 4. Normalization/Scaling
K-Means is sensitive to scale. After combining your processed features:

Normalize numeric columns (e.g., MinMaxScaler or StandardScaler from Scikit-learn).

This avoids features like duration dominating others.

🔹 5. Final Feature Matrix
Combine your numeric and encoded categorical data into a single DataFrame or NumPy array.

This will be your input for the K-Means algorithm.
