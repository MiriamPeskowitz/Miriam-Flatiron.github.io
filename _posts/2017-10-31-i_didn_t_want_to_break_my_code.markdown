---
layout: post
title:      "I Didn’t Want to Break My Code"
date:       2017-10-31 17:10:56 -0400
permalink:  i_didn_t_want_to_break_my_code
---

## Miriam Peskowitz

I was so excited to learn web-scraping. I’d taken a workshop a while back using Python and the descriptively-named Beautiful Soup library, and I'd worked on some APIs for my Code for Philly project. I couldn’t wait for this part of the Flatiron curriculum and for the first project: the vaunted CLI Data Gem project. I was geek-thrilled to watch the video about bundling, too, and requirements, a combination of mysteries I’d always wanted to solve: where all these files with fancy names come from and what they do, and how you tell files to interact with each other. I was a happy camper. 

I was so psyched about my mini-gem. It worked. It scraped four kernels of daily information -- a meditation, a word of the day, a writing tip of the day, and some ideas for conversation -- and presented them to you, the user. It's the perfect starter to a day, which is why I happily called it Day Starter. When my Terminal gave birth to the output, well, I was the proud parent of an awesome working gem. Had we not moved away from Terminal output decades ago, well, my app could be the first thing that millions would awake to, appreciatively, each day. I've built things with code before, but this was the best. I didn't want to change it ever. 


![Round 1](http://res.cloudinary.com/tech-stories/image/upload/c_scale,e_trim:10,h_197/v1509472154/Screen_Shot_2017-10-18_at_9.29.08_AM_vzxpku.png)

## You Know the Downfall's Coming

Except, as Tech Coach Enoch noticed about 28 minutes into one of our sessions, it worked without actually using Object Orientation. 

"But it works," I said. 

"Yes," he replied. 

"There are classes," I continued. 

"Yes," he agreed. "But there are no object created. “We can't pass you along without an object. You forgot to use Object Orientation.”

I opened a file whose lines I’d commented out, to show him that I'd started to create an object, but then realized I could make the app work without it, and so I did just that. Don’t they say that working code is good code? 

We were 28 minutes into our 30 minute session.

"Good," he said, always upbeat. "You're on your way." 

It's not hard to code an object. I take that back. Until you get object orientation, it’s abstract and your brain has to constantly supply the 95% of stuff you’re not seeing in your code and you have to think through how the classes collaborate and what their relationships are, as if it’s a softball team, or three kids working on the same Minecraft world: how’s everyone getting along an working together? 

There is a flow and a rhythm to creating an object class, with repeatable questions to ask: 
	What is this object? 
	What does it do? 
	What properties will it need to do its thing?
	What does every instance of it need when born?
	What responsibilities does it have? 

Indeed, the example we watched in video after video was baby = Baby.new. Objects are creatures. They’re modeled after real life. We’re in control of the design. 

You'd think I'd jump back in, rework my dear gem and move on. After months spent with Javascript, I loved the literary wordiness of Ruby. In truth, though, it was hard to reopen the Sublime files.

## Code-attachment
To code my Day Starter gem to the next level, I had to break it, and I didn't want to do that. 

Like everything else, coding is emotional and human; it emerges from how we like to do our work, from our quirky habits of creativity, and what we like to hold onto. At the same time as I was coding the gem, I was editing a 60 page chapter for a book, a chapter about Python projects for beginners. My goal: as much as possible, remove the abstraction, clear away anything that could break a reader’s attention and highlight the anecdotes and fun part .I was no stranger to taking things apart to make them better. 

Yet my gem went untouched for days, frozen in time. 

I didn't want to destroy what was working. The fact that no one in their right mind would care about or use an app that pushed information to the Terminal finally convinced me go in and make changes. We hold onto silly things. I made myself fetch the files from my github repo, and start the destructive-creative process. 

## Happy Ending? 
I started over. It happens. I chose one site to scrape from: audiodharma.org and checked that it’s HTML was relatively organized. It was, with nothing unseen manipulating the DOM. I reread lessons, watched more videos, signed up for studyhalls and codealongs and labs. The new-and-much-simpler app scraped five of the most recent meditations on AudioDharma – because when you want to listen to a meditative talk, you don’t really need to spend 20 minutes swiping through the site to pick the best and most perfect one. You choose, and then realize you're out of time. You want five, or even one, so you can get right to it. That's what my data gem offers. 

![Code snippet](http://res.cloudinary.com/tech-stories/image/upload/v1509473741/Screen_Shot_2017-10-31_at_2.15.08_PM_te9ztx.png)

The new gem, Meditation, was simpler but went deeper. It initiatlized with actual instance of the scraper class and used the scraped data to create instances of two other classes – like Todays_choices and Meditation. The classes collaborated simply and in an organized fashion. I'd realized over the past few weeks that I tend to overcode, adding methods I don't use, and more complicated patterns than needed, and in the new gem, my goal was to create only the methods I needed, and nothing else.  

![Code snipper, working CLI DATA GEM](http://res.cloudinary.com/tech-stories/image/upload/v1509484068/Screen_Shot_2017-10-31_at_5.07.05_PM_jllnq5.png)

(Thanks to Corinna for pointing out that most windows machines block system/open, and suggesting I add the actual url instead.)

## The Grand Finale
Go to Rubygems.org, type meditation in the search bar, and you'll see my gem, version 0.1.1.

[Meditation on Rubygems.org ](https://rubygems.org/gems/meditation)

[Github Repo](https://github.com/MiriamPeskowitz/CLI-meditation/tree/working)



