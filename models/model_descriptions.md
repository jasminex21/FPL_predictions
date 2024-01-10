### ML Models
- rf_regressor_model: Random Forest Regressor model that aims to predict the *exact* number of points a player will score in the upcoming gameweek. Results in low variance, around ~20%. 
- rank_rf_regressor_model: Random Forest Regressor model that aims to predict the rank of the amount of points a player will score in the upcoming gameweek. As in, all players that GW are ranked by the number of points they score (the more the points, the higher their rank), and a rolling average over the previous 3 weeks is computed such that it can be used as a predictor. Results in moderate variance, just over 50%.
    - The model tries to predict the exact rank; however, if the aim of this project is to determine, say, the top scorer in a 15-player lineup, this is not necessary. Hence, I wanted to determine how well my model was able to order a random sample of 15 players from a single GW by the actual points they earned. This was done for every (GW, season) combination, and Kendall's tau correlation coefficient was computed. Kendall's tau is a measure of the ordinal association between variables, without consideration of scale/magnitude. The mean of all correlation coefficients was around 53%.
      
      ![image](https://github.com/jasminex21/FPL_predictions/assets/109494334/0ee80764-c3b0-4cab-ab37-c6b11b5b04c0)

      Above: `points_rank` is the actual rank achieved by the player that GW. `prediction` is the rank prediction made by the model, based on various rolling and general statistics.
  

