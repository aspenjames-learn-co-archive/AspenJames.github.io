---
layout: post
title:      "Espresso.Log  - A React/Redux project"
date:       2018-10-11 22:51:11 +0000
permalink:  espresso_log_-_a_react_redux_project
---


As I approached my final project for Flatiron, I knew exactly what I wanted to create. I had been planning an application that would store and track espresso recipes for coffee shops. Most of the coffee shops at which I have worked - and there are a good number - have realized that this espresso recipe data can be useful. I highly agree with that thought - it can inform barista's decisions in the morning as well as indicate potential issues to managers and roasters. Despite the usefulness of tracking this data, there does not currently (to my knowledge) exist a tool that is easy to use and can provide valuable insights. At this time, I'm not quite ready to launch a publicly accessible version of this project, but you can view the demo [here](https://youtu.be/lAN5w8BDbHk) and the GitHub repo [here](https://github.com/AspenJames/espresso-log-react-simplified).

## What is an Espresso Recipe?

An "espresso recipe" is the set of parameters that go into making a shot of espresso. In general, we as baristas are paying attention to the dose, yield, time, and days-off-roast for our coffees. The dose is the weight in grams of the ground coffee that we'll be using to make the espresso. The yield is the weight in grams of the liquid espresso that gets served or used as an ingredient in a drink. The time is simply the amount of seconds it took to brew that espresso. Days-off-roast is how we measure how fresh a coffee is - quite literally the number of days since the coffee has been roasted. 

Many different variables can affect these parameters, some within our control and some without. In general, consistency is key. The only way we can know if what we're serving is good without tasting every single espresso is to make our preparation as consistent as possible. The only way we can ensure a consistent quality and flavor profile for our guests is to decrease the variation in preparation between baristas. Therefore, this data can be an extremely useful measure. 

## What does Espresso.Log do?

Espresso.Log provides a convenient platform to record, store, and track this data. One of the major things I knew I needed was ease of use and speed for the barista. Opening a coffee shop requires moving quickly and efficiently, often earlier than most care to be awake. If the tool we have to track our data is cumbersome, the likelihood that we will actually use it is very low. The barista simply selects the coffee they're using from a list and enters their recipe. If the coffee they're using is not yet on the list, it is extremely easy to add a new coffee. Espresso data is then presented in a graph where we can toggle individual parameters to view specific changes. 

## The Code

Espresso.Log is essentially two parts - the backend API server written using Ruby on Rails, and the frontend client written using React.js and Redux.js. The API makes use of a PostgreSQL database, Active Model Serializer for structuring the JSON responses, and bcrypt for ensuring the users' passwords are stored securely. In addition to React and Redux, the frontend client makes use of Redux-Thunk for dispatching async actions to store and fetch data as well as some custom middleware for dumping and refreshing a user's Redux store data to and from browser local storage. This allows users to refresh pages and navigate to specific links without the application resetting the store and logging them out. I used [CanvasJS](https://canvasjs.com/react-charts/) to render the espresso charts. This is a really nice library that integrates well with React, and I'm excited to explore the functionality more in the future. 

## Extensible Goals

The biggest challenge I faced while creating Espresso.Log was definitely scope creep. I was a bit overly ambitious with my original ideation of the project, and after spending much longer than I expected in development I chose to drastically simplify the scope. After putting many features in a "Stretch Goals" category, the project became much more manageable and I was able to accomplish it with relative ease. These are some of my goals to extend and expand this project in the future: 

  - Support for multiple users for each coffee shop
  - Creation of an "Admin/Manager" role
  - Inclusion of weather data by hitting an external weather API
  - More analysis and better portrayal of changes in data over time 
  - More interactive charts and graphs

## The Takeaways 

Projects can be a huge undertaking and require proper planning. I sketched out my database and models, but didn't take the time to sketch out the frontend and definitely suffered because of that. It may feel like a waste of time and, if you're like me, you may want to dive right into programming, but prototyping and planning is extremely important. 

New libraries are fun! I really enjoyed looking at a few options for making charts and graphs, and learning about CanvasJS was really nice. I'm curious to try out a few others, but with so many features and options I could spend a lot more time exploring CanvasJS and probably never reach the end. 

It's extremely nice to have everything I've learned lead up to this point. If I could go back in time and show myself this project, I don't think I'd believe it possible for me to learn this much in the amount of time that I have. Hard work and persistence really does pay off, and programming can be easier than expected with the proper resources and motivation. 
