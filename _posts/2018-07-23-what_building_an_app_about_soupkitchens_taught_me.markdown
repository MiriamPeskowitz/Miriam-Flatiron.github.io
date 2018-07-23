---
layout: post
title:      "What Building an App about Soupkitchens Taught Me"
date:       2018-07-23 14:40:24 -0400
permalink:  what_building_an_app_about_soupkitchens_taught_me
---



I decided to go to code school for two reasons. First, that I'd just finished writing a book about coding, for girls and beginners everywhere. It was wide rather than deep. I learned some Python, set up many Raspberry Pi's and figured out breadboarding, and that's just what made it into the book. On the cutting-room floor were long chapters on Minecraft, HTML and CSS, how to get started in Swift and make a "baby" app for your iPhone and lots more, thanks to workshops I'd taken with Girl Develop it Philly and other other local tech groups. I promised myself that when I finished writing, and during the many months we’d spend editing, designing and illustrating, I would go to code school. I’d fallen in love with coding. 

The second reason is all about Code for Philly. As part of writing the book, I’d stopped by a Code for Philly hackathon, and became part of the NearGreen team, which was at the beginning stages of building a healthy food finder app for Philadelphia. I did write about the experience, and our app even won the audience award at Demo Night, but the process had a long lasting effect on me. I’d watch Brad tinker with the back end. I’d see the CSS work of various front-end engineers on our gthub page. I knew enough to make sense of what they were doing, but what I really wanted was the know-how to build an app. I fell in love with code, and I fell in love with civic hacking. 

So here I am, summer of 2018 and I’m building my first full Rails app. 

For my Flatiron School Rails project, I decided to build a new part of that project. In June 2018  I had  a meeting with the Director of Chronic Disease Prevention at the Department of Public Health, and one of her colleagues. Her division is all about making healthy food accessible. I told her about our project, and I asked her what she needed. What would actually be helpful, would solve real problems. 

“Well,” she began. “What we really need is a Yelp for Soupkitchens.” 

That’s right. Turns out 30% of the city uses soupkitchens and foodpantries, and the hardest thing about getting someone who needs them to try them out is discomfort. Just like going to a restaurant you’re paying for, you’d like to have a sense of things before you get there. Crowdsourced reviews for soupkitchens and foodpantries? I could make a Rails app for that. 

And so I began. The resulting code is at https://github.com/MiriamPeskowitz/soupkitchens.



So what did I learn about coding from this project? 


### I feel in love with tests
I know, it’s a cliché in ever dev’s journey, wherein they fall in love with testing and devote themselves to Rails forever. Not to say that I wrote tests – I did write a few, but that’s far from the process I’ll do for my next project, which is write a test for every feature, as I build that feature. It would have made my life so much easier. Without tests, I was left only with my own eyes scanning my code in response to catchall browser errors like this LoadError that really meant to say: you’ve got a syntax problem somewhere, with commenting out code, trying pieces in the console. So, next phase: writing tests. 



!(http://res.cloudinary.com/tech-stories/image/upload/v1532370474/Browser%20Error%20screenshot.png/)



Because writing tests means you really know what your code is supposed to do. During my last few tutorials with tech coaches, the same theme has been reaching me: you can’t know how to fix something until you know what you’re trying to accomplish. You can’t know what you’re trying to accomplish unless you really understand routing, MVC, associations and databases. The take-away: know your stuff. Really. The second take-away, know what your methods are supposed to return. Because when you’re really stuck, knowing return values is a super power. 

### Slowing down
Slowing down while writing code, so that careless mistakes don’t get there in the first place. And slowing down while debugging, especially, really reading SQL statements to see if my code is doing what I think it is. Slowing down to test in the console. Slowing down to really learn new topics that come up, or slowing down enough to scroll to the bottom of a Stack Overflow thread, not just try to pop in the first suggestion.  

 ### Oh no, the envronment!
 Sometimes it really is the environment’s fault. Near the beginning of this project, I had my first major bummer of an environment problem. I still don’t know how I got there, but somehow my app started running Rails 3.2 even though I’d upgraded to Rails 5.2, and when I dug around, there were several Ruby versions catapulting into each other. What did I learn, when the problems get really weird,  check ruby –v and rails –v. Learn what’s making the programs themselves run, or not. 


###  What’s next?
First, the Rails eval, of course, and then, getting up with my Code for Philly team and getting some feedback; deploying the app on Heroku so others can see it, and getting it back to the city for their feedback, and for moving the app into the world so it can be useful

