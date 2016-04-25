---
layout: post
title: Using Movie Data to Predict the Decay Rate of a Film's Weekly Revenue
---

For my second project at Metis, I used movie data scraped from boxofficemojo.com and metacritic.com as the basis of a linear regression model. I sought to create a model that could predict a film's weekly box office revenue by using a decay rate as my independant variable. The use cases are many and would be particularly relevant to movie studios, producers, actors, movie theaters, shareholders of any publically traded entities involved in a particular movies, etc. 

First, let me define my label, or independent variable, the decay rate. I calculated the decay rate as follows:

`decay rate = (ln(opening weekend rev) - ln(last week rev)) / numer of weeks in theaters`


