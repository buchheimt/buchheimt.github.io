---
layout: post
title:      "Golf Links v2.0 (front end fun!)"
date:       2017-11-14 06:06:14 +0000
permalink:  golf_links_v2_0_front_end_fun
---


Well, I managed to find my way down more rabbit holes than I care to admit, but things are wrapping up and it is finally time to submit another project. This portion of the Flatiron School curriculum was deceptively tricky. Basically AJAX is hard, and it took me awhile to wrap my head around the full scope of the concept. The individual pieces made sense along the way and I understood the ultimate goal, but getting from A to B felt overwhelming. Slowly but surely that gap continued to shrink, and by the time I found myself in project mode I was more excited than nervous. I'll take it!

So, revisiting Golf Links. I was pretty happy with the result of the first stage of my app, and I was excited to incorporate JavaScript and take the project to the next level. Entering this phase I had two main objectives;  1) add some JavaScript (primarily through JQuery and related plugins) to enhance the UI and 2) implement an API in unison with AJAX to meet project requirements. I thought I had already done most of the heavy lifting in the Rails phase, but it's amazing how easy it was to get lost in the front end.

The first goal was fairly straightforward, and it felt great adding elements like a quality datetime picker and fancy range sliders. I was a little worried about incorporating plugins at first, particularly how they would fit in to the asset pipeline and my existing app, but for the most part it was surprisingly straightforward. The datetime picker was a bit tricky to fine tune, but the improvement felt great for the time invested.

That second part was a lot more challenging. Modifying my existing Rails app to deliver JSON in the right places wasn't too bad, but progress on the front end was much harder to come by. It took a bit of time to get up and running, and I was particularly frustrated with the lack of info out there on compiling ES6 for my deployed app. But that is a whole tangent, and might even warrant its own post as I'm not thrilled with my current solution.

For my particular domain, the TeeTime#show route was the sticking point. All along I had intended for this route to be crucial to the app, and I wanted to cram a lot of functionality into one page. The ability to join, leave, add guests, and remove guests are all accessible from here (as they should be!), and making sure the correct information was being passed from my API to enable me to complete all these tasks for the current user while maintaining the state of the tee time probably took the largest chunk of my time.

Once the big four AJAX features were up and running I turned to my comments section, a close runner up for the deepest rabbit hole. I was able to get the basics up and running surprisingly fast, and was excited to have a working comments section that displayed comments and had a form to create more. That was short lived sadly, as I soon realized that a comment feature with no ability to edit and/or remove comments wasn't much of a feature at all.

So I set off to add basic remove and edit functionality and dove a bit deeper. This was particularly tricky, as the entire comment section is generated via AJAX already so there was a lot of work to be done on the front end. Little things like authorization (you probably shouldn't be able to edit other people's comments!) suddenly felt much more complicated. But as always, after some trial and error I got the functionality up and running and was able to put the comment section to rest (after a lot more stylistic tinkering, naturally). I'm not sure if I'd recommend trying to implement CRUDy comments via AJAX at this stage of the program, it felt like a lot of work and not a lot to show, but it was a great learning experience if you're up for a challenge.

If there was one takeaway from this iteration of my Rails app, it's that you learn by doing. Obviously you need to get a handle on the basics first, but the best way to really wrap your head around a concept is to pick something challenging and build it yourself. It's not pretty at times, but I think that's where the real growth happens.

Well I think that about does it for this entry, the end is in sight! Feel free to play around with Golf Links live [here](https://golflinks.herokuapp.com/) (try username: user, password: user1234 if you don't want to sign up), the video walkthrough of the new features [here](https://www.youtube.com/watch?v=3mVBDeh84UQ), and the github repo [here](https://github.com/buchheimt/golf-links).

