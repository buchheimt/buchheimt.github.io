---
layout: post
title:      "Scene-It - React-Redux Final"
date:       2017-11-22 09:45:51 -0500
permalink:  scene-it_-_react-redux_final
---

Well this project threw me for a bit of a loop, but here I am! I was working under a pretty tight deadline this time; from day one my goal has been to finish under five months. It looks like I've made it, but I cut it a bit close. I would have loved to have more time with it, and I've found React equal parts exciting and frustrating. While Scene-It is definitely my least polished portfolio project for now, I'm still proud of the final product. There is so much to unpack from this experience, but for now I'm going to keep things relatively short.

The idea for the app was to create a Reddit clone(ish), with the intent to extend it and improve on that structure. My fully formed idea involved fetching movie data from a third party API (abandoned very quickly for the final review), gathering data on where movies (and TV shows) were streamable, and providing a nifty way to discuss them that felt a bit more fluid. What I ended up with is a what I feel is a pretty solid foundation, but ultimately just that: a starting point. I hope to realize some of these loftier goals down the line, but I think staying realistic with project goals is definitely a skill in its own right. It's hard to admit you don't have time, bandwith, etc., but I'd probably still be working on my Sinatra app if I didn't limit myself.

So what did I actually end up building? Well you have movies, posts and comments, and they all function exactly how you'd expect them to. Movies have many posts, which in turn have many comments. Within that framework, there are three components (heh) I'd like to touch on:

1. A scoring system (i.e. those simple looking reddit upvotes)
2. JWT authentication (or how the hell do I authenticate anything ever?)
3. Nesting comments (actually really not that bad at all)

So first off, the scoring system. This turned out to be a MONSTER, and in retrospect maybe wasn't worth tackling. A simple system is easy enough, and was exactly where I started. I simply attached a score to each scorable model (movies/posts/comments), and fired off a dispatch on click that adjusted the score for the target up/down 1 point accordingly. Functional? I guess. Completely useless and unrealistic? Definitely. While it was cool to get that up and running so fast, I knew it wasn't *real*, and that'd I'd have to address it eventually. My solution was to create join models that linked up users and scorables, which basically just acted as a join while holding a value (1/-1). This enabled me to track a users scoring, so the user could later change their vote (and see if/how they've already voted). It also prevents multi-voting, which would very quickly break the system otherwise. Handling these point join models was tricky on the react side of things, and my front end underwent several iterations to get it to a point that I felt was logical, though still not quite the DRYest. 

I hadn't even thought about user authentication when I started, and found that roadblock pretty quickly. I wasn't going to just leave my app open to who-knows-who submitting who-knows-what, so I looked through my options and quickly accepted it was going to be complex. I eventually landed on JWT, which as far as I can tell seems to be the go-to for connecting a React front end to a Rails back end. This involved a lot of setup, and pulling from a handful of sources to patch together a process that'd work for my situation. It definitely warrants its own blog post at some point, and I'm sure I wasn't alone in turning to google for help. The basic concept is that you use a JSON Web Token (JWT) and pass it back and forth from end to end, rather than more standard Rails systems. It involves quite a bit of code to get things up and running, but once you're there it's fairly straightforward and it's just a matter of passing your JWT along with any fetch requests from your front end that need to be authenticated.

Finally, nesting comments was actually pretty easy! Recursion can be a bit intimidating, but all it really took was attaching a parent id to comments, then rendering a post's comments layer by layer. This got a bit tricky when I wanted to include comments elsewhere as read-only (rather than having reply/edit/remove buttons), but conditionally rendering these components based on a `renderChildren` prop was surprisingly straightforward. The nesting worked out pretty well, and implementing multiple sorting methods was a breeze after the leg work was done.

And with that, I think I'll go ahead and wrap things up. This certainly isn't the end of my work on Scene-It, or this blog, and I'm looking forward to a bit of a post-graduation break where I can polish up my portfolio before starting the job search. I plan to write some more in-depth posts covering some of the topics mentioned here (as well as some sticky points from past projects), so if you find yourself struggling with similar issues be sure to check out my blog!


