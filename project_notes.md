Decision 1:

Prediction target:
Predict the winner of NFL regular season games

Reason:
Simplest classification problem

Decision 2:

Training data:
2015-2024 data

Reason:
Modern NFL rules and playstyle
Enough games for training

Decision 3:

Raw data:
games.csv
stats_team_week_YYYY.csv

Reason:
Holds game outcomes as well as the stats I will use to predict said outcomes

Machine Learning Dataset

Column | Description:

season | NFL season
week | week being predicted
home_team | home team of game being predicted
away_team | away team of game being predicted
home_avg_points | average points scored by home team
away_avg_points | average points scored by away team
home_pass_avg | average passing yards for home team
away_pass_avg | average passing yards for away team
home_rush_avg | average rushing yards for home team
away_rush_avg | average rushing yards for away team
home_rest | days of rest before game for the home team
away_rest | days of rest before game for the away team
home_avg_turnovers | turnovers made by home team
away_avg_turnover | turnovers made by away team
home_penalties_avg | penalties administered per game for the home team
away_penalties_avg | penalties administered per game for the away team
home_def_avg_pass | average amount of passing yards given up by the home defense
away_def_avg_pass | average amount of passing yards given up by the away defense
home_def_avg_rush | average amount of rushing yards given up by the home defense
away_def_avg_rush | average amount of rushing yards given up by the away defense
home_avg_points_allowed | average amount of points given up by the home defense
away_avg_points_allowed | average amount of points given up by the away defense
home_def_sacks_per_game | number of sacks by defense up until that week
away_def_sacks_per_game | number of sacks by defense up until that week
home_def_int_per_game | number of interceptions by defense up until that week
away_def_int_per_game | number of interceptions by defense up until that week
home_fg_pct | home field goal percentage
away_fg_pct | away field goal percentage
home_win | Target(1 if win, 0 otherwise)

Function: retrieve_stats(season, week, team)
Purpose: to get all previous games from that season that the team has played
Returns: data frame that has the previous games up until that week of the season

Function: calculate_team_stats(games)
Purpose: calculate all team stats needed for ML dataset
Returns: dictionary of the team stats needed

Columns for what will be needed for each team stat (parenthesis will tell what table the data will come from):
home_avg_points: home_score(games)
away_avg_points: away_score(games)
home_pass_avg: passing_yards(stats_team)
away_pass_avg: passing_yards(stats_team)
home_rush_avg: rushing_yards(stats_team)
away_rush_avg: rushing_yards(stats_team)
home_avg_turnovers: passing_interceptions, sack_fumbles_lost, rushing_fumbles_lost, receiving_fumbles_lost(all from stat_team)
away_avg_turnovers: passing_interceptions, sack_fumbles_lost, rushing_fumbles_lost, receiving_fumbles_lost(all from stat_team)
home_penalties_avg: penalties(stat_team)
away_penalties_avg: penalties(stat_team)
home_def_avg_pass: passing_yards(stat_team)(stats from opposing team depending on if the team is home or away)
away_def_avg_pass: passing_yards(stat_team)(stats from opposing team depending on if the team is home or away)
home_def_avg_rush: rushing_yards(stat_team)(stats from opposing team depending on if the team is home or away)
away_def_avg_rush: rushing_yards(stat_team)(stats from opposing team depending on if the team is home or away)
home_avg_points_allowed: away_score(games)
away_avg_points_allowed: home_score(games)
home_def_sacks_per_game: def_sacks(stat_team)
away_def_sacks_per_game: def_sacks(stat_team)
home_def_int_per_game: def_interceptions
away_def_int_per_game: def_interceptions
home_fg_pct: fg_made, fg_att
away_fg_pct: fg_made, fg_att