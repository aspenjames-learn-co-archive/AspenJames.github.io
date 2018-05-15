---
layout: post
title:      "Sinatra Project - OS Review"
date:       2018-05-15 06:31:34 +0000
permalink:  sinatra_project_-_os_review
---


For my Sinatra section project, I chose to create a review site for operating systems. Users would log in to post reviews about their favorite operating systems, either creating a new OS or choosing from a list of existing systems. 

There are three models: User, Review, and OperatingSystem. Each of these Ruby classes are mapped to a Sqlite3 database table using ActiveRecord. They also have the following associations: Users have many Reviews and many OperatingSystems through Reviews, OperatingSystems have many Reviews and many Users through Reviews, Reviews belong to both a User and an OperatingSystem. I thought this was fairly interesting, since the main Ruby class of this project, Review, is also functioning as a join table. I would not have expected the main class to be a join, so this relationship was not immediately apparent to me. After jotting down some notes and talking it out with my partner (aka thinking out loud in his general direction) did it click. 

Setting up the database migrations, model classes, and basic controller routes was fairly easy. RESTful route convention makes building out this section a (nearly) no-brainer. I'm a big fan of how easy ActiveRecord and REST makes short work of a large portion of the project! After the basic structure was built, most all that was left was the front-end HTML, CSS, and validations. I handled validations via a helper class (appropriately named Helper) and basic HTML5 form input validation. I used the Twitter Bootstrap for the navbar and applied a background and additional styling in a separate CSS file. For error messages and alerts, I used Flash messages with the Rack-Flash gem. '

The root index '/' view show either a Welcome page with a link to create a new review for logged-in users while users not logged in see links to the '/login' and '/signup' routes. I accomplished this by using an if/else conditional statement and calling on my Helper methods from within the ERB view. All other routes that depend on a user being logged in or not are handled in a similar way, though from the controller itself. 

I set a couple of stretch goals to explore down the line: adding a link to the operating system's website, possibly scraping for install instructions, and selecting a few "featured reviews" to display on the root index for logged-in users.

All in all, the practice with Sinatra was great, and I really enjoyed building out the project. Admittedly, I enjoy the back-end work *much* more than the front-end layout and design. I definitely learned to start with any frameworks/templates I want to use rather than try to apply them retroactively. The latter method is much more time-consuming and complicated!
