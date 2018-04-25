---
layout: post
title:      "The Hub Mystery, Deciphered"
date:       2018-04-25 17:11:11 +0000
permalink:  the_hub_mystery_deciphered
---



Around Flatiron, there are those that skip the so-called “Avi videos” and those who pass around tips to make the most of them, with notes like “Watch them on youTube where you can slow the pace to 75%” — be forewarned that when you do this, Avi Flombaum sounds like he's experiencing a high-pollen count spring day. You either bear through it, or learn to listen and code faster so you can return to 100% audio speed.  “Definitely code along with them, it’ll up your coding game” says Tech Coach Brad near the end of a study group one evening. “I got this from Avi,” says another TC as he showed me the “cool kids” secret of using Option + up arrow to quickly pop to the top of the long list of RSpec and Capybara-laden reasons why your code is currently failing. If you watch closely, you can hear the names of current tech coaches and section leads, as Avi says things like “Great point, Cernan,” or "Exactly, Dakota.” 

One video has a particularly mysterious ending. After creating files, no one can remember whether it's  Sinatra, Rails, or PORO, plain old Ruby objects, Avi saves the files not in the usual way, which would mean browsing to Github, creating a repo and following the third set of instructions to  "push an existing repository from the command line." Instead, he says, “Watch this, it’s amazing,” and proceeds to create a new repo from the command line AND then he git adds/commits/pushes the files. From the command line. 

Every so often, Flatiron students will ask each other, "Hey, remember that? What was he doing?” Well, the other day I slacked out the question, to which the ever-awesome Tech Coach Seth messaged back the tell-all answer: He uses hub. 


That’s the magic. 



Here's how to install hub and get it working so that you can create repos right from the command line. 



Make a new directory and cd into it. 


![mkdir](http://res.cloudinary.com/tech-stories/image/upload/c_scale,w_372/v1524508503/carbon_uhgww3.png)


Use homebrew to install hub: brew install hub.


(If you don't already have homebrew installed, here are the [machine-specific directions](https://docs.brew.sh/Installation)).


![](http://res.cloudinary.com/tech-stories/image/upload/c_scale,w_391/v1524511265/carbon_3_bpep04.png)


(Or you can install it from the source code on github: git clone https://github.com/github/hub.git && cd hub. More directions [here](https://github.com/github/hub), and it will look like this: 



![](http://res.cloudinary.com/tech-stories/image/upload/c_scale,w_478/v1524513943/carbon_18_jfss9w.png)



Once hub is installed, at the command line, type: alias git=hub.


![](https://res.cloudinary.com/tech-stories/image/upload/c_scale,w_395/v1524511466/carbon_8_ktlldu.png)


Check git version, to make sure both git and hub are set up. If they aren't, go back and troubleshoot the installation.


![](http://res.cloudinary.com/tech-stories/image/upload/c_scale,w_386/v1524511407/carbon_6_l4hrrn.png)



We're ready to do what we're used to: git init.

![](http://res.cloudinary.com/tech-stories/image/upload/c_scale,w_214/v1524676191/carbon_31_btlbar.png)


Then, git add and git commit:


![](http://res.cloudinary.com/tech-stories/image/upload/c_scale,w_639/v1524513767/carbon_17_l8wgb3.png) 



Here's the special code magic, the create-repo command: git create -d "Your-File-Name"


![](http://res.cloudinary.com/tech-stories/image/upload/c_scale,w_519/v1524513863/carbon_16_vvnyoy.png)


Use git remote -v, to check that the rep was created and to make sure your files are headed to the right place.


![](http://res.cloudinary.com/tech-stories/image/upload/c_scale,w_716/v1524511573/carbon_12_czasns.png)


Check your git log and/or git status, as usual, and then:  git push origin master, and follow any other directions that come up. 


![](http://res.cloudinary.com/tech-stories/image/upload/c_scale,w_662/v1524511140/carbon_13_e5i9tn.png)


Now for the fun: check your repo. 


![](https://res.cloudinary.com/tech-stories/image/upload/v1524511762/Screen_Shot_2018-04-23_at_3.08.41_PM_l3atlq.png)


 * There may be some troubleshooting on the push, like setting git push --set-upstream origin master. If you're trying this with a file name but no files, github may get slightly confused and direct you to the usual create-repo screen. 


After the initial hub setup, when you're ready to create the repo, use alias git=hub, add and commit, create -d "file name", and push. 

More on hub [here](https://hub.github.com/) and [here](https://github.com/github/hub).

>Q. How'd you get command line code to look like that? 

>A. Thanks to Seth Alexander for that link too:  [Carbon](https://carbon.now.sh ) to show source code.


