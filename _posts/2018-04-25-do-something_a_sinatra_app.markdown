---
layout: post
title:      "Do-Something, a Sinatra App"
date:       2018-04-25 15:13:07 +0000
permalink:  do-something_a_sinatra_app
---



I built Do-Something to address a despair of the Trump era: there was so much to do to resist, and yet, it gets wearisome, draining. It’s hard to feel like ordinary actions matter, that they add up. I start each day walking my dog in nearby woods, and of my friends, the other dogwalkers, many are activists. I’d listen to them talk each morning, and from those conversations came Do-Something, which is a place to keep track of your actions each day. 


Do-Something is a CRUD application that follows RESTful conventions. A user can add/edit/delete and read their entries.   It uses ActiveRecord to store and retrieve data  from a SQLite3 database. For privacy, it has signup, login and password-security, using the Ruby helper has_secure_password and the BCrpyt gem. 


![](http://res.cloudinary.com/tech-stories/image/upload/c_scale,w_577/v1524668899/carbon_29_xnxjr1.png)



In its current iteration, Do-Something has a User model/table and a Things model/table, the latter being the things one does each day. Though at first emerging from my sense of what my activist friends needed, the idea broadened to include all the things we do each day to feel part of something larger than ourselves. it might be resisting government policy. It might be contributing to a sense of community in our daily lives. It might be taking care of ourselves when all that work is exhausting us. 


Around the time I was completing the app, several friends and neighbors were dealing with cancer and heart disease and the like; I started to think about the micro-acts that we do each day to feel humanly connected, and they too became part of this micro-app. In fact, I started to think about the very concept of a micro-app, something that really meets us where we are in life, and uses code to support and nurture us there. 



User data comes in through a basic signup/login form, and begins the MVC flow. Further input moves over to the Things views, which is set to notice a first-time user — and respond with one type of question, and your returns, where it will list what you’ve been doing — letting you see and feel the heft of it, encouraging you with the accumulation of acts that in isolation, feel small. 


![](http://res.cloudinary.com/tech-stories/image/upload/c_scale,w_634/v1524666600/carbon_25_cgqr9v.png)



Each user only has access to their personal lists, but every user's daily actions are collected on the main welcome page, so that everyone can see the many things being done, and feel inspired to be part of that. 


![](http://res.cloudinary.com/tech-stories/image/upload/c_scale,w_527/v1524666010/Screen_Shot_2018-04-25_at_10.19.46_AM_ez73f7.png)



Once the basic CRUD functionality was completed and the controllers done, I focused on details in the views that would bring in better data, and used data and title fields, and texture input
things/new.html.



![](http://res.cloudinary.com/tech-stories/image/upload/c_scale,w_558/v1524667776/Screen_Shot_2018-04-25_at_10.49.21_AM_w56iup.png)



I wanted this app to be usable, to have a life beyond being a school project, so I paid attention to front end. I borrowed some navigation bar code from w3schools.com, and added a background-image url to the body in the CSS file. The background image comes from the 2017 women marches on DC. (By the way, I host my images on cloudinary.com.) 


![](http://res.cloudinary.com/tech-stories/image/upload/c_scale,w_593/v1524667375/carbon_27_hyfqtr.png)



After another round, I’ll clear the SQLite3 database, attach PostgreSQL and deploy Do-Something on Heroku. In the future, too, I hope to add an additional model/table of future acts, where a person can store three things they'd like to do next, and add User profile pages. 


Github: [Do-Something](https://github.com/MiriamPeskowitz/do-something)
