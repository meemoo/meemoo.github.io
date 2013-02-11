--- 
layout: post
title: Simple live code editor; JavaScript turtle graphics to SVG
tags: 
- turtle graphics
- svg
- live code editor
---

## JavaScript + &lt;canvas&gt;

I recently taught [Software Studies for Designers](http://softwarestudies.mlog.taik.fi/) at Media Lab Helsinki. It was a good place to experiment with a group of beginner coders. We didn't use Meemoo other than to demo what is possible with HTML. It was good for me to step away from the Meemoo code base for a few days and get back to coding from a blank slate. 

We started with Khan Academy's [live editor](http://www.khanacademy.org/cs/ring-toy/1321912374), which has some nice features for experimenting with code. Khan Academy uses Processing.js. Processing was great when it was hard to draw on the screen, but now with the HTML <code>&lt;canvas&gt;</code> it isn't so hard. Most 2D drawing commands are quite similar, and there are some things, like working with color, that are easier to code directly. 

[Here are some JavaScript examples](https://github.com/forresto/web-interactive-workshop/#processing-not-processing) that will get you started drawing on the canvas as easily as with Processing. This is not a library: just use the parts you need!

## JavaScript turtle graphics → SVG

One of the things that I experimented with is making LOGO-like vector turtle graphics. Why? I wanted to do some algorithmic experiments with the laser cutter in Aalto's FabLab, and turtle graphics directly translates to the motion of the laser.

LOGO was the first programming language [designed for kids](http://www.amazon.com/The-Childrens-Machine-Rethinking-Computer/dp/0465010636/). For drawing on screen, it is a little irrelevant, as canvas' `strokeRect(x, y, w, h)` is easier than `FORWARD 100 RIGHT 90 FORWARD 100 RIGHT 90 FORWARD 100 RIGHT 90 FORWARD 100`. But I think that these turtle graphics commands still have a place when they correspond to the real-world motion of a physical drawing robot (or laser cutter, CNC, 3D printer head, etc.).

At first I was doing the save-file/change-window/refresh-browser dance for every change, but tools like Khan's editor and [Mozilla Thimble](https://thimble.webmaker.org/p/fyxg/edit) have given me the expectation that my creative coding should have immediate feedback. So I set out to make my own editor.

[![LASER TURTLE](http://meemoo.org/images/LASER-TURTLE.png)](http://forresto.github.com/turtle-svg/#code/jY7LDoIwEEX3/Yq7LIlIwWCMRFcuXfoDDZliEyimlLow/LsFNUaN0d2cM3ceSYKdlWdIWCp722lP6E6ypFjputamQrCe1sxLi46qhozbk6ncERukecFUb0qnW4PeaMe1IytHjHBhgFZ4KmwhbhpvYcRIo2JqWC7mWX6HrynFX175Ff9n6cAG1rSeDi1fiBkyEazrrRk5WQWY5pah+Dz+aF0B) 
*Shoutout to [Martin Schneider](https://github.com/craftoid) for the code contributions.*

<a href="http://www.flickr.com/photos/forresto/8447807698/" title="cross-folded by fo.ol, on Flickr"><img src="http://farm9.staticflickr.com/8373/8447807698_d61b0707ba.jpg" width="375" height="500" alt="cross-folded" align="right" style="margin-left:1em;" /></a> It was really exciting to see the laser follow the my coded paths with speed and precision, making my algorithm into a physical thing.

The editor has a few features that I think are nice:

* Uses JavaScript, the most ubiquitous language, and outputs web-standard SVG.
* Uses [Ace](http://ace.ajax.org/), which checks the code with jsHint before attempting to evaluate it.
* Uses a worker to evaluate the script, so `while(true){}` makes the worker hang, not the page. This method is inspired by [John Resig's talk](http://ejohn.org/blog/talk-khan-academy-computer-science/) about Khan' editor.
* Compresses and saves code for sharing in the URL hash, no server or API needed. I first saw this method in [Mr.doob's html editor](https://github.com/mrdoob/htmleditor).
* Embeds the code and a link to the editor in a <code>&lt;!-- comment --&gt;</code> in the exported SVG.

It is pretty easy to piece together coding toys and tools like this, focused on a certain task. From here I'm going to figure out how to do live coding like this directly in Meemoo.
