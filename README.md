# MLB_Player_OPS_Plus_Projections
By Michael Scognamiglio
## Table of Contents
1. Business Case 
1. Project Overview  
1. Repository Structure
1. Modeling and Clustering Processes
1. Final Modeling and Analysis
1. Conclusions/ Next Steps
## Business Case
Players in Major League Baseball are under team control for their first six full seasons in the league. However, these contracts are not static or fixed in terms of salary compensation. More specifically, A player has no say in their salary in their first three seasons. However, a player's salary for the following three seasons is determined through arbitration.Arbitration is often a time consuming and stressful time for GMs. As player salaries can increase greatly relative to what they were making prior. Thus, the business case for this project is to offer general managers's a valuable tool (model) that they can use to project the offensive output of their players during their arbitration years. With this tool, A GM can lower a player's salary through the  arbitration process if they don't project well. The model could also be used to determine whether a player's offensive output will be sufficent or a GM should look for other players through a trade of Free Agency who will project better over those seasons. 
## Project Overview 
The data used for this project was offensive statistics for players on a season by season level. The data was collected using the sports reference API and was compiled into a large dataframe where the offensive stats were aggregated by player over their first three seasons. OPS+ was the target variable. OPS+ is on base percentage plus slugging percentage adjusted for each player's home ballpark. OPS+ is a useful stat because it encapsulates a player's offensive output well and it is more standardized than regular OPS.  These aggregate stats were then used coupled with some engineered features and then used to train some regression models. The primary evaulation metric was RMSE. Since this would be a regression model, the goal was to create projections as close as possible to actusl OPS+ values.Thus, RMSE gives us the best measure of how well our model is performing.
## Repository Structure 
All visulaizations used for both this Readme and the presenation pdf can be found in the pngs folder.
 The pdf 'MLB_Player_OPS+_Projections' contains the  pdf presentation of this project.
 
Please see the goals of the code contained in the notebooks below. 
 ### Master_notebook.ipynb
  - Collect mlb player offensive data from 2000-2020 using sports reference API  models
  - Compile all player offensive data into large dataframe for EDA,analysis,modeling
  - Clean and prepare Dataframe for analysis and Modeling
  - Conduct EDA and Stat Testing to gain more insight into data
  - Use Clustering as a feature engineering technique to help improve regression models
  - Build models with different paramters to determine best performing model
  - Select Final Model and conduct Model analysis
 ### Modeling_Adjustments.ipnyb
 - Contains the code to build a baseline model
 - Baseline Model performance used as a reference when evaluating other models
  
## Modeling and Clustering Processess
For Modeling, It was decided that four different types of models would be ideal. The belief was that four distinct types of models and varying hyper parameters of those models would lead to an ideal model in terms of performance. The four different models that were used to create these multi year projections were a Simple Linear Regression Model, Lasso Model, Ridge Model, and a Simple Neural Network Model. A baseline model was constructed as well for reference. The baseline model achieved a RSME of 21.0 and MAE of 16.4. The Linear Regression achieved a mean absolute error of about 15 points and a root mean square error of about 19 points. The Lasso model achieved similar results with a mean absolute error of about 15.1 points and 19.3 points for root mean square error.  The Ridge Model performed nearly identically to the Lasso Model achieveing 15.1 and 19.3 for mae and rsme respectively. The Neural Network Model surprisingly performed the poorest. As it achieved an rmse of 22.5. Before these models were trained on data, a cluster model was applied to the dataset to assign players to a cluster. The goals of this clustering was to provide more info the models could use to improve predictions. Please see the images below to see how the clusters were created and how well players in each cluster have performed.  

![Image](https://raw.githubusercontent.com/Scogs25/MlB_Player_OPS_Plus_Projections/main/pngs/Player_Clusters.png)
![Image](https://raw.githubusercontent.com/Scogs25/MlB_Player_OPS_Plus_Projections/main/pngs/Clusters_1980_onward.png)


## Final Modeling and Analysis
 Due to it's best performance, the simple Linear Regression was selected as the final model. It achieved the best mean abosoulte error of about 15 points and more importantly it achieved the best rmse of about 19 points. After looking at a residuals plot, the variance in error was clearly random so I was not concerned with homoscedasticity. 
  ![Image](https://raw.githubusercontent.com/Scogs25/MlB_Player_OPS_Plus_Projections/main/pngs/Residuals_Plot_for_4th_Year_Projections.png)
 
 The coefficents of this final model were analyzed to determine what offensive stats matter the most and should be looked at further.
 
 ![Image](https://raw.githubusercontent.com/Scogs25/MlB_Player_OPS_Plus_Projections/main/pngs/Feature_Coefficients_4th_Season_Projections.png)

As you can see above, slugging percentage played the largest role in projecting a player's 4th year OPS+. Slugging was then looked at further to see if any further insights could be found. 
 ![Image](https://github.com/Scogs25/MlB_Player_OPS_Plus_Projections/blob/main/pngs/How_Past_Slugging_Performance_Influences_Future_Offensive_Output.png)
 
 As you can see above players whose slugging in their first three season was elite (top 25% of players) performed significantly better than the general population of players. Please note that an OPS+ is conisdered average so the average of the elite group was 22% better than average. A one sample means test confirmed that
 the differnce between these two groups is statistically siginificant.
 
 ## Conclusions and Next Steps
  Through this poject, Please see the following insights that GM's should look at closely when evaulating players. 
  1. Look for players who have elite slugging percentage, we found players belonging to this group performed on average 22% better than an average player
  1. Look closely at a players average OPS+ over their first three seasons, We found a R^.2 of .55 between average OPS+ and a player's OPS+ in their fifth season
  1. Prioritize Power Hitters above all else, we found a small differnce between hitters who can hit for both power and contact and hitters who only hit for power. However, we found a big differnce in OPS+ between hitters who can only hit for contact versus hitters who only hit for power. 
  
 ![Image](https://raw.githubusercontent.com/Scogs25/MlB_Player_OPS_Plus_Projections/main/pngs/5th_Season_OPS%2B_projections.png)
 ![Image](https://raw.githubusercontent.com/Scogs25/MlB_Player_OPS_Plus_Projections/main/pngs/How_Different_Types_of_Hitters_Perform_in_6th_Season.png)
  
  As for next steps, I would like to apply what I have learned to building a model to project free agents' future offensive production. This model could be used with the arbitration projections to give General Manager's even more information to make decisions on roster decisions. 
