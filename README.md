# Predicting FPL Player Scores

An exploration of the capabilities of machine learning in the prediction of player points in Fantasy Premier League (FPL). To do so, I am using historical player statistics from games from 2016/17 to halfway through the current season, 2023/24. 

### Predictor features
Features are primarily based on rolling averages of statistics from the prior three games; for example, minutes played, whether the games were won, and so on. FPL-specific features (all rolling over the last 3 games) include transfer balance (if lots of people are taaking a player out of their team, that may indicate poor performances or injuries), ICT index (a summary statistic of a player's Influence, Creativity, and Threat), points scored, etc. And finally, general information such as the player's position, club, opposition club, and home/away status is also considered.

### Models
As of now, I have investigated two means: 

1. Predicting the *exact* number of points
The unpredictability of football, and sports in general, makes this a challenging proposition.

2. Predicting the general amount of points a player will score, ranked compared to all other players
One of the main use cases of this project (for me) is to predict which player out of the 15 players in my team would make the ideal captain selection (the captain's points are doubled for the given gameweek). As such, it would be useful to have an inkling of who is more likely to score the most points, even if the exact number of points is unknown.
  - The average Spearman's correlation coefficient for a random 15-player team per (GW, season) combination was close to 66%, implying that when the exactness of the ranks is not considered, the predicted orders match up fairly well with the actual orders. However, a commonly-occurring issue that bogs down the correlation coefficient is consistent overestimation of point ranks, which in turn affects the ordering. This could in part be due to the inability to account for player injuries - while FPL managers can see player injury and availability information, this does not seem to be available in the API.

### TODO
- Create user interface (web application) where users authenticate using their FPL login information, and are then able to access predictions
- For some players, filling in position and club didn't work out because they are, for some reason or another, not in the original full dataset. It wasn't a good idea to fill them based on what they were in the original data anyways - it was mainly just a temporary measure at the time that I now have to fix. It would probably be most accurate for me to search up each player (automated using selenium), but that does take a while. I may consider creating a team-position-correspondance at the beginning of the season and updating it after the transfer window? Another issue is that certain names do not match exactly with what is searched in the FPL player database, but it does work if I paste the full name into the search bar directly.
- Goes without saying, but see if you can improve the model predictivity in any way. Take a better look at the features.

#### Credits
- Historical FPL data up to 2023/24: [Fantasy-Premier-League by vaastav](https://github.com/vaastav/Fantasy-Premier-League)
