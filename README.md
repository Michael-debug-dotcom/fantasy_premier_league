# Fantasy Premier League

## Project Overview:
This Python script retrieves player data from the Fantasy Premier League (FPL) API, processes it, and uses machine learning (RandomForestRegressor) to predict player performance. It also identifies the top players for each position and rates Premier League teams based on recent performance and injuries. The project involves API interaction, data merging, model training, and evaluation.

## Step-by-Step Breakdown:
### Libraries and Setup:

The script imports libraries: requests for API calls, pandas for data manipulation, RandomForestRegressor for machine learning, and others for model evaluation.
A helper function get_fpl_data(endpoint) fetches data from FPL's API endpoints.
### Data Extraction:

General Info: Using the "bootstrap-static" endpoint, the script extracts general FPL data like players, teams, and positions. These are converted into Pandas DataFrames.
Player History: The get_player_history(player_id) function fetches each player's match history from the "element-summary" endpoint. All player histories are merged into a single DataFrame player_hist_df.
### Data Enrichment:

The script merges player data with team performance stats (average goals scored/conceded) and injury data.
Positions (e.g., Goalkeeper, Midfielder) are encoded numerically for model training.
### Feature Engineering:

The dataset is prepared for machine learning by selecting relevant features (minutes, goals, assists, etc.).
Data is split into training (pre-24/25) and test sets using train_test_split.
### Machine Learning:

A RandomForestRegressor model is trained to predict players’ total points using the historical data.
Model evaluation is performed using mean_squared_error and r2_score.
### Top Player Recommendations:

The recommend_top_players() function identifies the top 5 players in each position (Goalkeeper, Defender, Midfielder, Forward) by predicting their future performance based on the trained model.
### Team Rating:

The calculate_team_rating() function ranks teams based on their recent performance (average goals scored vs. conceded) and injury count, outputting the top 5 teams.
### Outputs:
Top 5 Players for each position (Goalkeeper, Defender, Midfielder, Forward).
Top 5 Teams based on recent performance.
How to Use:
Run the script to fetch data from FPL API.
Train the machine learning model using historical player data.
Use the model to predict and recommend top-performing players.
View team ratings based on their performance and injury status.

Requirements:
Python 3.x
Libraries: requests, pandas, sklearn
