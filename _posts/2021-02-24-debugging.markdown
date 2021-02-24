---
layout: post
title:      "Debugging "
date:       2021-02-24 18:21:54 +0000
permalink:  debugging
---

For this post about my final react project I’ve chosen to write about debugging, because this, more than anything, has become what I wanted to get good at before finishing. 

There were other things too: syntax, researching answers, learning design patterns. I can add: feeling at home with redux store and organizing my data; doing async fetches and understanding promises and accounting for lag time in a react component with loading features; and figuring out routing with react-router, especially for show page and  update features with dynamic content in the url. 

But all of these things, ultimately, can be learned from others, with enough repeat readings of docs and blog posts, and video rewatching. To feel like I’m ready to be a developer, I set for myself the goal of solid debugging skills. 

The app,  [Mourning](https://github.com/MiriamPeskowitz/mourning-front-end-2020),  has a Rails API and a React-Redux-Thunk frontend. Debugging in Rails was something I was used to. I’ve worked with the rails console, binding.pry, and the server responses enough to understand where the problems are. I know how the flow works: urls find config/router, find controller/api/v1/entries, finds model.rb or entry_serializer.rb. Thus, it was on the frontend side that my debugging skills needed to grow. 

1. **The Redux action flow**-- from a component importing an action, running it through an export default connect to “reduxify” it, calling it from a render, flowing into the action creator for an async dispatch, that then runs through a synchronous action creator that changes the redux store, which then is called back to the component with a mapStateToProps function to update the component’s data —is a big abstract circle to understand. Some debugging became easy over time, but largely because I got it wrong in so many instances: has the action creator been included/destructured in the export default connect — or is the component still using the lighter version, the unconnected version that was imported? Seeing workflow arrows flowing through a component became a debugging skill that solved many problems, once I could figure out which part of this multi-component flow still needed to be wired in. 

2. **Where did my redux data go?** An important debug I learned was to make sure that each case inside a reducer put the data back in the exact same order as the initial state was set. Otherwise the data object structure inside the store changed, which often meant that another component depending on it would error out. 

1. **Making sure that the interface between js and rails was clear**. Big tangles of data not working often are solved by 1) making sure that the object to be stringified is in the exact format that the rails params specify, with the correct names in snake case. That was an important debug to learn.
2. **Type:** one of my earliest lessons as a coding student was to stare at the rails server, and realize that what a thought was an integer — 5— was really a string—“5”. It felt like the ultimate kind of close attention to detail, and I came back to that again and again, so that when an id wasn’t working, I had another tool for figuring out why. 

3. **Research, research, research, luck.** This code worked:

![](https://res.cloudinary.com/tech-stories/image/upload/v1612808590/dispatch_addEntry_entry.data.attributes_fmzvcg.png)

The app added the new entry to the reducer, cleared out the new entry form, and loaded the proper component, EntryCard.js, with the proper data, so the user can see what they just created. 

This is similar code, and it worked. 
![](https://res.cloudinary.com/tech-stories/image/upload/v1612808596/dispatch_resetEntryForm_w81tgo.png)

This, however, in an action creator that deletes an entry, did not:

![](https://res.cloudinary.com/tech-stories/image/upload/v1612808604/dispatch_deletEntryIsSuccessf_couukl.png)

The result was about 8 hours researching why it didn't work, and trying out a variety of hacks and work-arounds suggested on stack overflow. The problem was that when history.push(‘/profile’) loads, the Profile.js component, the data does not refresh. This meant that the recently deleted entry would still be there. Also, the re-loaded component didn’t have access to the props that had fed it when it first loaded, and thus would error out, unable to find the data it needed. The reason: history.push doesn’t cause a refresh of data; that’s just what happens. 

The first two examples above, from the addEntry and updateEntry action creators, push to a route that includes a render. That’s why they work to reload the page and refresh the data. 

![](https://res.cloudinary.com/tech-stories/image/upload/v1612808608/Route_exact_path_signup_component_Signup_e5uzaq.png)

Once I understood what my problem was, that it was a feature, not a bug, I tried out a slew of Stack Overflow proposed solutions. These included turning my /profile path into a render — (render={()=> <Profile />} — but versions of that didn’t work. I also tried fake-out redirects, various uses of window.location() and  goBack() and various other hacks to trick the component into refreshing. The most telling thing I learned from all those hours: so many times, developers on SO would say, I don’t know what this solution works, but it does. 

A series of console.logs and alerts I’d added in-between each line were showing me that after dispatching to my reducer with (deleteEntryIsSuccessful(id)), my code was going right into a re-render of my app component; it wasn’t even returning to line 156. I couldn't figure out why this was happening. Then, pretty much in desperation I switched the order, and it worked. 

![](https://res.cloudinary.com/tech-stories/image/upload/v1612808613/history.push_profile_eizxif.png)

My code was able to send a delete request to the back end, get back the response that it had not caused an error, rerender the profile page and then dispatch the change to the reducer. 

It still feels like a hack, because I don’t fully understand why the order matters here. Also, it seems to depend on the synchronous function deleteEntryIsSuccessful’s  updating the store -- and that this will happen more quickly than the profile page can reload. But I’ve gone with this solution. (Another one would have been to rewrite the component as a class, and use the lifecycle method componentDidUpdate(), which checks for current and previous params, but I’d seen that done in a series of videos I was watching to learn design patterns for React/Redux, and I wanted to see if I could do it a different way.)

There were other debugs, and many hours spent checking react and redux dev tools, and assessing console.logs. Often, the answer to a debugging problem was to learn/relearn how something works. This was very much the case with the react router props of match, location and history. There's no way around that; we have to understand how something is supposed to work so we can figure out why it isn't. But I reached my goal: not just a working mvp with full CRUD capability, but really feeling comfortable with the process of figuring out why my code wasn’t working, and pushing through the debugging process. 




