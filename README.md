# Over/Under Predictor

## File/Folder Breakdown
Notice that there are 2 different folders with models in them - model_with_weather_pca and model_with_weather_no_pca. As the name implies, one folder has models where PCA was applied to the feature space, and one folder has models where PCA was not applied. To write the report on our models, we used the results from the model_with_weather_pca folder. However, we thought it would be useful to leave it in there to see the difference in results between PCA-modified and non-modified models.

## Datasets
### Shared Datasets
These datasets are shared among all models. Both (1) and (2) were downloaded from the internet, and (3) was built using the data_collection.ipynb. That script took a really long time to run (a lot of GET requests), so we compiled the results into a dataset.
1. spreadspoke_scores.csv - This is the original dataset from Kaggle. Contains about 12,000 game statistics. Includes general game information (team names, date, score, spread, over/under, stadium, weather, etc.)
2. nfl_teams.csv - This dataset contains team information; mostly used to translate from the spreadspoke_scores dataset to a pro-football-reference.com team-specific URL.
3. all_game_stats.csv - This dataset contains team stats for every game in the spreadspoke_scores dataset. It is linked to that dataset using a game ID, consisting of the date (mmddyyyy) and the home team ID.
4. team_datasets
5.  unclean_data - This folder contains datasets that hold the game statistics for each individual team.
6.  clean_data - Largely the same data as unclean_data, just with columns moved around and renamed
7.  avg_data - Contains the 16-game rolling average for each team's stats. This is the data that will be joined with spreadspoke_scores to form our complete dataset.

### Model-Specific Datasets
These datasets were built with specific models in mind. For example, in the PCA folder, the datasets contain the principal components, while in the non-PCA folder it contains the original statistics (yards, turnovers, etc.). 
1. unclean_scores and clean_scores.csv - Almost the same as spreadspoke_scores.csv just with columns renamed, removed, and moved around
2. scores_w_avgs.csv - A combination of spreadspoke_scores.csv and the avg_data datasets.
3. {pca/non_pca}_weather_scores_with_avgs.csv - THe final dataset used for model generation. Contains the relevant statistics for that particular model type (i.e. PCA or non-PCA).
