# Project 2: March Madness Prediction Model
### October 1, 2026

## Problem Definition

This model addresses the extent to which a regression model can accurately predict a team’s numerical tournament depth using adjusted offensive efficiency, adjusted defensive efficiency, power rating (chance of beating an average D1 team), wins above bubble, and seed in the 2025 March Madness Tournament. The target variable is labeled “POSTSEASON” and is the number of wins a team gets in the tournament. Many people, whether officially or recreationally, try to predict the winner of March Madness, so models like this can help with these predictions. 

## Background and Context


## Data Description

The data for this project came from the site Kaggle and is a College Basketball Dataset. The link is at the bottom of the page under Sources. The original dataset has 4249 rows and 24 columns. Each row represents a college basketball team, with the columns representing different stats and information about the team. The dataset was shortened from the original dataset for this model. It was limited to only the 2025 season and to the feature columns. For this model, the target variable is the column “POSTSEASON”.  The variables for this model are team name (TEAM), the year (YEAR), wins above bubble (WAB), adjusted offensive efficiency (ADJOE), adjusted defensive efficiency (ADJDE), power rating (BARTHAG), and seed (SEED). Data collection had limitations because teams that did not make the tournament did not receive a seed. 

## Data Understanding and Exploration

We can look at some of the summary statistics to see what our data reveals. ADJDE and BARTHAG are both negative, suggesting they predict fewer postseason wins, while ADJOE, WAB, and SEED are positive, suggesting they predict more postseason wins. All features have p-values below 0.05, meaning they are significant. The R-squared value is 0.696, meaning the features explain almost 67% of the variance in the POSTSEASON variable.  The Root Mean Square Error (RMSE) shows the average difference between predicted and actual values. A lower RMSE is best. The POSTSEASON target variable is distributed so that any team that did not make the tournament has a 0; teams that made it but lost in the round of 64 got a 1; teams that lost in the round of 32 got a 2; teams that lost in the sweet 16 got a 3; teams that lost in the elite 8 got a 4; teams that lost in the final 4 got a 5; the runner-up got a 6; and the champion got a 7. The outcome will be uneven because only 64 teams make the tournament, and fewer teams advance each round. 

<img width="899" height="450" alt="image" src="https://github.com/user-attachments/assets/d0f0307e-0952-4f2e-8ece-a59aa66d2a81" />

This visualization shows the relationship between Adjusted Offensive Efficiency and Adjusted Defensive Efficiency. Since teams want higher offensive efficiency and lower Adjusted Defensive Efficiency, they want to be in the lower-right quadrant of the graph. The POSTSEASON_STAGE shows that teams that didn’t make the tournament tend to have lower adjusted offensive efficiency and higher adjusted defensive efficiency. The National Champion, Florida, had an adjusted offensive efficiency of 127.8 and an adjusted defensive efficiency of 94.2. Both were among the best efficiency ratings. 


<img width="899" height="450" alt="image" src="https://github.com/user-attachments/assets/4b18a038-d69b-479d-9da6-cefff070ab05" />

This visualization shows teams with the Highest Wins Above Bubble, as well as each team’s Power Rating. The graph shows the teams with the most wins above the bubble. The color shows the team’s power rating. Meaning how likely they are to beat an average Division I team. All four teams that made the Final Four are ranked in the top ten for Wins Above Bubble, and their power rating is above 0.95.


## Data Preparation and Feature Selection

Since only 64 teams make the March Madness tournament, only 64 teams received a SEED and a POSTSEASON value. To fix this, I set any team that did not make the tournament to have a SEED of 0 and a POSTSEASON value of 0 to indicate they did not make the tournament. For this model, I restricted the data to 2025 only. The first feature is wins above bubble (WAB). I chose this feature because it measures the number of wins a team had in the regular season over teams that made the March Madness tournament. Next is power rating (BARTHAG), which shows how likely a team is to beat an average Division I team. Adjusted Offensive Efficiency (ADJOE) measures how efficient a team is at scoring. Adjusted Defensive Efficiency (ADJDE) shows how efficient a team is at stopping other teams from scoring. Lastly, seed (SEED) is the seed that the committee gave to that team. Before training and testing, the team variable was dropped as it is just the name of the team, and year was dropped as all the data is from 2025.

## Baseline and Model Development

I used Mean Squared Error as the baseline. This gives us an average number of wins to start with. The first machine-trained model I ran was linear regression. That model provided coefficients and p-values to determine which features are significant. This model helped predict a line of best fit to estimate the target variable. The second model I ran was a ridge regression. The ridge regression adds an L2 penalty to prevent overfitting and handle correlated variables. The L2 penalty is the sum of squared coefficient values. This can add some bias as the model lowers the variance. I used the same training and testing splits to fairly compare the two models. 

## Model Evaluation and Selection

The evaluation metrics I used are mean squared error (MSE), R-squared, and root mean squared error (RMSE). Mean squared error squares the differences and penalizes large errors and outliers. Root mean squared error is the square root of that value, which retains large error penalties in original units. The R-squared value explains the proportion of variance explained. The ridge model performed better, as it had an R-squared value of 0.9997, while the linear regression model had an R-squared of 0.696. I selected the ridge regression model as the final model. Because ridge has a higher R-squared, it explains more variance in the model. The ridge regression model also had better coefficients. 

## Model Interpretation and Insights

The most influential coefficient is power rating (BARTHAG). Next is wins above bubble (WAB). Adjusted offensive efficiency and adjusted defensive efficiency were similarly influential.  The weakest coefficient is seed (SEED). Feature importance shows each coefficient’s importance and supports that power rating is the most important feature. Residuals show the difference between the predicted and actual values. Many of the residual values are close to zero. From this model, we can conclude that all the features were significant in predicting the target variable and that power rating (BARTHAG) was the most influential coefficient. 

<img width="790" height="490" alt="image" src="https://github.com/user-attachments/assets/cda45357-e73f-4fa7-ab97-2c7b581ef089" />


## Limitations, Ethics, and Reflection

The bias in this dataset is survivor bias. Teams that keep winning and moving on play more games. Seeding is also chosen by a committee, and there could be bias in the seeding and in selecting the teams that make the tournament.  Incorrect predictions can affect people who use this to bet on or predict game outcomes.  This model could help real-world decision-making, but it would be better if it addressed bias more fully, accounted for factors like location, added more stats and features, and used more data from past years. Next time, I would explore more past data to help predict games. 

## Code and Transparency 

Link to Jupyter Notebook: [StudioProject2.html](https://github.com/user-attachments/files/33031803/StudioProject2.html)







