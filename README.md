# Capstone


Problem: 

People are predicting NBA analytics everywhere. The potential for the legalization of sports gambling within the US is subject to change, which would open a new market for sports betting outside daily fantasy sports(DFS) and betting in casinos in Las Vegas. 

Data: 

First, I scraped Basketball Reference’s season long statistics and wanted to perform EDA for season long trends and get a look at a high level of correlations within the season long averages. 

I also received the following datasets for box score statistics broken down by game in a csv from BigDataBall.com.

1.	Team Statistics 
2.	Season Player Feed

The 2 major benefits to choosing the NBA was availability of data and timing. 
-	The NBA has an enormous variety of advanced analytics that are accessible to consumers and BasketballReference.com is very friendly for web scraping.  
-	On top of this, by the time I turn in this project the NBA will have completed just over 96% of its season. That has translated to almost 25,000 rows of data and 650 different players. 


Exploratory Data Analysis

The data from BigDataBall.com was very clean. They were able to constantly supply csv’s the day after games occurred and the bulk of the cleaning came in the feature engineering section below.
Also within BasketballReference was the ability to look at converted statistics. This included, Per 36 Minutes, Per possession, and other advanced statistics. It would allow for normalizing minutes and games across all players and create metrics such as Win Shares to one’s impact on the games differently.  

Feature Engineering

The main issue was the time series aspect of what I was trying to solve and the diversity in the data collected. I couldn’t use previous game statistics to project a player previous points scored, so I shifted the data by a game so it made it testable. 
The other piece of the NBA schedule that needed addressing is that each game the teams would face a different opponents each game. I wanted to incorporate team statistics into my data set so that I would have features such as Offensive Efficiency, Defensive Efficiency, and team’s Pace of Play. 
Once I had merged all of the dataframes it was time to create rolling averages of all the attributes I collected. I chose to collect three-game, five game, and ten-game averages because players play more minutes based on their recent productivity thought NBA coaching styles.
One of the key factors I had to remember was that because I had initially shifted my data by one game, I needed to shift my target, (y), back one game so that I would be accounting for predicting their points within the last game. 
At this point, I had a large data set. I needed to drop the null values that remained from the previous shifts and it left me with the shape of the dataset at: (24773, 224).  


Neural Networks

The need for a machine learning algorithm to handle the complexity of my data led me to Neural Networks. I liked that it could keep all of the games in a times series simply by adjusting the shuffle attribute. What I also realized what that scaling the data was crucial for exploring its correlation with one another. Transforming the data also served the purpose of making it three dimensional for going in the network. 
At this point, it was time to experiment with amount of layers, epochs, drop out percentages, and make sure I understood when my model began over fitting. In the chart on the next page you will see that overfitting didn’t occur until just after the fourth epoch. 


Mean squared error - 23.4


Conclusion

The neural network was the right model given the data I was working with. Increasing the dropout rate and adding a density layer all helped with increasing my accuracy. By the nature of neural networks, it was easier to use than traditional statistical methods because it could examine features both non-linearly and all against one another. 
I also believe that there is room for improvement within linear regression. Because I drilled down to the individual player level and shifted the data, the game sample size per player went down to ~64 games. Accounting for opponent player defensive ratings by position, would allow for more a “opponent player match up” feature to be included. Also one could argue that making Road/Home games a (0,1)/binary doesn’t effectively measure the atmosphere of playing arena to arena. Traveling across time zones and playing in altitude play a big part in the NBA travel schedule today.  






