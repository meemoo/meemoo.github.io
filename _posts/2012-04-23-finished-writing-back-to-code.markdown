--- 
layout: post
title: Finished writing, now back to the code
tags: 
- thesis
- ux
---

Meemoo started at a prototype in the January 2011 Interactive Cinema class at Media Lab Helsinki. It looked quite different back then, and had one function: cutting around triggers of multiple web video players.

<a href="http://www.flickr.com/photos/forresto/5353762681/" title="ytsq alfalfa 0.1 by fo.ol, on Flickr"><img src="http://farm6.staticflickr.com/5287/5353762681_c88925eb59_n.jpg" width="320" height="236" alt="ytsq alfalfa 0.1"></a><object type="application/x-shockwave-flash" width="320" height="240" data="http://www.flickr.com/apps/video/stewart.swf?v=109786" classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000"> <param name="flashvars" value="intl_lang=en-us&photo_secret=7a5a844217&photo_id=5368822026"></param> <param name="movie" value="http://www.flickr.com/apps/video/stewart.swf?v=109786"></param> <param name="bgcolor" value="#000000"></param> <param name="allowFullScreen" value="true"></param><embed type="application/x-shockwave-flash" src="http://www.flickr.com/apps/video/stewart.swf?v=109786" bgcolor="#000000" allowfullscreen="true" flashvars="intl_lang=en-us&photo_secret=7a5a844217&photo_id=5368822026" height="240" width="320"></embed></object>

As this project progressed, I wanted the videos to be in a different browser widow than the controllers. I made a text format for control signals to be sent between windows with window.postMessage(). This browser function could only be used to send strings, but around the middle of the year (Gecko 6.0) the function expanded to allow all kinds of data to be passed from window to window. At this point the *web video remixer* idea became the *web remixer remixer* (the metamedium metaremixer).

I realized that this idea could encompass most of my web/interactive experiments, so I made it my thesis project. In the written thesis I looked at *design for hackability*, and how that could be positive for education. 

Other services for learning code (like Code Academy) start with "this is a var." You complete the lessons, get badges, and maybe get a fundamental concept of programming, but what can you really do with it? Meemoo starts with "this is a stop motion application." Use it as is, or look under the hood and hack it if you like. I think that this design for hackability feeds curiosity and encourages learning in a more natural way, much closer to how I and many other actually learned coding.

At every step in the process, people can instantly share their apps and creations for the world to see and modify. Or not, and keep it all local.

Lev Vygotsky said that learning happens in the space between what can do by ourselves and what we can do with guidance from someone with more skill. He called this the "zone of proximal development." The Internet is the ultimate manifestation of this metaphorical space. Most web coders learned with "view source," and this project seeks to extend this concept to creative web apps.

Feel free to read the full version of the thesis:  
[![Meemoo: hackable web app framework thesis cover](http://meemoo.org/images/thesis-cover.png)](http://meemoo.org/files/ForrestOliphant-MeemooThesis-web.pdf) (1.6MB PDF)

<img src="http://meemoo.org/images/Screen-shot-2012-04-23-plugends.png" alt="draggable plug ends" style="float:right;margin-left:1em;"/>Since submitting the paper I have been happy to get back into the code. The biggest change to the UX has been with the wires, adding draggable plug ends. You can see this in action on [the Processing example](http://meemoo.org/iframework/#/example/processing), dragging a wire from one reflow module to the other.

Meemoo has also accepted it's first code from another developer! This is a big moment for any open source project. [Automata](http://automata.cc/) added the foundations of a history stack, so if you delete a module you can press ctrl-z to undo the deletion.