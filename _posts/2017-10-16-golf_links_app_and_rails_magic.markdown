---
layout: post
title:      "Golf Links App (and Rails Magic)"
date:       2017-10-16 04:10:31 -0400
permalink:  golf_links_app_and_rails_magic
---


It took a lot of work to reach the Rails section at Flatiron, but oh boy was it worth it. I had been looking forward to building a real, working, you-can-actually-show-family-and-friends app from day one. Early on while I worked my way through the Ruby curriculum I had a hard time grasping what it was all for. Not that it wasn't useful; I love Ruby and really enjoyed building my CLI program! My brain just couldn't connect what I was doing at the time to building complex web apps. 

Then SQL came along (then ActiveRecord, then Rack, and then *finally* Sinatra), and I could really start to see it. MVC clicked, being able to write Ruby along with html through erb blew my mind, and it was challenging but very rewarding to finish off my Sinatra portfolio project. Still though, it all felt a little off. I knew Sinatra wasn't the 'top of the mountain', I just didn't really understand where things went from there. I found myself running into roadblocks left and right during my Sinatra project, settling for "just wait till Rails" but not really understanding *what* the solution would look like.

Now, as I convince myself to finally stop working on my Rails project and just submit the thing, I think I understand some of that Rails magic. Not all of it by any means, I think that might be borderline impossible, but enough to be dangerous. Enough to change my mindset from *"uh oh, I don't even know how to begin to handle this. I have no clue what I'm doing. nope nope nope"* to *"I have no clue how to handle this **yet**, but I know where to look and I'm going to figure this out"*. It's a pretty cool feeling, but it took a long time to get there and I still have a ton to learn.

I have heard a lot about "Rails magic", and want to briefly touch on that as well. For anyone not quite there yet, Rails is, in fact, magical. Things like form_for, collection rendering with partials, and nested routing are ridiculously powerful, will sound like gibberish if you're not there yet, and make life a *lot* easier. I think it's still really important to try and understand what's going on under the hood though, and not lean on these tools as a crutch. Ideally they are tools in the sense that they simplify work and make life easier, rather than you'd be totally lost without them. It also makes debugging a lot more efficient, and allows you to more easily tinker with all of the options and possibilities rather than using the most basic documentation example. As anyone at Flatiron can attest, the curriculum does a great job of emphasizing this mentality throughout. 

I took this "under the hood" approach with my user authentication for Golf Links. I decided not to use Devise early on because I had a number of user customizations in mind and had heard of the difficulties of implementing them, and ultimately I'm happy with that decision. I don't think it's a black and white choice though, and if out-of-the-box Devise suites your needs I'd definitely recommend it. I managed to complicate my omni-auth (FB) quite a bit, and it'll probably get reworked after my assessment, but if nothing else I think it was a valuable exercise and I learned a lot.

**Golf Links**

My initial concept for my Rails app was way too ambitious. It would be cool to build up my app to that point someday, piece by piece, but it was beyond the scope of this project by several magnitudes. So I settled for something a bit simpler for now: an app that allows users to create and join tee times in hopes of improving their golf experience.

Basically, golfing without a full group of 4 can be kind of a drag sometimes at popular/busy golf courses. You might get matched up with another group to fill out a tee time (i.e. maximize profits). In my experience, it's a poor time more often than not. Not necessarily the golfing with strangers part, but the *kind* of golfers you get paired with. Everyone has different pace-of-play preferences, and very different skill/experience levels. A father and son playing alongside two scratch golfers can lead to a frustrating time for everybody. Match up the father and son with others who are still learning, or form a full group of experienced golfers, and everyone involved is a lot more likely to have a good time.

The point of Golf Links is to help you find a better fit before you get to the course. Eventually I'd like to build out more features (especially social ones), but as it stands you can easily create, join, and leave tee times. Each user has a pace and experience setting, which are visible (and averages are displayed for tee times) so you can get a sense of what kind of players you would be playing with. You can also easily bring guests along and add new courses that aren't already in the database, along with an array of minor features.

If you're interested, the app is deployed [here](https://golflinks.herokuapp.com). Switching my database over to PostgreSQL was a bit of a challenge, but I'd definitely recommend it. If you're somewhere earlier in the curriculum and interested in deploying eventually, I'd highly recommend taking note and using PostgreSQL from the start. There are plenty of great tutorials out there if you're unfamiliar. I started from scratch and was up in running pretty quickly.

You can check out the video walkthrough of Golf Links [here](https://www.youtube.com/watch?v=4RdcIHf0SaI&feature=youtu.be), and the github repo [here](https://github.com/buchheimt/golf-links) (Yeah, I know there's a lot of room for refactoring views). I have added virtually no JavaScript to the app at this point, so a lot of the front-end will be reworked for the next stage (JQuery front-end and JSON API).

Thanks for reading, and don't hesitate to get in touch! Especially with any suggestions or bugs, there's always room for improvement. I'll wrap up with a few screenshots for the curious.

![TeeTime#index](https://i.imgur.com/iXeHyOc.jpg)

![User#show](https://i.imgur.com/OSoCvtv.jpg)

![Course#show](https://i.imgur.com/4mJQsl6.jpg)



