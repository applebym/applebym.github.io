---
layout: post
title: Using Movie Data to Predict the Decay Rate of a Film's Weekly Revenue
---

For my second project at Metis, I used movie data scraped from boxofficemojo.com and metacritic.com as the basis of a linear regression model. I sought to create a model that could predict a film's weekly box office revenue by using a decay rate as my independant variable. The use cases are many and would be particularly relevant to movie studios, producers, actors, movie theaters, shareholders of any publically traded entities involved in a particular movies, etc. 

First, let me define my label, or independent variable, the decay rate. I calculated the decay rate as follows, which is also illustrated in the two graphs below:

`decay rate = (ln(opening weekend rev OR highest weekly rev) - ln(last week rev)) / numer of weeks in theaters`

![The LEGO Movie](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/lego.png)![Interstellar](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/stellar.png)
 
Thus, the more negative the decay rate, the faster revenue drops over time or the steeper the curve. I chose to use weekly revenue per theater vs. gross weekly revenue to adjust for the fact that some movies have a limited release in the first few weeks (as can be seen in the picture below for the movie Philadelphia) and for the differing theater counts throughout a movie's lifespan, which would directly affect revenue. Most movies with a limited early release at the end of the year do so to be eligible for that year's Academy Awards. For comparison, the weekly revenue chart for The Da Vinci Code is below Philadelphia and shows a more normal, exponential shape of weekly revenue per theater. 
 
![Philadelphia](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/Philadelphia.jpg)![The Da Vinci Code](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/davinci.jpg)
 
A look at the data shows that the decay rate does differ somewhat significantly between buckets of certain features. Below are five charts showing the average decay rate for each group of a particular attribute. Most of it jived with my initial intuition. For example, higher rated Metacritic scores and movies released in the early summer and holiday season are associated with less negative decay rates. These are the five features I ultimately chose to include in my linear regression model. 

![Avg Decay by Metacritic Rating](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/avg_decay_by_meta.png)![Avg Decay by Genre](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/avg_decay_by_genre.png)

![Avg Decay by Rating](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/avg_decay_by_rating.png)![Avg Decay by Release Month](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/avg_decay_by_month.png)

![Avg Decay vs Budget](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/scatter_budget_decay.png)

Using these variables, I was only able to obtain an R-sqaured of 0.128 on my training set and 0.117 on my test set. Below is a graph of the betas for each variable and its 95% confidence interval. All of the genres, ratings, and release months are binary variables. The way I interpret my results is that the genre serves as the intercept and the other variables add or subtract small amounts to arrive at the calculated decay rate. The betas for budget and the metacritic rating are much smaller because the absolute size of the input is quite large in comparison to the decay rate, which is a tenth of a decimal. In general, the betas are fairly in line with what we saw in the initial charts. For example, August has the most negative beta of the release months and also had the most negative average decay rate in the chart above. 

![Betas](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/betas.png)

To illustrate how my model would work, I put together two archetypes of a steep decay movie and a shallow decay movie. According to the model, an R-rated, low-budget, Horror film released in August with a low Metacritic score would yield a decay rate of -0.359. On the other end of the spectrum, a PG-rated, high-budget, Animation film released in November with a high Metacritic score would yield a decay rate of -0.161. I have graphed what the weekly revenue per theater curve would look like for each, assuming they start at the same opening weekend per theater revenue point for easy comparison. 

Attributes			            Terms

R rated				          -0.087908

$5mn budget			        0.082270

Horror 				          -0.371003

August release 		    -0.022476

25 Metacritic score	  0.039499

------------------------------

Decay rate 			          -0.359

Attributes			      Terms
PG rated			-0.000303
$100mn budget	        0.098248
Animation 			-0.363797
November release	-0.021356
80 Metacritic score	 0.126397
--------------------------------------------
decay rate 			      -0.161


![Weekly Revenue Example](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/weeklyrevs.png)

Despite seeing a notable difference in the average decay rate between different attributes, I think there are several reasons this was not captured in my model. First, I think I could have further adjusted my revenue per theather metric used in the calculation of the decay rate. As seen with Philadelphia, a limited release movie will have an abnormally high opening weekend revenue per theater, which will skew the decay rate more negative for movies that have quite a "strong" or shallow tail. Using the revenue per theater number at the widest release week may solve this. Second, there are features that I did not include in my regression analysis that could explain some of the variation between the revenue curves. For example, advertising spending (both dollars spent and timing), social media hype, competition from other movies, and Oscar nominations. Lastly, using a decay rate as my independant variable limited the representation of the revenue curve. In reality, these curves have different shapes between opening and closing weeks, including slight bumps around Oscar season. A different metric or non-linear regression may have been able to capture this better. 

I ended this project with many ideas of how to move forwards and improve my model and look forwards to doing so when I have some time. I will report back in a future post with my findings!
