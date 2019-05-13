---
layout: post
title:      "Open Source Alternatives to Trello"
date:       2019-05-13 00:30:54 +0000
permalink:  open_source_alternatives_to_trello
---


If you're like me, you're a **huge** fan of open source applications, and you try to limit your use of proprietary software whenever possible. I'm by no means exclusively using free/libre software, but I always look for alternatives for the tools I like when they are closed source proprietary applications. 

One pain point I had recently was finding a project management tool that fit my needs. My ideal application is open source, free/libre, and would run locally (without an internet connection). I find myself needing to settle (temporarily) on only meeting some of those requirements, as most of the options I have found are web-based applications and therefore require a server running locally or a web endpoint to use. I have plans to build a simple TUI (text user interface) application that would meet all of my needs, ideally saving to plain text files that then could be synced across devices manually. Until then, however, these are the alternatives that I have been exploring:

[Taiga](https://taiga.io) - Tool that supports different project management sytles. If you need a solution to manage Kanban boards as well as Scrum boards, this is the tool for you. Also supports running your own server either locally or deployed in case you would like to be fully in control of your own data. Easy to add custom tags and priority levels, assign tasks to users, etc. GNU GPL Affero License.

[Wekan](https://wekan.github.io/) - Allows for a [trial](https://demo.sandstorm.io/appdemo/m86q05rdvj14yvn78ghaxynqz7u2svw6rnttptxx49g1785cdv1h) before installing your own server instance. Does not have a hosted endpoint to use, unlike Taiga, which means it must be installed locally or on a server. Allows for complete control of one's own data, but will take a bit more work to set up than an option that you can use via a website. MIT License.

[TaskBoard](https://taskboard.matthewross.me/) - Pretty similar to Wekan in that it offers a [live demo](https://taskboard.matthewross.me/demo.html), but must be installed in order to use to its full potential. Allows for markdown syntax in editing, which is pretty rad. Very transparent tech stack laid out in the above link. MIT License.

I am currently using Taiga, as I tend to prefer GNU GPL licenses, and I like that I could use it on a web endpoint without needing to install locally. It also appeared to be the most feature-full option, which will let me test drive many features to plan out what I would like to include in my own TUI implementation. Give one of these a try -- if you find some features you like, you can find the lines of code that make those features possible! That's the beauty of free and open source software. 
