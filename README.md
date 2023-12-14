# sds-final-project
## Overview of the Package
Our group has developed a song recommendation package utilizing the Spotipy package and the Spotify track dataset. The package consists of two classes: SpotifyDataProcessor and song. The SpotifyDataProcessor class provides access to Spotify song track data from users. The song class employs various functions to generate song recommendations based on the danceability and energy attributes of songs. The reason for creating this package is to deliver personalized and relevant song suggestions to users based on the attributes(danceability and energy) of the songs they have recently added to their liked song list. Our package provided a foundation for developers interested in developing more complex song recommendation algorithms. The package could also fulfill the needs of users seeking additional song recommendations based on their recently liked tracks.

## `SpotifyDataProcessor` Class

### Overview

The SpotifyDataProcessor class is designed to provide easy access to a user's Spotify account, specifically retrieving information about their top 10 loved songs.

### Example Usage:


### Attributes:
- `client_id`: Spotify client ID.
- `client_secret`: Spotify client secret.
- `redirect_uri`: The redirect URI after the user grants/denies permission.
- `scope`: The range of data that you want the class to access.

### Methods:
`authenticate_spotify()` <br>
Authorizes the user's Spotify account. <br>
- Return: 
    a class instance for accessing the user's Spotify account.

`get_top_10_songs(sp)` <br>
Retrieves the user's top 10 loved songs and returns a DataFrame. <br>
- Parameters:
    sp: A class instance for accessing the user's Spotify account.

- Return: 
    a DataFrame of the user's top 10 loved songs.

`process_spotify_data()` <br>
Retrieves the user's top 10 loved songs and returns a DataFrame. <br>
- Return: 
    a DataFrame of the user's top 10 loved songs.

## `song` Class

### Overview

The `song` Class recommends songs based on genre, danceability, and energy filters.

### Example Usage:
new_song = song("To Begin Again", "Ingrid Michaelson;ZAYN") <br>
new_song.music_recommendation()

### Attributes:

- `dataset (dict)`: The Spotify tracks dataset.
- `song_name (str)`: The name of the target song.
- `song_artist (str)`: The artist of the target song.
- `song_danceability (float)`: The danceability score of the target song.
- `song_energy (float)`: The energy score of the target song.
- `song_loudness (float)`: The loudness score of the target song.
- `selected_genre (str)`: The randomly selected genre for filtering.

### Methods:

`__init__(self, song_name, song_artist)` <br>
Initializes a song object with specified song name and artist.

- Parameters:
    song_name (str): The name of the target song.
    song_artist (str): The artist of the target song.

`genre_mask(self, df_music) -> pd.DataFrame` <br>
Applies a genre mask to the DataFrame based on the selected genre.

- Parameters:
    df_music (pd.DataFrame): The music DataFrame.

- Returns:
    pd.DataFrame: DataFrame filtered by genre.

`danceability_mask(self, df_music, df_genre) -> pd.DataFrame` <br>
Applies a danceability mask based on the song's danceability.

- Parameters:
    df_music (pd.DataFrame): The music DataFrame.
    df_genre (pd.DataFrame): DataFrame filtered by genre.

- Returns:
    pd.DataFrame: DataFrame filtered by danceability.

`energy_mask(self, df_music, danceability_df) -> pd.DataFrame` <br>
Applies an energy mask based on the song's energy.

- Parameters:
    df_music (pd.DataFrame): The music DataFrame.
    danceability_df (pd.DataFrame): DataFrame filtered by danceability.

- Returns:
pd.DataFrame: DataFrame filtered by energy.

`music_recommendation(self) -> None` <br>
Recommends a random song based on genre, danceability, and energy filters. Prints the recommended song and artist. <br>
- No parameters.
