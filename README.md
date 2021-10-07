# over_under_predictor
This is a class project for CSE 40647 at the University of Notre Dame that involves building several machine learning models in order to predict the over/under result of NFL games..

There are several datasets involved with this project. Descriptions can be found below:

spreadspoke_scores.csv: The original dataset from Kaggle. This contains a lot of details we don't care about like the spread, stadium, and weather. However, it also serves as the main
dataset that we base our work off of. It contains the date of a game, season, home team, away team, score of each team, and the over/under of each game.

nfl_team.csv: Another dataset from Kaggle. We only really want this dataset for its mappings of team names to Pro Football Reference IDs (i.e. it maps 'Arizona Cardinals' to 'CRD'),
which is very useful later in data cleaning and integration.

team_data/unclean_data/<\team_id>\_unclean_data.csv: This contains the individual game stats for each game associated with that team ID. For example, if the team_id is CRD, then
the CRD_clean_data.csv contains the data for every game that the Arizona Cardinals (or their previously named franchise) have played. It includes the game id (combination of date
and home team), the date in string form, each team ID, and the total yards, passing and rushing yards, first downs, and turnovers of each team.

team_data/clean_data/<\team_id>\_clean_data.csv: Contains largely the same columns as unclean_data, but with some cleanup done to it. Columns were renamed from the unclean data
to indicate which team stats we care about for this file, and which team's stats are the opposing team.

team_data/clean_data/<team_id>_avg_data.csv: Contains the rolling 16-game average stats for each team for associated game id. This will be the final form of our features.

scores.csv
