# MLB_Player_OPS_Plus_Projections
By Michael Scognamiglio
## Table of Contents
1. Business Case 
1. Project Overview  
1. Repository Structure
1. Modeling Selection Process
1. Final Modeling and Analysis
1. Conclusions/ Next Steps
## Business Case
Players in Major League Baseball are under team control for their first six full seasons in the league. However, these contracts are not static or fixed in terms of salary compensation. More specifically, A player has no say in their salary in their first three seasons. However, a player's salary for the following three seasons is determined through arbitration.Arbitration is often a time consuming and stressful time for GMs. As player salaries can increase greatly relative to what they were making prior. Thus, the business case for this project is to offer general managers's a valuable tool (model) that they can use to project the offensive output of their players during their arbitration years. With this tool, A GM can lower a player's salary through the  arbitration process if they don't project well. The model could also be used to determine whether a player's offensive output will be sufficent or a GM should look for other players through a trade of Free Agency who will project better over those seasons. 
## Project Overview 
The data used for this project was offensive statistics for players on a season by season level. The data was collected using the sports reference API and was compiled into a large dataframe where the offensive stats were aggregated by player over their first three seasons. OPS+ was the target variable. OPS is on base percentage plus slugging percentage adjusted for each player's ballpark. OPS+ is a useful stat because it encapsulates a player's offensive output well and it is more standardized than regular OPS.  These aggregate stats were then used couplesd with some engineered features and then used to train some regression models. The primary evaulation metric was RMSE. Since this would be a regression model, the goal was to create projections as close as possible son RMSE gives us the best measure of how well our model is performing.
## Repository Structure 
