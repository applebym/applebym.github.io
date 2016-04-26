---
layout: post
title: Using Movie Data to Predict the Decay Rate of a Film's Weekly Revenue
---

For my second project at Metis, I used movie data scraped from boxofficemojo.com and metacritic.com as the basis of a linear regression model. I sought to create a model that could predict a film's weekly box office revenue by using a decay rate as my independant variable. The use cases are many and would be particularly relevant to movie studios, producers, actors, movie theaters, shareholders of any publically traded entities involved in a particular movies, etc. 

First, let me define my label, or independent variable, the decay rate. I calculated the decay rate as follows, which is also illustrated in the two graphs below:

`decay rate = (ln(opening weekend rev OR highest weekly rev) - ln(last week rev)) / numer of weeks in theaters`

![The LEGO Movie](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/lego.png)![Interstellar](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/stellar.png)
 
Thus, the more negative the decay rate, the faster revenue drops over time or the steeper the curve. I chose to use weekly revenue per theater vs. gross weekly revenue to adjust for the fact that 

![Philadelphia](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/Philadelphia.jpg)

![The Da Vinci Code](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/davinci.jpg)

![Avg Decay by Metacritic Rating](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/avg_decay_by_meta.png)

![Avg Decay by Genre](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/avg_decay_by_genre.png)

![Avg Decay by Rating](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/avg_decay_by_rating.png)

![Avg Decay by Release Month](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/avg_decay_by_month.png)

![Avg Decay vs Budget](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/scatter_budget_decay.png)

![Betas](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/betas.png)

![Weekly Revenue Example](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/post2/weeklyrevs.png)
