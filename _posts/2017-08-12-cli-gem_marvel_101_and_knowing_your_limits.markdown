---
layout: post
title:  "CLI-Gem: Marvel_101 (and knowing your limits)"
date:   2017-08-11 20:24:35 -0400
---


I’ve had an absolute blast on this thing. I was intimidated at first, who isn’t, but creating something from scratch can be immensely satisfying. That doesn’t mean I didn’t struggle at times though! All-in-all the project took me right around a week from start to finish while working sporadically. I’d like to write a bit about what I learned from the experience, then briefly show off my shiny new gem.

I went into a CLI Study Group session a few weeks back with no clue about what to do for my project. I was just looking for ideas, and I came out of the study session with a bunch of scattered concepts. I ultimately landed on trying to do a comic-based cli through either Marvel’s API or through a site called Comic Vine.  Using an API was mentioned during the study group, and it seemed like a great way to extend myself a bit on this project.

The results of that were… not great. It took me longer than I care to admit just to figure out how to do a basic query, handle the API key, and turn that result into something readable in ruby. And once I had that, I realized that this just wasn’t what I had envisioned. I had hundreds of superheroes and teams at my fingertips, but my initial vision was something much simpler. I wanted a way to breeze through Marvel’s latest and greatest, catch up on characters with upcoming movies, that sort of thing. 

Instead I found myself with *too much* information, and I felt that even if I could use it efficiently it just wasn’t what I wanted. I thought of maybe scraping a popular heroes/teams list from a different location and gathering info on that smaller data set, but that felt weird and came with a whole host of problems. For one, the data just wasn’t what I wanted. I had access to thousands of issue numbers, volumes, cross-overs, etc., but I just wanted a little infographic with things like “real name” or “powers”, just basic stuff. Second, I got some bizarre results. I couldn’t just simply search for Batman, for example, because I was handed back multiple versions of the caped crusader from alternate universes, movies, spin-offs, and all sorts of random locations. I just wanted *THE* Batman, and it just felt overcomplicated.

So right as I was ready to abandon my comic domain, I decided to just wander around Marvel’s main site for a bit. Eventually I found my way to a nice little corner that had exactly what I wanted! Separate pages that had lists of the most popular heroes/teams/villains, and I could scrape links from there to solid individual pages. After making sure the data I needed would be accessible via Nokogiri, I laid out the broad strokes of what I wanted, and made it happen. I started from the main menu and worked outward, and now I have a program I’m pretty proud of.

I guess what I took away from the experience was importance of knowing my limits. I wanted to make the API work *really* badly, but it just wasn’t a good idea for me. I found myself toying with ideas throughout the process of expanding my app, but constantly had to check myself and make sure I wasn't biting off more than I could chew. It can be hard when that feels like admitting defeat, but I think being honest with yourself is very important to keeping on track with a project like this.



This is already a pretty long post, so I’ll try to keep this short. Marvel_101 has a very simple menu flow, allowing you to navigate between lists of topics, teams, and characters. I'll go ahead and skip to an end point and give an example of character output:

```
1

-----------------------------------Spider-Man-----------------------------------
DESCRIPTION: Bitten by a radioactive spider, high school student Peter Parker gained the speed, strength and powers of a spider. Adopting the name Spider-Man, Peter hoped to start a career using his new abilities. Taught that with great power comes great responsibility, Spidey has vowed to use his powers to help people.
REAL NAME: Peter Benjamin Parker
HEIGHT: 5'10"
WEIGHT: 167 lbs.
ABILITIES: Peter is an accomplished scientist, inventor and photographer.
POWERS: Peter can cling to most surfaces, has superhuman strength (able to lift 10 tons optimally) and is roughly 15 times more agile than a regular human. The combination of his acrobatic leaps and web-slinging enables him to travel rapidly from place to place. His spider-sense provides an early warning detection system linked with his superhuman kinesthetics, enabling him the ability to evade most any injury, provided he doesn't cognitively override the autonomic reflexes. Note: his power enhancements through his transformation by the Queen and after battling Morlun - including his organic web glands and stingers -  have been undone after Spider-Man's deal with Mephisto.
GROUP AFFILIATIONS: Avengers, formerly the Secret Defenders, "New Fantastic Four", the Outlaws
FIRST APPEARANCE: Amazing Fantasy #15 (1962) 
ORIGIN: Amazing Fantasy #15 (1962)

Marvel wiki available! Type 'wiki' to open in browser
Marvel 101 available! Type '101' to open in browser
--------------------------------------------------------------------------------
You can enter (M)ain to go back to the main menu or (E)xit to... exit
Type (L)ist to return to Popular Heroes menu

```

Those wiki and 101 options towards the bottom do in fact work, and are one of my favorite aspects of the end product. 

If you'd like to learn more about marvel_101, [here](https://www.youtube.com/watch?v=pb5RuMjB2jg) is my video walkthrough, and [here](https://github.com/buchheimt/marvel_101) is a link to the repo.
If you're at all interested, I'd also encourage you just to give it a try yourself! It's a ruby gem, so all you need to do to try it at home is to run:

```gem install marvel_101```

```marvel_101```

and you'll be testing it yourself in no time! Feel free to reach out to me if you have any questions, suggestions, troubleshooting, etc.

That's all folks!

