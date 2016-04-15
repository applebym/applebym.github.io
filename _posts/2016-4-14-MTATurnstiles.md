---
layout: post
title: Using MTA Turnstile Data to Create a Smart Canvasseering Plan
---

I ride the subway everyday, along with millions of others. Each time someone swipes their card and plows 
through the turnstile, the MTA captures that bit of data at that points in time (well, actually during that
specific four hour increment, to be precise). 

For our first project at Metis, we were challenged with the task of downloading, cleaning, organizing, 
scrubbing, and analyzing this data to help an organization with the task of deploying a street team
to canvas for their gala at the beginning of the summer. The task was loosely defined: we knew that the 
gala appealed to women in tech and that the organizations goals were firstly, to gather as many email 
addresses as possible and secondly, to increase gala attendance and potential contributions. The rest was up 
to us to determine.

Thus, my team and I started out by creating our own assumptions for the gala. We decided that the gala would
be held during the first week of June in Manhattan. Thus, we collected data from the 5 weeks leading up to 
June in 2015, assuming this is an accurate proxy for subway traffic in May in 2016. 

Before looking at the data we brainstormed potential factors that could influence our decisions of where
to place canvaseers. Below is a snapshot of our list:

Factors that influence number of email addresses:
- number of entries and exits
- time of day
- day of week
- seasonality / holidays
- proximity to tech companies
- number of canvassers

Factors that influence gala attendance and contribution:
- resident vs. tourist
- disposable income
- occupation
- distance from gala
- gender
- age

Ideally, we could gather all of the above data and overlay this insight with information gathered from our 
analysis of the MTA data. Given timing and ability constraints, we chose to focus on the following factors:
number of entries and exits, day of week, seasonality / holidays, proximity to tech companies

We used dictionaries and pandas DataFrames in Python to store and clean the MTA data. Once that was finished,
we took some high level snapshots of the data. Below you can see some of the output generated:

![Top 10 Stations](https://raw.githubusercontent.com/applebym/applebym.github.io/master/images/top_20.png)

I will finish my blog post this weekend with details on the data side of things. 
