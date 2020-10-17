--- 
layout: post
title: Thinking about Meemoo 2.0
author: forresto
tags: 
- meemoo
- plans
---

Meemoo lives!

This is how I started my last post (2016). I'm happy that Meemoo continues to work whenever I spin it up with an idea.

<a href="https://app.meemoo.org/#gist/e8bba8fe01e4c8df2327214b2773e17f"><img alt="meemoo app with video clips of me counting 1 2 3 4 in individual loops" src="https://meemoo.org/images/meemoo-1234.gif" width="628" height="597" /></a>

(Saving to gist needs some help. Github probably turned off anonymous Gist creation, or changed that API. Other than that, I think that this project is stable enough to keep working. As long as I pay for the domain registration.)

Meemoo as a project and thesis always had these layers in mind:

1. A layer on top to build mini apps with UI, to encapsulate the dataflow flow view.
2. (Existing) data flow view.
3. A layer beneath, to see, fork, and/or edit the source code of any module. 

I commissioned this illustration to show how these layers would unfold:

[![meemoo layers](https://meemoo.org/images/meemoo-illo-by-jyri-pieniniemi-400.png)](https://meemoo.org/images/meemoo-illo-by-jyri-pieniniemi.png)

With this sequence of layers in the Meemoo ecosystem, I imagined guiding folks down the rabbit hole towards "learning to code."

1. Somebody sees an eye-catching image or animation out on the internet somewhere.
2. They ask the author "what app did you use to make that?"
3. They get a link to the Meemoo app, and use it to make and share their own images. (Layer 1)
4. They might stop there, but they might notice the invitation to hack the app, and see the data flow behind the UI. (Layer 2)
5. Once they understand how hacking the app works, and see the library of available modules, they might want to hack a module or make their own with code. (Layer 3)

There was also supposed to be a community site for sharing and forking these mini apps. Why did Meemoo stall with just the dataflow layer? Probably some combination of starting a family, running out of grant funding, and getting a day job. Standing up an online community is a major obligation in terms of moderation. I felt like making a community without committing the resources to make it a safe and good learning environment would be worse than not making the community at all. Meemoo hasn't gained traction or a life of its own, which I've decided to be OK with.

Also it reached a local maxima of being "fun enough," which isn't a bad thing.

## Meemoo 2.0?

So what is there to do at this point? Will there be a Meemoo 2.0?

Meemoo is built on Backbone and jQuery/UI, which are fairly obsolete. On the other hand, they are simple, stable, and _work_.

A lot has changed in web development in the 9 years since my first commits. In the first version, the camera module was powered by Flash, because the [web standards for accessing a device camera](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia) hadn't shipped yet. As standards like this shipped to the web platform, I was able to remove code and complexity. 

Meemoo's "Hello World" app is a camera module that sends images to an image stack, that can compile an animated GIF.

<iframe allow="camera" src="https://app.meemoo.org/#example/cam2gif" style="width: 100%; height: 480px;"></iframe>

[Meemoo cam2gif](https://app.meemoo.org/#example/cam2gif)

If Meemoo modules were packaged as Web Components, it would be possible to build this app with a few lines of code in any web page:

```html
  <meemoo-cam id="cam" />
  <meemoo-animation id="animation" />
  <meemoo-link from="cam" out="image" to="animation" in="image" />
```

By taking the module code out of the dataflow environment, it might be possible to jump from interface to code more easily. The dataflow environment wouldn't be needed to style or edit the app, but it could be loaded as a layer on top of (or under) the published app.

I'm not sure if Web Components are really the best abstraction for what I want to do here. There are at least [43 ways to build Web Components](https://webcomponents.dev/blog/all-the-ways-to-make-a-web-component/), that have tradoffs with authoring complexity and compatibility with other frameworks. This has caused some analysis paralysis on my part.

I'm also not sure if "reusing Meemoo components" should be my first design goal with future Meemoo work.

## So what is the web missing?

Several of my web developer peers express fondness for Flash, as it existed around 2002. I credit the combination of vector editing, timeline animation, and scripting with my initial love for creative coding. Are there any environments that combine separate modalities like this now? What about other metaphors, like spreadsheets for tabular data editing and visualization?

I've been thinking about designing a "thicker" Meemoo module with a full-featured animation timeline. Maybe also a mini spreadsheet module. 

But is dataflow the correct metaphor to be coordinating these modalities?

Could it be that the "correct" metaphor is just a webpage, with any framework, or none at all? 

## "Exposing ports"

Meemoo components announce their inports and outports: what type of data they expect as input, and output. This is something that most component systems lack, including React and standard Web Components.

This enables a few things:
* UI for tweaking initial state of components
* Wiring hints for compatible data

Do any other component systems expose "data types" like this? Is there room for some kind of standard around this?

## HMU

After several years on the backburner, I'd like to find Meemoo's next step. Got ideas? 👉 [Talk in issue #145](https://github.com/meemoo/meemooapp/issues/145)
