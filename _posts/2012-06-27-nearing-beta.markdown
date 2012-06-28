--- 
layout: post
title: Nearing beta
tags: 
- progress
- ux
- modules
- mozilla
- nokia
- aalto
---

I presented Meemoo at the [Masters of Aalto](http://moa.aalto.fi/2012/en/masters/forrest-oliphant/) show and [Media Lab Helsinki Demo Day](http://mlab.taik.fi/news/2012/05/21/media-lab-demo-day-23-5-2012-programme-here/). Here are some animations made by event-goers:

![hats](http://i.imgur.com/nLFKo.gif) ![smooch](http://i.imgur.com/y2GKs.gif)

At these events I had the chance to do some (covert) user testing, and see how people interact with it on their first try. I noticed that many people's first interaction is disconnecting all the wires. Then they seem surprised that it doesn't do anything! Obviously this points to a design flaw that I need to address. The wires are colorful and draw attention before the buttons that send data over the wires. A quick, clear, guided tutorial to introduce basic Meemoo concepts will go a long way.

One of my thesis evaluators works for Nokia Design, and invited me to present there. I got some encouraging feedback from that group.

I have been working on the modules and instructions for a challenge for Mozilla Summer Code Party. The [Meemoo challenge](https://wiki.mozilla.org/Webmakers/Projects/MeemooClock-DIY) will present two clock apps for participants to experiment and hack. [My own hack](http://meemoo.org/iframework/#gist/2930234) of the concept is pretty far out.

Some major changes:

* Module library is sorted into collapsible categories for easier navigation
* Drag modules library to position in graph
* New modules:
    * Util: color-hsla, color-rgba, math
    * Image: text, transform, combine
    * Draw: rectangle, circle
+ Save app to browser's localStorage (private)
+ Save app to [gist](https://gist.github.com/) (public)

Many of these features have been on the [to-do list](https://github.com/meemoo/iframework/issues) for some time. Behind the scenes there was a pretty major refactoring of code as well. With these done, it will be much easier to start making the bigger changes that are coming...