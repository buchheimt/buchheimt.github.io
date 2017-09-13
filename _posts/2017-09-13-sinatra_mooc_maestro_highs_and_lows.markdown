---
layout: post
title:  "Sinatra – MOOC Maestro (Highs and Lows)"
date:   2017-09-13 19:10:31 -0400
---




As I prepare to submit my second portfolio project for Flatiron, I look back at the past week with some mixed feelings. I went in to this project with a clear vision for my first web app, wanting to create a personally useful (though limited) app to track my progress in online courses across a variety of topics and websites. It felt like a good fit for the Sinatra project, but as I started mapping out my database and models I quickly realized that my initial concept was overambitious.

Slowly but surely, I whittled my idea down to something I felt was actually realistic to implement. I started with what I considered a given: users that can create and/or join courses which belong to programs. From there, I decided to expand my database to incorporate platforms and subjects. Platforms would have many programs, and subjects would have a many-to-many relationship with courses. Through these models, my hope was to create an app where one could theoretically browse indices via all these models (courses, programs, platforms, and subjects) to find new courses to join. I wanted all items to be shareable so that, in a more developed iteration of the app, many users could join the same course, and users could find new courses and programs based on the additions of like-minded learners. So, with all this in mind, mapping out all of these models on paper looked something like this:

![](https://i.imgur.com/xj0rWzP.jpg)
(forgive the… less than stellar handwriting)

After translating this to code, I found myself with a bunch models and tables, unsure of the next step. The number of routes I needed to put together was pretty intimidating, and I couldn’t decide where to begin. Ultimately, I started with the user controller and focused on building out all the appropriate RESTful routes. After moving on to the course controller, and the associated join table, things started coming together. Eventually I managed to build out all the necessary controllers and routes with some ugly-but-functional views. At this point I stopped to take a look at what I had built and I was… really disappointed. 

All the pieces were there but with zero styling, a horde of edge case bugs, and some remaining stubbed methods, it just felt like a mess. The code wasn’t remotely DRY, I was abusing the poor database with unnecessary queries, and what it was capable of just wasn’t impressive. It soon checked off all the project requirements (the stubbed functionality was above and beyond), but it just felt off. I think part of the problem is simply wanting to do more than I’m capable of at this point, and learning to accept my current limitations and abilities.

At this point, I had been working for 2-3 days. But after another 3 days, plenty of bootstrap, and a LOT of refactoring (really, it was pretty excessive), I have a project I’m proud of. The homepage allows the user to add progress to their courses, or quickly access any of their active courses or programs. (Check it out [here](https://i.imgur.com/xg11VVX.jpg), the image isn't cooperating at the moment)

For each category (courses, programs, platforms, subjects), there is an index of all items of that topic, a show route for info on a particular item (and the ability to join/leave/edit where appropriate), and routes for editing and creating new courses. Here is an example program show view:

All-in-all it was a bit of a rollercoaster, and I know I could’ve chosen a better topic for a simple Sinatra app, but I enjoyed the process by the end and I’m excited to move into rails. I’m a bit past the two month mark at Flatiron now, and while I’ve come pretty far I know I still have a long way to go.

Thanks for reading, and feel free to check out my quick walkthrough video [here](https://www.youtube.com/watch?v=iWNG_RcLwH4), or clone the repo [here](https://github.com/buchheimt/mooc_maestro) and play around with it yourself. 

Happy Coding!

