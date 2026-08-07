# World-Cup-2026-Simulator

A Python-based simulation engine that models the complete 2026 FIFA World Cup format and estimates the probability of most likely knockout match=ups through the tournament.

The model combines Elo ratings, Poisson goal modelling, dynamic rating updates, and Monte Carlo simulation to generate thousands of possible tournament outcomes.

## Project Overview

The 2026 FIFA World Cup introduces a new 48-team structure consisting of:

- 12 groups of four teams
- 32 teams progressing to the knockout stage
- The top two teams from each group qualifying automatically
- The eight best third-placed teams also progressing
- A 104-match tournament from the group stage to the final

This project translates that tournament structure into a fully automated simulation model.

By default, the simulator runs 10,000 complete tournaments and calculates the most likely Knockout match-ups for the:

- Round of 32
- Round of 16
- Quarter-finals
- Semi-finals
- Third-place playoff
- Final

And the most likely teams to win the World Cup in these simulations

## Key Features:

-Full 48-team group-stage simulation
-Official-style 12-group tournament structure
-Qualification of the eight best third-placed teams
-Complete knockout bracket through to the final
-Elo-based team strength ratings
-Host-country rating adjustments
-Poisson-distributed goal simulation
-Penalty-shootout modelling
-Dynamic Elo updates after each match
-Margin of victory adjustment
-Configurable number of Monte Carlo simulations
-Stage-by-stage probability outputs
-Optional display of a single simulated tournament
-API-based third-place mapping retrieval with support for local caching

## Modelling Approach
1. Elo Ratings

Each team begins the tournament with an Elo rating representing its relative strength based on the pre tournament World Football Elo Ratings.
For a match between teams A and B, the model calculates their expected result using the difference between their ratings. Host nations receive an additional (small) rating bonus.

2. Expected Goals

The difference in Elo ratings is converted into an expected-goals value for each team.
A base expected-goals level is adjusted according to relative team strength, while minimum and maximum limits prevent unrealistic values.

3. Poisson Goal Simulation

The number of goals scored by each team is sampled from a Poisson distribution.
This allows stronger teams to have a higher expected scoring rate while preserving the uncertainty required for draws, upsets, and unexpected scorelines.

4. Group Standings

Teams are ranked within each group using tournament-style criteria, including:
Points
Goal difference
Goals scored
Additional tie-breaking logic where required
The top two teams in each group qualify automatically. The eight strongest third-placed teams are then selected and assigned to the Round of 32 bracket.
One of the last tie-breakers is yellow and red cards which have not been included in this simulation due to the complexity of including this feature.

5. Knockout Matches

Knockout matches cannot finish level. When required, the simulator models:
Penalty shootouts
Penalty shootouts are simulated using a configurable conversion probability based on real research.

6. Dynamic Elo Updates

After each match, Elo ratings are updated based on:
The expected result
The actual result
The stage of the tournament
The winning margin
This allows tournament performance to influence team strength as the competition progresses.

7. Monte Carlo Simulation

The complete tournament is repeated thousands of times.
The frequency with which each team reaches a particular stage is converted into an estimated probability.
For example:
Estimated probability of winning =
Number of simulated tournament wins / Total simulations

## Limitations

This model is a simplified representation of football matches. It does not currently account for every factor that may influence real tournament outcomes, including:

-Player injuries and suspensions
-Squad selection changes
-Managerial changes
-Tactical matchups
-Travel and recovery time
-Weather conditions
-In-match substitutions
-Recent player-level performance
-Correlation between scoring and game state

Elo ratings and model assumptions also influence the resulting probabilities. The outputs should therefore be interpreted as model estimates rather than predictions with certainty.

## Skills demonstrated 

This project demonstrates experience in:

-Python programming
-Probability and statistics
-Monte Carlo simulation
-Quantitative modelling
-Data processing with Pandas
-API integration
-Debugging and error handling
-Algorithm design
-Translating complex rules into code
-Communicating model assumptions and limitations

## Disclaimer

This project is intended for educational and analytical purposes. It is not affiliated with or endorsed by FIFA. Team ratings, tournament groups, and model outputs may change as new information becomes available.


## Installation

pip install -r requirements.txt

## Usage

Open `WorldCupSIMV5.ipynb` in Jupyter Notebook or JupyterLab
and run.

## Author 
Georgel Huja interests in quantitative analysis, markets, and data-driven modelling.
