--- 
layout: post
title: Live animation with Meemoo as VJ software
author: forresto
tags: 
- vj
- live
- animation
- claymation
- zodiak
---

I was invited to do visuals for a [Zodiak](http://www.zodiak.fi/en/)'s Side-Step dance festival club night. I used the gig as an opportunity to push Meemoo development and pressure-test the live-animation features. 

<iframe width="720" height="405" src="http://www.youtube.com/embed/T_tCyYGLWKM?rel=0" frameborder="0" allowfullscreen></iframe>  
[Meemoo Live Animation at Zodiak (on Youtube)](http://www.youtube.com/watch?v=T_tCyYGLWKM)

Many thanks to Aino Riiho (and other partygoers) for the clay sculpting, Juho Santasalo for the videography, and Heikki Sillanpää ([dkstr](http://soundcloud.com/dkstr)) for the music.

![Zodiak claymation animated](http://meemoo.org/images/Screen-shot-2012-02-12-zodiak.gif)  
This is what you get for hiring a web developer to VJ your party (o_-)

As the party started and I was still coding furiously, adding features to the world module. Thirty minutes later the music tempo picked up, inviting people to the dance floor, and I made myself declare the coding done for the night. It was a thrill to see the first sprite hit the dance floor: multicolored glitter swirling in water.

We used clay and construction paper (and some glitter) as the basic building blocks of the visuals. I'm attracted to the textures and imperfections that come from using materials like these. Using the taptempo module, I synced the sprites' animation to the rhythm. It was fun to build these tiny animations and then throw them onto the screens around the dance floor. 

For the gig I made some special modules for creating a "world" into which I could insert animated sprites. On the software development side, I'm happy that I decided to make two modules (Controller and World) share the same Backbone model. Each module has its own view of the same model, so the data passed through the wire will be the same on both sides.

There are lots of improvements and ideas that came up in the evening:

* Camera: I used a Sony Eyetoy webcam, and the color was pretty bad. I chose kid's art supplies with rich colors, but most of the color was washed out in the first step. Next time I'll do some tests to find a better webcam, or use the camera on my phone, or a real digital camera somehow.
* Audience participation: I planned to use Kinect to get silhouettes of people dancing into the world, but ran out of time. I was imagining using different animated textures for specified depth ranges.
* Flocking: I only had time to implement the tiled animation. The original concept was that sprites could be individual or flocks that would move around the screens.
* UX tweaks: Confirm dialog on every delete got annoying when juggling around modules. Directly un/replugging wires is a suggestion that is now high on the to-do list.
* I made a hack to open the World module in a new window to view it fullscreen on the projectors. I plan on making this a built-in feature for any module.

Despite these limitations, I got a lot of good feedback about the visuals. People were interested in what I was doing, and came around to play with the art supplies. Doing visuals powered by a web browser (Firefox Aurora, by the way) was a fun experiment, and with a few more display options I think that the limitations would have been less aesthetically obvious. Performing under pressure was a good way to test the system.

Only *once* in the evening did a JavaScript warning pop up on the dance floor. I consider that a victory, and it made me laugh a lot when it happened.