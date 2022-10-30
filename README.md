## Final Project Report

## Project Title: Predicting Qualification / Relegation for Championship League

## Student(s): Iustin Toader, Joaquin Restrepo, Riley Faulkner

#### Date: 12/08/2021
---

#### Abstract
---
The goal of this project is to see if we can predict which English Premier League teams are most likely to qualify for the Championship League, and which are most likely to be relegated. We are calculating our predictions using Win/Loss/Draw data from seasons 2015 - 2019. We split the dataset into 2 parts, training and testing. The testing data set contains data from the 2019 season, while the training data set contains data from 2015 - 2018. 



Upon completing the project, we were 100% accurate with predicting the top 3 teams and the bottom 3/4 teams (there was a tie in points, normally it would be the bottom 3 but in this case since the seasonal points were tied, there are 4.) **Our data model predicted that Manchester City, Liverpool, and Chelsea would be the top 3 teams** for that season and have the highest chance at qualifying for the UCL based on seasonal point values. **Our data model also predicted that the bottom teams would be Fulham, Huddersfield, Burnley, and Cardiff.** When comparing this to the actual standings for the end of the 2019 season we were 100% correct.

Link to the data set on Kaggle: https://www.kaggle.com/ivanpv/premier-league-football-matches-20152019 

### Introduction
---
The Union of European Football Association (UEFA) Champions League (UCL) consists of 32 teams which were picked from qualifying matches prior to the Championship tournament. 

The goal of this project is to see if we can confidently predict which European Premire League teams are most likely to qualify for the UCL based on previous and current season statistics, including the number of games won, lost, and drawn. We used data from seasons 2015 - 2019 and split the data into training and testing sets. The testing set contains match data from 2019, and the training data contains the rest of the season (2015- 2018).
In reality, the qualification of teams for the UCL is more complex, as previous winners of certain European competitions are automatically qualified for the group stages of UCL. Our dataset does not contain any information regarding this. What is more, the number of teams qualifying for the UCL changed in the 2017/18 season from 3 to 4. As such, our model follows the previous rule and predicts the top and bottom 3 teams for consistency.

Our method is the following:     
- Predict the outcome of each game using the data over the first 3 seasons
- Compile the end-of-season standings for each team using our predicted values
- Check the accuracy of our predicted top-3 and bottom-3 teams as compared to the actual standings



We used Decision Trees and the Random Forest model in order to calculate the accuracy of our predictions. The accuracy of our decision tree wasn't the best, roughly 40%. The non-tuned Random Forrest model has an accuracy of 50.2%, but after tuning and finding the best estimators we achieved a 4% increase in accuracy to 54.2%. We could have increased the accuracy even more, but a limitation we found was that higher accuracy scores generally ignore the "Draw" result and focus on  predicting Wins or Losses. However that would not have represented our data correctly since draws happen quite frequently. In this regard we sacrified increased accuracy in order to account for the chances of a draw occuring. 

### Data Sources
---
The data we are using is taken straight from the matches from 2015 - 2019. The data points include: Date, Home Team, Away Team, Outcome (In reference to the home team), Odds for win/loss/draw, Ranking of the Home and Away teams at the time of the match, Last home result, and Last away result. 

### Conclusion
---
The purpose of this project was prediction. Using a dataset on 4 years of Premier League Football matches, our goal was to correctly predict the end-of-season standings for the 2019 season. 

Before getting too deep into models and feature engineering, we first fit our X_total (comprised of prediction data, and onehot vectors) variable into the decision tree classifier- which we use for a baseline accuracy score. Here, we get 40.1%

In essence, the accuracy of predicting the outcomes of every game using all variables inside a Decision Tree model is about 40%. 

Next, we fit the data to a Random Forest model. This pushed us up to 50.2%, and after a bit of hyperparameter tuning we ended up with 54.2%. Now, we found that by ignoring Draw results and prioritizing predicting either Wins or Losses, our accuracy would be higher. The glaring issue here is that we wouldn't be operating with predictions that are true to data- even if they're more accurate on paper. 

Up to this point, we were only precicting game outcome. However what we learned was integral for constructing team standings, which of course is what we were really after.

Our initial step here is a bit of data massaging so that we're moving forward without loose ends. First- we needed to break up our dataset into individual seasons. You can find our construction code commented in the body of our project, but the basic idea is to chop up team winnings based on home, and away games- and then run the league calculation to generate the points value for that team. Continue this for each team, and each season- and then we have prediction data to compare to the real standings data.

We also made a point to generate T/F vectors for our predicition vs actual in order to have an accuracy score for each season. Via this method, we got 33.3%, 66.6%, and 33.3% for the 15-16, 16-17 and 17-18 seasons respectively. Average accuracy was about 44%.

Finally, we compiled the end-of-season standings for our testing dataset using the same method discussed above. Our Random Forest classifier method managed to accurately predict 100% of the top-3 and bottom-3 teams, or the teams which would qualify to the UCL and the teams which would be relegated to the second football league in the UK. We consider this a glaring success to our project, since we managed to achieve this accuracy without having any of the tiebreaker data used in the actual Premier League, such as the final score for each game and so on. We believe that having possessed more of this data, as well as had more seasons included in our training dataset, our model would get even closer to accurately predicting the outcome of each game firstly, and the end-of-season standing secondly. 

### References
Link to the data set on Kaggle: https://www.kaggle.com/ivanpv/premier-league-football-matches-20152019 
