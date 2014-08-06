--- 
layout: post
title: Next Steps
author: forresto
tags: 
- future
- dataflow
---

In addition to the new modules for MozFest, I have been working on a rewrite of Meemoo's graphing interface.

## Dataflow

![dataflow](http://meemoo.org/images/dataflow-2012-11-28.png)

[Dataflow](https://github.com/meemoo/dataflow) is a total rewrite of Meemoo's graph editing interface. I started this project from scratch in order to have a clean start, implementing all that I have learned in the past year. Some of the goals of this rewrite:

* __Better separation of data models and views.__ Currently, there is a lot of spaghetti code that ties models and views. Now views just listen to ```change:``` events in the models. Currently, canvases are attached to views. In the new version they will be attached to the model, so that different views can show smaller and/or lower-fps preview versions of the full canvas.
* <img src="http://meemoo.org/images/meemoo-illo-by-jyri-pieniniemi-400.png" style="float:right;margin-left:10px;width:30%"> This will help make it possible to design and define "__app views__" for Meemoo graphs. The illustration of a box with UI elements on the lid that can be unscrewed to see the "routing view" below is how Meemoo apps will work. You can use the app as it is designed, but if you want to see/hack how it works you can always unscrew the box, hack, and save your changes.
* __Submodules__ will be a way to encapsulate a graph into a module. You'll be able to define a graph's inputs and outputs and then load that graph as a module into any other graph. The concept is a bit complicated to explain in words, but it will result in less visual confusion in complicated graphs.
* __Plugins__ encapsulate functionality, making it easier to manage the code.
* Dataflow is available for other projects to use as well, since it is totally separated from Meemoo's code. The next version of Meemoo will extend Dataflow's design and module library.

## Hub

I have been working with the limitation of keeping Meemoo 100% client-side. In the next months I will be testing an early version of a "Meemoo Hub" (name to be decided) with features for sharing and remixing apps, modules, and images.