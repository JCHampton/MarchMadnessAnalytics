# MarchMadnessAnalytics - Minneapolis Blakers Repo

Here is the repo for the March Madness MinneAnalytics competition

## Overview

We created an XGBoost model to help predict the outcome of NCAA Men's March Madness games. Features of the model were based on "over expectation statistics." For each of the statistics provided (points, rebounds, assists, etc.), we obtained the average for the team in each category and the cumulative average for what their opponents gave up. We then subtracted those and obtained the "over expectation statistic." For example, if the Minnesota Golden Gophers averaged 68 points per game but their opponents cumulatively gave up 65 points per game on average, the Gophers would have scored 3 (68 - 65) points per game over expectation. We also used the final Massey ranking for each team in the model. We created a couple other models that didn't use the Massey ranking or may have included the seeds but we found that the model without seeds but with the Massey ranking (and of course with the over expectation data) performed the most accurately while also sufficiently predicting upsets. 

Once we had the model tuned, we created a tournament simulation according to the point scoring system used by MinneAnalytics. In this competition, you got 1 point for a correct first round prediction, then 2, 4, 8, 16, and 32 for subsequent rounds like normal. But in addition to that, you also got points for upsets. If you correctly predicted an upset, you got the amount of points that is equal to the difference in seeds so if you picked a 12 seed to beat a 5 seed and it happened you'd get 12 - 5 = 7 points in addition to the "normal" points. Because of this upset incentive, you will see a LOT of upsets in our bracket. For each game we would compute the "expected points" based on the scoring system that not only took into account this round but also future rounds. Generally, for the earlier rounds, if a team had even a small chance for an upset (like Oral Roberts), their expected points was going to be higher so we picked them. From this simulation, we were able to get our picks.

## Future Implementations

In future implementations, we would like to test whether the Massey, Hollinger, KenPom, or BPI (among others) rankings provided the most accurate results. We didn't have enough time for that and just chose the Massey ranking because we knew it had a good history of being fairly accurate. 
Additionally, we would also perform a feature analysis on the input "over expectation" features to see which were not affecting the model much and could be removed. This could also reveal what sort of statistics we may want to look at in future implementations with different data.

## Relevant Files

* [BasicModel.ipynb](https://github.com/JCHampton/MarchMadnessAnalytics/blob/main/MarchMadness/BasicModel.ipynb): This is where we make the models and simulate the tournament. We get our final MinneAnalytics results here
* [PredictGames.ipynb](https://github.com/JCHampton/MarchMadnessAnalytics/blob/main/MarchMadness/PredictGames.ipynb): This is where we get the csv for the Kaggle competition and can see the individual predictions on who beats whom
* [EDAforMM.ipynb](https://github.com/JCHampton/MarchMadnessAnalytics/blob/main/MarchMadness/EDAforMM.ipynb): This is where basic EDA was done
* [NoSeedsYesOrdsModelPredictions.pdf](https://github.com/JCHampton/MarchMadnessAnalytics/blob/main/MarchMadness/NoSeedsYesOrdsModelPredictions.pdf): Here is the MinneAnalytics Model Predictions
* [PredictionsNoOrds.csv](https://github.com/JCHampton/MarchMadnessAnalytics/blob/main/MarchMadness/PredictionsNoOrds.csv): Here is the Kaggle Competition Predictions

## Bracket 

![](https://github.com/JCHampton/MarchMadnessAnalytics/blob/main/MarchMadness/MainBracket.png)

## Team Members
* Jackson Hampton, Will Bentz, Atef Ali, Blake Andert

## Questions?
* Email me at hampt146@umn.edu 
* DM on twitter [@JHamptAnalytics](https://twitter.com/JHamptAnalytics)

## Results
* After Round 1: In first place! 
![](https://github.com/JCHampton/MarchMadnessAnalytics/blob/main/MarchMadness/Round1Results.png)
* After Round 2: In first place! 
![](https://github.com/JCHampton/MarchMadnessAnalytics/blob/main/MarchMadness/Round2Results.png)
* After Round 3: In first place! 
![](https://github.com/JCHampton/MarchMadnessAnalytics/blob/main/MarchMadness/Round3Results.png)

# Sweet 16 Challenge

In the MinneAnalytics Sweet 16 challenge, everyone redid their brackets starting at the sweet 16. 
The organizers allowed every team to make two brackets as long as they still supported each with some methodology.

For bracket #1, we just used the same model/simulation as before and the bracket can be seen here
![](https://github.com/JCHampton/MarchMadnessAnalytics/blob/main/MarchMadness/Sweet16ChallengeBracket1.PNG)

For bracket #2, we just picked all of the favorites in the games. The only underdog we picked was UCLA over Alabama.
![](https://github.com/JCHampton/MarchMadnessAnalytics/blob/main/MarchMadness/Sweet16ChallengeBracket2.PNG)

## Sweet 16 Challenge Results

* After the Sweet 16: In first place with bracket #2! Bracket #1 was 31 out of 38 teams
![](https://github.com/JCHampton/MarchMadnessAnalytics/blob/main/MarchMadness/Sweet16ChallengeRound3Results.PNG)
