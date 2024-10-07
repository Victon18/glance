```python
import requests
import pandas as pd

# Replace with your TMDB API key
API_KEY = 'your_api_key_here'
BASE_URL = 'https://api.themoviedb.org/3'

# Function to get popular movies
def get_popular_movies(api_key, page=1):
    url = f"{BASE_URL}/movie/popular?api_key={api_key}&language=en-US&page={page}"
    response = requests.get(url)

    if response.status_code == 200:
        return response.json()
    else:
        print(f"Error: {response.status_code}")
        return None

# Get popular movies
data = get_popular_movies(API_KEY)

if data:
    movies = data['results']
    # Create a DataFrame
    df = pd.DataFrame(movies)

    # Select relevant columns
    df = df[['id', 'title', 'popularity', 'release_date', 'overview']]

    # Save to CSV
    df.to_csv('popular_movies.csv', index=False)
    print("CSV file 'popular_movies.csv' created successfully.")
```
