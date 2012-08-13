--- 
layout: post
title: 60fps is a good number of fps
tags: 
- progress
- native
---

### Progress

In the last post I mentioned bigger changes coming, and now I'm ready to show some of them.

The biggest change in the framework was making the foundation of "native" nodes. Now I am starting to port some of the old iframe nodes to this new way of doing things.

Until now, all modules were loaded as iframes. I started with this architecture as a way to keep everything distributed, so that anybody could make their own modules. This is still possible, but as I made more complicated apps I realized that there should be a library of basic node types that are loaded in the same context as the framework. Loading an entire DOM to do one math calculation isn't very efficient.

Thanks to some of the profiling techniques outlined by Paul Irish in the video tutorial [Chrome DevTools Timeline's New Frame Mode](http://www.youtube.com/watch?v=Vp524yo0p44), I was able to optimize how animation is done. Everything that changes the display is triggered from a single [requestAnimationFrame](https://developer.mozilla.org/en-US/docs/DOM/window.requestAnimationFrame) call from the GraphView level to each native node. 

With iframe nodes, this recursive drawing fractal was running at 10-15fps. While it ran on my iPod touch, it seemed to be taking 2-3 seconds per frame. I was expecting to see a speedup with native nodes, but I was pleasantly surprised when the animation was suddenly blazing at 60fps. 60fps was my "maybe if the browser gods smile sure would be nice" goal. Even adding a few more levels of recursive image transforms I have not been able to get this particular composition below 60fps (in Chrome). The native version runs at 9fps on my iPod Touch.

<img src="http://meemoo.org/images/recursive-1.jpg" alt="recursive square" width="370" height="306"> <img src="http://meemoo.org/images/recursive-2.jpg" alt="recursive square" width="370" height="306">  
[one square, drawn recursively](http://meemoo.org/iframework/#gist/3124854)

Different tools encourage different kinds of creative exploration. With tools like Photoshop, it is impossible to put a layer inside of itself. Recursive image transforming is something that could be programmed without Meemoo, but I never thought of trying it. Plugging boxes together with wires is quite different than writing code. 

Another design motivation behind Meemoo is the ability to quickly plug different tools together. The above fractal uses a simple square as the base image, but I wanted to try drawing the base image. Vilson Viera had made a Meemoo module fork of mr.doob's Harmony procedural drawing tool (Harmony was originally based on Ze Frank's [Scribbler](http://www.zefrank.com/scribbler/about.html) algorithms, so the algorithms live on). After a little bit of wiring and sketching, I liked what I saw. I added some animation to the transform variables, and got some interesting and life-like forms, flexing and recursing at 60fps.  

<img src="http://meemoo.org/images/recursive-harmony-1.jpg" alt="recursive sketch" width="370" height="306"> <img src="http://meemoo.org/images/recursive-harmony-2.jpg" alt="recursive square" width="370" height="306">  
[Try it!](http://meemoo.org/iframework/#gist/3338251)

These recursive drawing experiments were inspired in part by Toby Schachman's [Recursive Drawing](http://recursivedrawing.com/) project. I should make it possible to directly manipulate the transform variables (move, scale, rotate) in each module. This will allow more fluid and direct experimentation.

### Next steps

Steps from here: the "app view," more native image nodes, [Seriously.js](http://seriouslyjs.org/) WebGL image effects, Web Audio API nodes, and the foundations of the [community site](https://github.com/meemoo/meemoo-hub/wiki). Planning and code contributions welcome!

### Say hi

Look for me ([@forresto](https://twitter.com/forresto)) at the Mozilla booth at [Campus Party](https://www.campus-party.eu/2012/) in Berlin August 21-26.

### Your Meemoo

We have a [gallery page](http://meemoo.org/hack-our-apps/)! If you're making modules or apps, get in touch so we can show off your stuff.
