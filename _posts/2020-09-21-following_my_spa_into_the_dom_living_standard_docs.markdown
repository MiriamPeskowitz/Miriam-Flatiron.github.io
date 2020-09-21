---
layout: post
title:      "Following my SPA into the DOM Living Standard docs"
date:       2020-09-21 13:50:32 -0400
permalink:  following_my_spa_into_the_dom_living_standard_docs
---


At the point that I imagined, wireframed and built the API and frontend for Writing Place, I had been in Flatiron’s Fullstack program long enough to have created the first version of this project using jquery. It had been an app for Soup Kitchens, where users could leave yelp-like feedback on soup kitchens and food pantries they’d visited. The idea came from a project I’d done at Code for Philly, and then, from conversations I’d had with the Dept of Health. I coded most of that project, and then ran into a problem using data-id and event bubbling. My work life heated up, too, and I had a new book to promote, so I took many months before I returned to this project. By then, happily, the curriculum had changed. JQuery was out, and SPA design patterns were in, using a vanilla JS frontend with a Rails API. 

Instead of retooling the old app, I created [Writing Place](https://github.com/MiriamPeskowitz/underground_frontend) The concept: Writing Place provides spaces and places as a prompt for writing. You choose a topic, and use each of it’s eight sites as a writing prompt. Then (and this is still a stretch feature), you can see all your notes together, and edit and stitch them together into a longer piece. The app nurtures you into new kinds of writing, and I imagine it might be useful for education, or for adults who want to write and journal but need some structure for doing it, and an element of surprise. 

![](https://res.cloudinary.com/tech-stories/image/upload/v1600710049/Screen_Shot_2020-09-21_at_1.39.51_PM_or4uju.png)

Building the Rails API was fairly straightforward, but since I’d been thinking in JavaScript for many months, I had to relearn Rails and RESTful conventions. What was new was working with serialization so that my data could move back and forth from Ruby and JSON, and I chose to work with the fast_jsonapi gem, after spending some time with tutorials, and understanding the specific ways that it nests data. 

The JS front end had two big challenges. The first was coding in Object-Oriented JS. This, I found, was an act of imagination. Even when I copied suggested syntax and “got it right,” I found that it wasn’t enough; it still didn’t feel familiar. To get there, I had to sit and close my eyes and follow the data through its flow, seeing it start in the database, watch it as JSON, see it come into the front end through the fetch function, and only then did it make sense that my JS class constructors were organizing the JSON to use as a coherent class, or grouping, on my front end. This act of imagination felt like a step forward. You can actually get a lot done on an app without actually understanding what’s happening, but I wanted to not feel like any line in my app, or any relationship between code and files was a mystery. 

The second challenge, again, was using data-id, and then when I cleared that up, the challenge was in understanding and using eventListeners with dynamically-created elements. Because of its async character, eventListeners become a problem in JS when the elements they’re attached to aren’t available, and in an SPA app, this happens all the time. The result is a click that won’t work, or a situation where the first of a series of data will click open, but the rest won’t.

In my SPA, I need to capture the data-id specific to a single site in a dynamically-generated list. 

![](https://res.cloudinary.com/tech-stories/image/upload/v1600710029/Screen_Shot_2020-09-21_at_1.40.18_PM_k7g3wl.png)

The solution to the problem of eventListeners with dynamic JS is to attach the eventListener not to the specific element, but to a parent that will always be present. Then of course, one’s left with the problem of locating the exact location of the click, so that the code related to that specific click in a single location can trigger the intended reaction. This is done by using event.target to find the location of the click, and making sure that it corresponds to the correct  id, class or element. 

Here are some examples of attaching the eventListener not to a specific element but to a parent, like document, and then using e.target to only run the function if the click equals a specific className, in this case the “see-sites-button.”

![](https://res.cloudinary.com/tech-stories/image/upload/v1600709799/Screen_Shot_2020-09-21_at_12.42.40_PM_kmjyl5.png)

Similarly here. The addEventListener function is attached to document, and runs only if event.target.id is the “show-writing-button.” 


![](https://res.cloudinary.com/tech-stories/image/upload/v1600709805/Screen_Shot_2020-09-21_at_12.42.30_PM_mqrx88.png)



And here, the eventListener is on`document. The location is grabbed by using event.target, this time finding not the id or the className, but the dataset id, the particular id attached to a list of rendered items. The specific data-id is nabbed, then used to locate the object’s data using a findById method built into the object-oriented JS design. 

![](https://res.cloudinary.com/tech-stories/image/upload/v1600709809/Screen_Shot_2020-09-21_at_12.42.09_PM_vhjhbj.png)


At this point, the click will attach to the correct element on a list. One of the topics in Writing Place is Underground Sites in Philadelphia. Click on that topic and you’ll see a list of 8 sites, each with a photo and description. A user can click on any of these and a form will come up to reflect and write, based on this site. The way to make this click work for all members of the list is to attach the click to the parent, and then tell the browser to use event.target to find the data-id number, and use that to find the correct site. 




To figure this out, I ended up doing a deep dive into event listeners, which became a deep dive into the target property, the Event interface (and all the things we get with a browser that we don’t have to add code for; the browser itself is a living object), EventTarget, and event delegation. All of this is beyond the scope of this blog post, and I’m leaving some resource links below. But here are a few things to remember. 







First, the browser. The browser has events, and the three most common are window, document and element. It’s the document event that we’re attaching our event listeners to, in lieu of attaching to a specific element, through we could attach it to the window as well, or to a specific parent element that we know will be present throughout the life of the SPA.  When something is confusing, I recommend searching the MDN docs and other resources to deepen your understanding of the browser. It really is the environment that we full stack developers live in, and it’s worth getting to know how it really works. Often the MDN docs include a link to the source code for that topic in the LS, or Living Standards, published by the WHATWG community. When I understood the surface level of “attach the event listener to the parent element” and “then use e.target”, it still just felt like magic until I tracked through MDN and found the DOM Living Standards and started to understand the code behind the DOM. 

Second, event.target works because “an EventTarget object represents a target to which an event can be dispatched when something has occurred.” A primary use of the target property is to “implement event delegation.” Event delegation is one of those HTML topics that you cover quickly, and it returns in JS with a vengeance, and I found that if you don’t take the time to imagine what’s happening, to slow down and see the movie of your code, the way data moves through it and events move through it, then you’ll feel like you’re faking it. The classic article is this: https://davidwalsh.name/event-delegate. It’s a huge topic but here’s the short form. HTML elements are nested in the browser, and an event attached to an element will propagate, or move around. It can “bubble” up, going from child to parent, inner to outer element. This is the default. Event propagation can be coded to “capture,” or move from parent to child, or outermost element to innermost element; you’d do this by adding an optional 3d argument to your event listener. 

Here’s the HTML. I’ve underlined various parent elements that I could have attached an event listener to, though I chose document instead. A click on the button with a data-id of 3 would have bubbled up to all of them, and beyond, to the document event that’s part of the browser. 


![](https://res.cloudinary.com/tech-stories/image/upload/c_scale,w_493/v1600709789/Screen_Shot_2020-09-21_at_1.17.10_PM_pieqfz.png)
 
At various points in learning JS, HTML becomes really important, and this is one of them. It’s all about knowing, really knowing, the stack of events that will be fired through the HTML elements in the browser, and how JS expands this and works with it. 

As promised, resources: 

https://davidwalsh.name/event-delegate
https://developer.mozilla.org/en-US/docs/Web/API/Event
https://developer.mozilla.org/en-US/docs/Web/API/Event/target
https://dom.spec.whatwg.org/#interface-eventtarget
https://dom.spec.whatwg.org/#interface-event
https://dom.spec.whatwg.org/#event-target
https://whatwg.org/
https://stackoverflow.com/questions/1687296/what-is-dom-event-delegation) 





