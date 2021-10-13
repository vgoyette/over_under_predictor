# over_under_predictor
This is a class project for CSE 40647 at the University of Notre Dame that involves building several machine learning models in order to predict the over/under result of NFL games..

There are several datasets involved with this project. Descriptions can be found below:

**spreadspoke_scores.csv**: The original dataset from Kaggle. This contains a lot of details we don't care about like the spread, stadium, and weather. However, it also serves as the main dataset that we base our work off of. It contains the date of a game, season, home team, away team, score of each team, and the over/under of each game.

**scores_w_avgs.csv**: This is the one we really care about. Contains >10000 NFL game results, along with the rolling 16-game average of each team's yards and turnovers (for the first model at least)

______________________________________________________
Following datasets were included for clarity and an understanding of how we went from our original dataset (spreadspoke_scores.csv) to our clean and shiny dataset (scores_w_avgs.csv).

nfl_team.csv: Another dataset from Kaggle. We only really want this dataset for its mappings of team names to Pro Football Reference IDs (i.e. it maps 'Arizona Cardinals' to 'CRD'), which is very useful later in data cleaning and integration.

team_data/unclean_data/\[team_id\]_unclean_data.csv: This contains the individual game stats for each game associated with that team ID. For example, if the team_id is CRD, then
the CRD_clean_data.csv contains the data for every game that the Arizona Cardinals (or their previously named franchise) have played. It includes the game id (combination of date
and home team), the date in string form, each team ID, and the total yards, passing and rushing yards, first downs, and turnovers of each team.

team_data/clean_data/\[team_id\]_clean_data.csv: Contains largely the same data as unclean_data, but with some cleanup done to it. Columns were renamed from the unclean data
to indicate which team stats we care about for this file, and which team's stats are the opposing team. For example, the unclean data for CRD contained their stats for each, but these stats were in different columns based on if CRD was the home or away team. Now, all of CRD's stats are in the same columns instead of potentially in a "Home_team_yds" or "Away_team_yds" column. The main reason for doing so was ease of use in Python and not much more. Having the generically "opposing team" stats also will allow us to incorporate averages against each team's defense rather than just averages for their offenses in a later model.

team_data/clean_data/\[team_id\]_avg_data.csv: Contains the rolling 16-game average stats for each team for associated game id. This will be the final form of our features. This is where the clean_data files come in: to calculate a team's rolling average for a particular statistic, we just have to call DataFrame\['stat_name'\].rolling(17) for a certain column. We'll then be able to easily incorporate these stats into the larger scores

scores.csv: Based on spreadspoke_scores.csv, but with extraneous columns removed and useful features like team_id's were added.
