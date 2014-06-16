--- 
layout: post
title: An introduction to noflo-canvas
tags: 
- gsoc
- gsoc2014
- google
- mozilla
- fbp
- noflo
- flowhub
---

During the last weeks we were working on [noflo-canvas](http://github.com/noflo/noflo-canvas) and experimenting with it. Here I describe some of those developments and how we ended with the current *noflo-canvas* design.

Arrays and grids
----------------

Following Forrest suggestions we have designed *noflo-canvas* inspired by [Grasshopper](http://www.grasshopper3d.com/), an algorithmic modeling tool for [Rhino](http://www.rhino3d.com/).
In *Grasshopper* you can create an unique point or [an array of points](http://vimeopro.com/rhino/grasshopper-getting-started-by-david-rutten/video/79844298) using the same component.
In *noflo-canvas*, you have components like `MakePoint` which receives an unique pair of *(x,y)* coordinates or an array of them.

<img src="http://meemoo.org/images/oneXarray.gif" width="730" />

When given an array of x and y coordinates, `MakePoint` makes one point *for each pair* of x and y. It resembles [Spreads](http://vvvv.org/documentation/tutorial-spreads) from [VVVV](http://vvvv.org). 

Another possibility is to create one point *for each possible combinations* of x and y. `MakeGrid` does that and resembles the *cross product* between two vectors (also resembles [Cross](http://vvvv.org/documentation/cross-%282d%29) from *VVVV*). This example makes it easy to understand:

<img src="http://meemoo.org/images/pointsXgrid.gif" width="730" />

Such patterns are powerful to algorithmic design because we can create complex shapes using few components. Imagine how many `MakePoint`s are necessary to reproduce the same of just one `MakeGrid`.

Lazy evaluation
---------------

Another interesting detail in *noflo-canvas* design is how drawing commands are evaluated. `Draw` is the main component in *noflo-canvas* and all the magic happens inside it. Take the following program as an example:

![Example program](http://meemoo.org/images/example-commands.png)

`Draw` receives these commands:

```js
    [{"type": "fill", "items":
         {"type": "circle", "center":
             {"type": "point", "x": 100, "y": 100}, 
             "radius": 100},
         "fillstyle":"#00ff00"}] 
```

If we remove JSON stuff we get this *Lispy* representation:

```lisp
    (fill (circle (point 100 100)
                  100)
          "#00ff00")
```

Lisp was a great inspiration not only for how we represent commands but on how we evaluate them. `Draw` parses received commands and applies the respective Canvas 2d method on its arguments. 

The entire process remembers a *lazy evaluator*: each component just has to generate a specific instruction like `{"type": "point", "x": 100, "y": 100}` and send it to the target component. It repeats until those commands are finally received by `Draw` that evalutes them. 

Connection ordering is important in those situations because we want commands evaluated in specific order: "I want to clean the canvas first, then draw a circle, then ...". NoFlo [supports](https://github.com/noflo/noflo/issues/128) connection ordering which makes this design possible.

This *lazy evaluation pattern* is becoming useful in FBP, specially when you have to deal with an independent dataflow like the ones of Canvas 2d or Web Audio.

Running on backend
------------------

Thanks to [node-canvas](https://github.com/LearnBoost/node-canvas), it is also possible to use *noflo-canvas* on *NoFlo* programs running on *Node.js*. *Flowhub* has helpful [documentation](http://flowhub.io/documentation/getting-started-node/) about how to connect *Flowhub* on your *Node.js* runtime. 

*Node-canvas* uses [Cairo](http://cairographics.org/) as its graphics toolkit and
we are using it to generate images with high dimensions on backend. Ready-to-use images like that are useful for caching. We are currently reporting experiments of this use of *noflo-canvas* in [this issue](https://github.com/noflo/noflo-canvas/issues/23).

