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

#### Credits
- Historical FPL data up to 2023/24: [Fantasy-Premier-League by vaastav](https://github.com/vaastav/Fantasy-Premier-League)
