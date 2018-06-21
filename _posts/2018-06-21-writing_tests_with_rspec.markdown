---
layout: post
title:      "Writing Tests With RSpec "
date:       2018-06-21 05:57:44 +0000
permalink:  writing_tests_with_rspec
---

 
In the Flat Iron program, much of our work on labs has been guided by specs, which are tests written with RSpec. I've been reading RSpec code for a few months now, and I'm really familiar with reading the code and using the output to guide my programming. However, I haven't *written* much RSpec code at all, and the idea of writing a bunch of specs seemed overwhelming. One of the best ways to learn almost anything in programming is to **just do it**, and RSpec is, by no surprise, not dissimilar in this way.  
 
### So what the heck is RSpec?? 
 
It's your friend! RSpec is a "domain-specific language", or DSL, used to test Ruby code. Domain-specific languages are exactly what they sound like - a language specific to a domain, or application. You can think of a DSL as a library of functions or methods that you can use for a specific purpose. RSpec is written in Ruby, and its purpose is to test Ruby code. Ruby-ception! 
 
### Why do we test code? 
 
Testing code is very important. Most any serious work you do in programming will likely involve testing code, and most useful code you'll encounter will be well-tested. RSpec is often used specifically for Behavior Driven Development (BDD), which itself is a specific form of Test Driven Development (TDD). TDD simply ensures that all pieces of code involved in your software works, and BDD involves writing your tests first, then programming solutions to make those tests pass. This type of workflow is sometimes referred to as "Red, Green, Refactor." Your tests, when you first run them, are red (like actually, for real, in your terminal), then turn green when you get the tests to pass. This often is followed by some refactoring, since your initial solution may not be pretty or efficient. Tests are essential whether you like them or not, but they are your friend and they will make you a better programmer.  
 
### OK, great, but I still don't know where to start. 
 
Neither did I! There's this great thing about open-source code, though, where you have access to **ALL THE CODE** and **SO MANY EXAMPLES**! Here's what I did (and am currently doing, as I write this): Find a project that is similar and has good tests written already. Use those tests to guide writing your own tests. Depending on how similar your projects are, many tests can be copied and pasted with little to no adjustments, though I would recommend typing them out the long way to get more used to syntax. It's way different typing something than reading it. I'm working on my [Rails Portfolio Project](https://github.com/AspenJames/rails-portfolio-message-board), using [this lab's specs](https://github.com/learn-co-students/rails-amusement-park-v-000) as a reference. As I went along writing tests and making sure they were working, I was checking in on the [documentation](http://rspec.info/documentation/). Before long (like actually a couple hours) I was writing a few tests of my own without checking in on the lab's specs for reference.  
 
### But documentation is scary... 
 
While documentation can sometimes be very intimidating, it is another thing you can get better at by **just doing it**. If you're uncomfortable with documentation, try reading the docs for some things you already understand well. The more documentation you read, the less intimidating it gets! That's also how I've become (mostly) comfortable with man pages as well. All of these things are here to help you out, if you let them. Also most things are not going to break by just trying things, and most things you break can easily be fixed.  
 
### Wow! I think I could actually do this! 
 
You totally can! Go write some specs for a piece of software you already know works, no matter how simple. The tests may seem silly at first, but it's the easiest and fastest way to learn how to write tests. These methods work with anything in programming as well! Whenever you're faced with a new thing, find another thing like it. Find examples and read documentation, avoid copy-paste when you can, and take a step back to a simpler version if needed. These things aren't as fast as Googling your problem and pasting in a solution from StackOverflow, but these things will lead to understanding. Instead of just getting that one specific problem solved, you'll know *how* to solve that problem when you see it or another like it again.
 

