# CS210-Fall-2023-Project
The aim of this project is to analyze my Lichess games' data that I obtained from Lichess app. The presentation can be found in this link: https://drive.google.com/file/d/1hNLCUnwA2SDrG-CZf45h7dhHFdyVVOLJ/view?usp=sharing

I downloaded the data from Lichess app. Then converted the downloaded data to .txt format to process it easily. I extracted the dataframe using Pandas and regex. Also, I hided my opponents names since they may not want their usernames to be published. I also did some preprocessing on the data while creating the dataframe to make my job easier in the future. Some of the preprocessings are extracting win, lose, draw from "1-0" information provided in the data and also extracting rival's and my elo's according to role provided by data. 

After creating the dataframe, I did some exploratory data analysis on my data to see patterns. I looked at the numbers of games I played in each month from 2021 to 2023. To visualize this, I used an overlayed histogram from plotly express. It can be seen that I downloaded the app around December 2021, I stopped playing the game from March to August in 2022 and again my use of app decreses around the same time in 2023. This can be seen in plot1.png.

I calculated the number of games I played in each time (morning, noon, evening, night) of the day and visualized the results with a histogram using plotly. The histogram can be seen in plot2.png The frequency of games I play is significantly low in the night, which makes totally sense since I am asleep. I also looked at the winning rates in each time of day but the rates are close to each other around 0.5.

I calculated my longest win, lose, draw streaks and visualized the results with a horizontal bar chart which can be seen in plot3.png.

The calculation of winning rates based on my role (white/black) in the game did not provide a significant difference. The results of white and black are really close.

I calculated the number of games I played in each day of the week and visualized it using a histogram. The distribution seems to be uniform but Sunday has less games than every other day, which makes totally sense since I spend time with my family and friends. The results of the histogram can be seen in plot4.png

Again, calculation of winning rate based on the day game is played did not provide a significant difference. All ratios are around 0.5 and close to each other.

Apart from winning rates, I also wanted to observe the distribution of my rivals' elos based on the result of the game in my perspective. I used an overlayed histogram and marginal rug plots to visualize this. It can be seen that when the result is win or lose, the distribution is close to normal. It can also be observed from the rug plots of win and lose. The plot can be seen in plot5.png.

I also constructed a density plot to observe my elo and my rival's elo to see how the algorithm pairs me with others. As expected, the densest part is around where my elo and my rivals elo's are close to each other and that point is nearly 1400. I say it is expected because who would play the game if algotihm pairs them with extremely experienced rivals? The distribution of elo's for me and my opponent can be seen in the marginal histograms. The plot can be seen in plot6.png.

I also extracted castling information from the moves list provided in the data. O-O means kingside, O-O-O means queenside and O-O O-O-O or O-O-O O-O means the rivals did castling right after each other. After extracting these, I looked at the number wins, loses and draws, total games played and win rates for each castling (kingside, queenside and none). The win rates are not significantly different. However, my preferences are really interesting because I use queenside castling a lot less than others. Maybe I should use it more and see the results. These are visualized in plot7.png with a horizontal bar chart.

I looked at the openings to see if they have effect on my winning rate or not. For this, I eliminated the openings that are used less than 10 to be safe. Moreover, I eliminated games that are played with lower ranked rivals to eliminate the effect of advantage. The remaining openings are tested with Z-test for proportions with significance level 0.05. My null hypothesis is that an opening does not affect the winning rate. And for some pairs of openings, the null hypothesis is rejected. The results of this test is visualized with a network graph using NetworkX and plotly. The nodes represent the openings and if nodes are connected, it means that one of the nodes have significantly less chance of winning than other. This can be seen in plot8.png.

I wanted to see my elo as the time progresses and it can be seen that my elo is increasing in the current times. Moreover, I constructed a waffle chart to see the relative frequencies of the outcome of games based on varied rivals. 

Lastly, I preprocessed another dataframe to use it in Machine Learning model. I encoded the outcome of the game to 0, 1 and 2. I eliminated 2 since it has much less occurence than others. I also eliminated games that have less than approximately 10 moves to be safe. I used Rival Elo and My Elo as predictors and tried to predict the outcome of the game as win or lose. I used a Decision Tree model for this task. I used hyperparameter tuning with GridSearchCV and fitted the best parameters. I used %80 of my data to train and %20 of my data to test randomly. The model has higher recall for win scenario but not that much for lose. 
