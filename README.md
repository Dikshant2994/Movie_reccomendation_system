Movie Recommendation System
___________________________________________________________-
Introduction:-
The Movie Recommendation System is a Python-based machine learning project that suggests movies to users based on their preferences. By using content-based filtering, the system finds movies similar to a selected title using text similarity techniques applied to movie metadata such as genre, cast, crew, and storyline.
________________________________________
Objective:-
The main goal is to help users discover movies they might enjoy by analyzing similarities between films.

Specific objectives include:-
•	Suggesting movies similar to a user-selected film.
•	Utilizing movie metadata to find similarities rather than relying on explicit ratings.
•	Delivering fast and relevant recommendations via an interactive web app.
________________________________________
Data Collection
•	Dataset sourced from TMDb (The Movie Database) public dataset containing:
o	Movie titles
o	Overview (plot summary)
o	Genres, keywords
o	Cast and crew information
•	Data is stored as CSV files (tmdb_5000_movies.csv & tmdb_5000_credits.csv).
________________________________________
Technologies & Libraries Used
•	Python – Programming language.
•	Pandas – Data handling and preprocessing.
•	NumPy – Array-based operations.
•	Scikit-learn – Vectorization and similarity computation.
•	NLTK – Text preprocessing.
•	Pickle – Model/data serialization for faster loading.
•	Streamlit – Web app framework for user interface.
________________________________________
Data Preprocessing
Steps followed before building the recommendation engine:
1.	Merging datasets – Movies and credits datasets combined on the title column.
2.	Feature selection – Retained relevant fields: movie_id, title, overview, genres, keywords, cast, crew.
3.	Text extraction – Converted JSON-like strings into plain text lists.
4.	Feature engineering –
o	Combined genres, keywords, cast, and crew into a single tags column.
o	Processed plot summaries (overview) into tokens.
5.	Text cleaning –
o	Lowercasing
o	Removing spaces between multi-word tokens (e.g., "Science Fiction" → "sciencefiction").
6.	Stemming – Reduced words to their root form (e.g., “running” → “run”) for better similarity matching.
________________________________________
Model Building
•	Vectorization:
o	Used CountVectorizer to convert tags text into a bag-of-words matrix.
o	Limited vocabulary to top 5000 words to improve performance.
•	Similarity calculation:
o	Computed cosine similarity between all movie vectors.
o	Stored similarity matrix for instant recommendations.
________________________________________
Recommendation Function:-
_________________________________________________
def recommend(movie):
    index = movies[movies['title'] == movie].index[0]
    distances = similarity[index]
    movies_list = sorted(list(enumerate(distances)), reverse=True, key=lambda x: x[1])[1:6]
    for i in movies_list:
        print(movies.iloc[i[0]].title)
_________________________________________________________
        
•	Finds the index of the selected movie.
•	Sorts all movies by similarity score.
•	Returns top 5 recommendations.
________________________________________
Streamlit Web App Features
•	Movie Selection Dropdown – Choose any movie from the dataset.
•	Recommendations Display – Shows top 5 similar movies.
•	Poster Fetching – Uses TMDb API to display movie posters alongside recommendations.
•	Interactive UI – Built with Streamlit for a simple, clean interface.
________________________________________
Challenges Faced & Solutions:-
•	Challenge: Handling missing or inconsistent metadata.
Solution: Dropped rows with essential missing values and standardized data format.
•	Challenge: Slow similarity computation for large datasets.
Solution: Precomputed similarity matrix and stored it with Pickle.
•	Challenge: Multi-word genre/keyword handling.
Solution: Removed spaces to treat multi-word phrases as single tokens.
________________________________________
Conclusion:-
The Movie Recommendation System successfully demonstrates a content-based filtering approach to personalized suggestions. It leverages text processing and similarity measures to recommend movies without user rating history, making it useful for cold-start scenarios. The Streamlit interface ensures an interactive, visually engaging experience for end users.

