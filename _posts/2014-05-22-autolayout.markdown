--- 
layout: post
title: Auto layout
tags: 
- fbp
- noflo
- flowhub
- autolayout
---

One issue around
[Flow Based Programming](http://www.jpaulmorrison.com/fbp/) is the
amount of time we spend dragging-and-dropping boxes to get the most
proper layout.

On a text-based programming language we have at least the left-right
and top-down directions to follow. However, in a 2D FBP canvas those
nodes can be anywhere and the graph can become really messy. 

![Graph layouts can become really messy, requiring lots of time of
dragging and dropping boxes to organize them in a proper layout](http://meemoo.org/images/pd.png)

A proper layout is crucial to make a graph easy to read to both its
creator and anyone else (*the graph is the documentation*).

So we want easy to read graph layouts but we don't want to do it by
hand. Auto layout to the rescue!

<img src="http://meemoo.org/images/autolayout-action.gif"
style="width: 730px;" alt="KLayJS in action" />

Last months
[we were researching](https://github.com/noflo/noflo-ui/issues/53)
auto layout algorithms on [The Grid](http://thegrid.io). There are
plenty of techniques and features we can expect from those algorithms
and implementations. At the same time, in FBP environments like
[Flowhub](http://flowhub.io) / [Meemoo](http://meemoo.org) we have
many constraints to consider: port ordering, components as groups or
subgraphs, input and output "nodes" and so on.

We ended up using a layer-based hierarchical algorithm called
[KLay Layered](http://rtsys.informatik.uni-kiel.de/confluence/display/KIELER/KLay+Layered)
which is originally written in Java. It is part of the
[KIELER Project](http://rtsys.informatik.uni-kiel.de/confluence/display/KIELER/Overview)
from [Kiel University](http://uni-kiel.de).

In collaboration with the amazing KIELER / KLay team we developed
[KLayJS](http://rtsys.informatik.uni-kiel.de/confluence/pages/viewpage.action?pageId=8651755),
a JavaScript interface to KLay using
[GWT's JSNI](http://www.gwtproject.org/doc/latest/DevGuideCodingBasicsJSNI.html). Now
we can run the original layout algorithm inside a Web Worker and get
rid of all the
[GWT crazyness](https://github.com/the-grid/the-graph/pull/146#issuecomment-42935253). There
is already a [Bower component](http://github.com/automata/klay-js) to
this interface, so you can use that on your own graphs.

The auto layout feature provided by KlayJS is currently available on
[Flowhub](http://app.flowhub.io): it's the *magic stick* you can weave
anytime you want to organize your graph.

![Auto layout in Flowhub](http://meemoo.org/images/autolayout-ui.gif)

While using auto layout we are identifying two scenarios where it is
becoming really useful:

1. When creating a graph from scratch you don't have to think where is
   the best place to drop your components. Keep focus on problem
   solving and just call auto layout everytime you need to align and
   organize the components;

2. Auto layout works better when you have
   [grouped components](https://github.com/noflo/noflo-ui/issues/53#issuecomment-36917555). So
   it motivates you to keep grouping components together, making it
   easy to read and document.

Auto layout is not perfect, many times edges crosses and nodes are not
well arranged, but it is a handful tool on FBP environments like
[Flowhub](http://flowhub.io) / [Meemoo](http://meemoo.org) and we want
to keep
[improving it](https://github.com/the-grid/the-graph/issues/85).
