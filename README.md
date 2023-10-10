# Spotify-ETL-Pipeline-with-Airflow

## Spotify ETL Process Repository

Welcome to the Spotify ETL (Extract, Transform, Load) process repository. This repository contains a set of scripts for extracting your recently played Spotify tracks, processing the data, and loading it into a SQLite database. The process includes an Apache Airflow DAG for scheduling the ETL tasks.

## Repository Structure

- **`dags` Folder**:
  - **`spotify_dag.py`**: This file contains the Airflow DAG definition (`spotify_dag`) responsible for orchestrating the Spotify ETL process. It schedules and executes the `run_spotify_etl` function from `spotify_etl.py`.
  
- **`dags` Folder**:
  - **`spotify_etl.py`**: This file contains functions for interacting with the Spotify API, performing data transformations, and loading data into the database.
  
- **`main.py`**: This file includes a standalone script for executing the Spotify ETL process without Airflow. It can be run independently for ad-hoc data extraction.

## Prerequisites

1. **Spotify API Token**: Obtain your Spotify API token from the [Spotify Developer Console](https://developer.spotify.com/console/get-recently-played/).

2. **Python Dependencies**: Ensure you have the necessary Python packages installed. You can install them using `pip`:
   ```
   pip install sqlalchemy pandas requests
   ```

## How to Use

### 1. Configure Spotify API Token

In `spotify_etl.py` and `main.py`, update the `TOKEN` variable with your Spotify API token obtained from the Spotify Developer Console.

### 2. Understanding the ETL Process

#### Code in `spotify_etl.py`:

- **`check_if_valid_data(df: pd.DataFrame) -> bool`**: Validates the data extracted from Spotify, checking for empty data, primary key violations, null values, and correct timestamps.

- **`run_spotify_etl()`**: Extracts recently played Spotify tracks using the Spotify API, transforms the data, and loads it into the SQLite database.

#### Code in `main.py`:

- The code in `main.py` performs the same ETL process as `spotify_etl.py` but as a standalone script without the need for Airflow.

### 3. Run ETL Process with Airflow (Optional)

1. Place `spotify_dag.py` and `spotify_etl.py` in your Airflow `dags` folder.
2. Configure the `TOKEN` variable in `spotify_etl.py` and `spotify_dag.py` with your Spotify API token.
3. Start your Airflow web server and scheduler to execute the DAG.

### 4. Run ETL Process without Airflow

Execute `main.py` using Python to run the ETL process without Airflow.

```bash
python main.py
```

### 5. Explore Your Data

Once the ETL process is executed, you can explore your Spotify listening history stored in the `my_played_tracks.sqlite` database. Utilize SQL queries to gain insights, create visualizations, or integrate the data into your applications.

## Important Notes

- **Security**: Keep your Spotify API token secure and do not expose it publicly.
- **Data Privacy**: Ensure you are compliant with Spotify's terms of use and respect user privacy while accessing and processing data.

Feel free to customize and expand upon these scripts to cater to your specific needs. Enjoy analyzing your Spotify listening history!
