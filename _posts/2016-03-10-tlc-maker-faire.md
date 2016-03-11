--- 
layout: post
title: The Learning Center school Maker Faire
author: forresto
tags: 
- meemoo
- imgur
- gifv
---

Meemoo lives!

We were invited to set up a stop-motion animation station at the local school's Maker Faire. A lot of people came to try their hand at making stop-motion loops. A few people had done stop-motion before, so I was able to pitch the hackability aspect to them. I think that the Maker Faire surroundings helped people understand the benefit of being able to hack creative apps.

One young person asked how to wire in [sound effects](http://www.leshylabs.com/apps/sfMaker/)... that's a module that needs to be made!

![aperture](https://i.imgur.com/lLByoNc.gif) ![alien olive flower](https://i.imgur.com/eVcMcw6.gif) ![](https://i.imgur.com/53odKlP.gif) ![shape dance](https://i.imgur.com/cqii4Du.gif) ![blink](https://i.imgur.com/47XHGD0.gif) ![jumping tailless](https://i.imgur.com/oBzROxq.gif) ![smile frown](https://i.imgur.com/EYysC6P.gif) ![fire flower](https://i.imgur.com/jbOQxEB.gif) 

<video preload="auto" autoplay="autoplay" loop="loop" style="width: 300px; height: 300px;">
  <source src="//i.imgur.com/cHx8TV4.mp4" type="video/mp4"></source>
  <source src="//i.imgur.com/cHx8TV4.webm" type="video/webm"></source>
</video>

## Update

### Imgur

I jumped back into Meemoo a bit to change how images are stored to the web. Imgur has a funny GIFV format that's actually a looping mp4/webm video. (If you see a `.gifv` link you can change it to `.mp4` or `.webm`.) This is nice for longer animations with big filesizes. Meemoo still has to save and upload the animation as GIF, so the process is lossy, but still an improvement.

You can see the looping video made by Imgur in the last loop above.

### HTTPS everywhere

Chrome started blocking `getUserMedia` (webcam) access on non-https web apps. Meemoo will now redirect you from `http:` to `https:` so you should not run into that issue.
