---
layout: post
title:      "Refactoring Rails App with jQuery"
date:       2018-08-10 00:02:47 +0000
permalink:  refactoring_rails_app_with_jquery
---


## The project

I refactored my [Rails messaging board app](https://messaging-board-rails.herokuapp.com/) recently to use a [jQuery front-end](https://messaging-board-jquery.herokuapp.com/) for loading some resources. **Note: Logging in with Twitter is currently broken - I'm working on it!** 

The two apps above are separate branches of the same Github repository, so if you'd like you can compare the [Rails app](https://github.com/AspenJames/rails-portfolio-message-board/tree/postgresql-db) with the [jQuery app](https://github.com/AspenJames/rails-portfolio-message-board/tree/jquery-front-end). 

## The differences 

If you navigae to the "Boards" tab on the Rails version and sort alphabetically, you'll notice the page refreshes (and has an ugly URL). In the jQuery app, this is handled much more nicely, without a page refresh, and without a cluttered URL. The jQuery version also has the added benefit of leaving the parameter requested selected in the dropdown menu rather than returning back to "Default". 

You'll also notice that posting a new message to a board will also require a page refresh with the Rails app, but not so with the jQuery app. This is a much nicer user experience, and drastically reduces the amount of information being requested from the server when submitting a new message. With  the standard app, an entire HTML document must be generated and served upon message submission, whereas the jQuery version only requests the newly created message data in JSON format. 

## The challenges 

I definitely fought with Active Model Serializer a bit when setting up the internal API. Things more or less worked okay, but I was having a hard time getting the Board model serializer to include the User data associated with its Messages. I ended up writing a custom serializer for this association and things were back to working just fine. 

One mistake that was very simple to make, yet took me an embarrassing amount of time to track down was in loading the Board index page. This is the view you get when you click "Boards" in the navbar. There was this weird thing happening where sometimes there would be many duplicates being rendered and very odd behavior. Turns out, I was rendering some elements twice due to how I set up my controller. 

While setting up the serializers, I set up a simple `respond_to` block in my index action so I could switch between the HTML view and the JSON. It looked like this:

```
def index 
  respond_to do |f|
	  f.html {@boards = Board.all}
		f.json {render :json => Board.all}
	end
end
```

I've removed the logic behind the sort function, but that's not necessary here. The issue showed when I refactored the index page to render all content with JavaScript instead of HTML/erb. I needed the `respond_to` block so I could load the HTML "template" as well as retrieve the JSON data with `$.getJSON...` without the need to create a separate route/controller action. For some reason, when I left it as above, some boards were getting loaded multiple times. All it took was changing `f.html {@boards = Board.all}` to `f.html {render :index}`, and I didn't have any more issues with that. 

Also, somewhere along the way my database got cluttered with duplicates and incomplete data. I scoured my code to find where there may have been a rogue `$.post` or anything similar, and couldn't find any. I chalked it up to me doing something strange when setting up Postgres, since I've never used it before this project. Resetting the database and re-seeding fixed the weird data and I haven't been able to duplicate the issue, so I'm counting it as resolved for now!

## What I would do differently next time 

Well, this doesn't really apply since the project was to refactor an existing Rails app with jQuery, but I wouldn't do that again. I would instead use jQuery from the start or not at all. That's not to say I _couldn't_ do this again if needed. It's just that if I wanted a jQuery front end, that's so much easier to achieve if I start with that. 
