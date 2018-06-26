---
layout: post
title:      "Rails App - Messaging Board "
date:       2018-06-26 23:34:46 +0000
permalink:  rails_app_-_messaging_board
---

 
For the past couple days, I've been coding a basic [Messaging Board web app](https://github.com/AspenJames/rails-portfolio-message-board) using Rails. The object relations, routing, controllers, etc., are all pretty easy for me now, so I chose a different way to challenge myself: using RSpec and Capybara to test my application, and using a front-end framework to make my app look a bit more polished.  
 
## RSpec and Capybara  
 
I already covered most of my experience with RSpec [here](http://aspenj.com/writing_tests_with_rspec), so I won't recap very much. The most complicated thing I ran into was debugging Capybara feature tests when they weren't functioning quite like I expected. The most useful thing here was, of course, `binding.pry`. However, I quickly realized once I was in that pry session that I wasn't quite sure what to do! We can examine the `#<Capybara::Session>` object returned by `visit foo` by using the `page` keyword. Ruby has this awesome method called `methods` that you can call on just about anything, and it returns a list of methods to which the object you called it upon responds. I strongly recommend checking that out anytime you *just don't know what to look for*. It most definitely gave me things to explore rather than just poking around in the dark.  
 
## ZURB Foundation  
 
I looked at a couple options for front-end framework and ended up choosing ZURB Foundation. I really liked the slick look of it, but most importantly their "Building Blocks" let you copy templates for individual elements you like. They have all sorts of building blocks to choose from including nav bars, forms, buttons, ...almost anything you could think of! Full disclosure, the styling of most of these didn't work right out-of-box for me. With a few simple tweaks to the CSS files I was able to get things looking nice though! I know with a bit more practice using front-end frameworks like this I'll get better and faster!

![](https://media0.giphy.com/media/cbd6CRamL8jAc/giphy.gif) 
 
## The Takeaway 
 
I had a lot of fun using some new tools, and implementing tests and a framework from the start is **infinitely** easier than trying to go back and apply them later. Separating new ideas and functionality into branches keeps things organized and gives the peace of mind that you're not going to mess up the working model you already have. I'm looking forward to exploring the stretch goals I have sketched out for this project! 
 
 

