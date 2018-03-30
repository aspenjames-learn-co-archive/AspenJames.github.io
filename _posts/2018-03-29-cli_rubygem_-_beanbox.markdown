---
layout: post
title:      "CLI Rubygem - Beanbox!"
date:       2018-03-30 02:57:56 +0000
permalink:  cli_rubygem_-_beanbox
---


For my CLI project, I chose to create a gem that returns a list of best-selling coffees from Seattle's roasters. To simplify the sourcing of the information, I turned to Beanbox.co - a local company that sends out "variety packs" of coffees. They partner with Seattle-area coffee roasters and send out these packs as a subscription service. Users can then rate the coffees and order full-size bags as well. Beanbox.co already had a convenient list of their best sellers, so I figured that would be a great place to scrape for my data. 

I decided to use the `bundle gem` command to get started with my project. This initializes a lot of the core structure, including a .gemspec file, initializing a git repository, etc. Whenever I can get a ton of work done with a three word bash command, I'm game. From there, I made the initial files I knew I would need - `coffee.rb`, `cli.rb`, and `scraper.rb`. Each of these would contain their own class in the Beanbox namespace (ex. `Beanbox::Coffee`), and each would be responsible for only one thing. The names are pretty self-explanatory, but `Beanbox::Coffee` is responsible for creating and storing the individual coffee objects, `Beanbox::Scraper` is responsible for scraping the website, and `Beanbox::CLI` is responsible for driving the interface. 

I also attempted to work with TDD by running `rspec init`, but after toying around with a few tests I realized that I was doing too much at one time. I plan on learning how to write tests and use TDD to my advantage, but it seemed like too much to take on - learning the rspec DSL as well as creating my first project - so I ended up proceeding without and eventually deleting the `.rspec` and `spec/` files. 

After much trial and error (mostly figuring out file requirements), I got a working model! When running `./bin/beanbox`, I was greeted with a simple message and displayed a list of four coffees and prices, then... the program exits. Super boring. Successful, sure! But boring, yes. I knew that this would happen, though, and I was ready with a plan: code in a menu to allow the user to select a specific coffee for more information. 

This was fairly simple. I created `#list_menu` in `Beanbox::CLI` that grabbed user input. If that input corresponded to one of the coffees listed, `Beanbox::CLI` called a new method in `Beanbox::Scraper`, `#scrape_detail`. This method scraped further details from the target coffee's specific URL and added those attributes to the corresponding `Beanbox::Coffee` object, then returning those in the CLI. I added a loop that waited for users to input `"exit!"` so that they could gather as much info as they wanted! 

For future features, I could see a tune-up on the display of the CLI as well as an option to navigate to the purchase page once the user has found a coffee they're interested in trying! 
