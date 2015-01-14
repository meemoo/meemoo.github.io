--- 
layout: post
title: Turtle power to the people
author: automata
tags: 
- mozilla
- mozfest
- artofweb
- mirobot
- noflo
- flowhub
- thegrid
---

The Grid meet up
===

<a href="https://www.flickr.com/photos/auto_mata/15065111643" title="MozFest 2014 #ArtOfWeb by Vilson Vieira, on Flickr"><img src="https://farm8.staticflickr.com/7552/15065111643_46ca051fa5_c.jpg" style="max-width: 100%;" alt="MozFest 2014 #ArtOfWeb"></a>

After working for about three years with [Forrest](http://twitter.com/forresto) we finally meet him on a meet up of [The Grid](http://thegrid.io) team.

During the first days we were preparing a workshop for [MozFest's #ArtOfWeb](http://mozfestartoftheweb.tumblr.com/) track. The idea was to present a quick introduction to [Flowhub](http://flowhub.io)/[NoFlo](http://noflojs.org) and how to use it to draw with [Mirobot](http://mirobot.io). Then we would let people create their own drawings. 

We created a [NoFlo component](http://github.com/noflo/noflo-mirobot) to talk with Mirobot:

<img src="http://i.imgur.com/mPaTFEJ.png" style="max-width: 100%" />

Having the robot represented as a component made it easier to even explain to people how it was drawing: "the *SendCommand* component waits for commands --- like go forward or turn left --- so when it receives a new command, it sends it to the robot. When the robot finishes drawing, it signalizes banging the *completed* port, so we are good for the next command".

For the workshop [Gabi](http://gabithu.me) created a NoFlo graph that draws contours of a given image:

<img src="http://i.imgur.com/F7C5adG.png" style="max-width: 100%" />

Given an image as input (the heart), the graph extracts its edges and chooses random points from it. If we give those points to Mirobot draw randomly, it will end up with a random path that wouldn't remember the original shape of a heart. We have to order the points in a way the robot will travel along the shortest path. We have a Travelling Salesman Person solver that finds the shortest path. After converting cartesian coordinates to polar ones --- because Mirobot just understands translations and rotations, remember? *forward X* and *turn left/right Y* --- we send the commands to Mirobot and using *noflo-canvas* we draw a preview. Here's the result:

<a href="https://www.flickr.com/photos/auto_mata/15686069502" title="MozFest 2014 #ArtOfWeb by Vilson Vieira, on Flickr"><img src="https://farm8.staticflickr.com/7581/15686069502_b1ba2ffe39_c.jpg" style="max-width: 100%;" alt="MozFest 2014 #ArtOfWeb"></a>

The other graph collects points someone draw on a canvas and after sending that, Mirobot draws them on paper:

<a href="https://www.flickr.com/photos/auto_mata/15065111643" title="MozFest 2014 #ArtOfWeb by Vilson Vieira, on Flickr"><img src="https://farm8.staticflickr.com/7552/15065111643_46ca051fa5_c.jpg" style="max-width: 100%;" alt="MozFest 2014 #ArtOfWeb"></a>

The meetup with [The Grid](http://thegrid.io) was incredible. We met [Forrest](http://twitter.com/forresto), [Jon Nordby](http://twitter.com/jononor) and [Henri Bergius](http://twitter.com/bergie). [Lionel Landwerlin](http://twitter.com/llandwerlin) joined us some days later. Those guys never stopped coding and inspiring us.

More robots on the way
===

While preparing the workshop we built a hack to Mirobot, making it possible to draw on walls. That's a work-in-progress and we are planning to keep improving and [documenting](http://automata.cc/drawbot) the process.

<a href="https://www.flickr.com/photos/auto_mata/15374301527" title="_MG_0062 by Vilson Vieira, on Flickr"><img src="https://farm6.staticflickr.com/5612/15374301527_724a160dc5_c.jpg" style="max-width: 100%;" alt="MozFest 2014 #ArtOfWeb"></a>

MozFest's ArtOfWeb
===

MozFest was fantastic. We met [Kat](http://twitter.com/codekat), [Eric](http://twitter.com/jenelson), [Paula](http://twitter.com/archiville), [Michelle](http://twitter.com/mishymishyme), [Allison](http://twitter.com/alliself), [Ginger](http://twitter.com/ossington), [Ricardo](http://twitter.com/rlaf) and all the other incredible "art phreaks" of the [#ArtOfWeb](mozfestartoftheweb.tumblr.com) track. [Ben Pirt](http://twitter.com/bjpirt), the Mirobot's creator, joined us in the art gallery and brought us his bots and kindness.

ArtOfWeb was a refuge during the chaotic creative tornado of MozFest. A place to chat, create and relax listening to [good music](http://soundcloud.com/alahaus/sets/mozfestartgallerymixl2) and enjoying art installations.

<center>
<blockquote class="twitter-tweet"><p>Yay, <a href="https://twitter.com/hashtag/Mozfest?src=hash">#Mozfest</a>: The <a href="https://twitter.com/hashtag/ARTOFWEB?src=hash">#ARTOFWEB</a> Gallery is packed w/ folks teaching + making open art together. Join now on Floor 2! <a href="http://t.co/bx4GMKXNUV">pic.twitter.com/bx4GMKXNUV</a></p>&mdash; Kat Braybrooke (@codekat) <a href="https://twitter.com/codekat/status/525971411924684800">25 October 2014</a></blockquote>
</center>

Our session did its job. We had people curious about the drawing robot, nice discussions about procedural *vs* flow-based programming and really nice collaborative drawings. 

<a href="https://www.flickr.com/photos/mozillaeu/15448050247" title="MozFest_26Oct_239 by Mozilla in Europe, on Flickr"><img src="https://farm6.staticflickr.com/5605/15448050247_b2c8149680_c.jpg" style="max-width: 100%;" alt="MozFest_26Oct_239"></a>

<a href="https://www.flickr.com/photos/mozillaeu/15634034695" title="MozFest_26Oct_237 by Mozilla in Europe, on Flickr"><img src="https://farm6.staticflickr.com/5597/15634034695_c70d960bc4_c.jpg" style="max-width: 100%;" alt="MozFest_26Oct_237"></a>

Henri recorded the following time-lapse video. A really nice way to capture this kind of session.

<iframe width="752" height="430" src="//www.youtube.com/embed/IMShMTn8yEU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

The festival ended up with a demo party where the most revealing feeling of collaboration and aesthetics experimentation took its place. Surrounded by curtains, music and projections, people and robots joined again to draw together.

<a href="https://www.flickr.com/photos/mozillaeu/15450606739" title="MozFest_26Oct_416 by Mozilla in Europe, on Flickr"><img src="https://farm6.staticflickr.com/5616/15450606739_d003e4175d_c.jpg" style="max-width: 100%;" alt="MozFest_26Oct_416"></a>

<a href="https://www.flickr.com/photos/neon_lobster/15481753580" title="Mozfest 2014 | #ARTOFWEB by Kat B, on Flickr"><img src="https://farm9.staticflickr.com/8267/15481753580_6b4a1b8612_c.jpg" style="max-width: 100%;" alt="Mozfest 2014 | #ARTOFWEB"></a>

<a href="https://www.flickr.com/photos/auto_mata/15474409768" title="MozFest 2014 #ArtOfWeb by Vilson Vieira, on Flickr"><img src="https://farm8.staticflickr.com/7547/15474409768_f2909fc342_c.jpg" style="max-width: 100%;" alt="MozFest 2014 #ArtOfWeb"></a>

We hope the next workshops are like this last experience and we'll try to make it happen more in the future. As well pointed by Kat, "[let's (re)make networked art](https://medium.com/@codekat/hello-world-lets-re-make-networked-art-6bb06913ac3a)".

We really want to thank and give a huge hug on all people we met. To our dear colleagues of [The Grid](http://thegrid.io), that made it possible to happen, thank you for all. To [Mozilla](http://mozilla.org), thank you to bring this amazing people together for a better Web of openness and opportunity. 

<a href="https://www.flickr.com/photos/neon_lobster/15480685669" title="Mozfest 2014 | #ARTOFWEB by Kat B, on Flickr"><img src="https://farm8.staticflickr.com/7578/15480685669_e0dac38c14_c.jpg" style="max-width: 100%;" alt="Mozfest 2014 | #ARTOFWEB"></a>

Looking forward to keep *phreaking* art and meet you all again this year!

*Photos by [Kat Braybrooke](https://www.flickr.com/photos/neon_lobster/), [Mozilla in Europe](https://www.flickr.com/photos/mozillaeu/) and [Vilson Vieira](https://www.flickr.com/photos/auto_mata/).*

