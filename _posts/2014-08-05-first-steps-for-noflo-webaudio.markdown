--- 
layout: post
title: First steps for noflo-webaudio
tags: 
- gsoc
- gsoc2014
- google
- mozilla
- fbp
- noflo
- flowhub
- webaudio
- assembly
---

Before any word, let's make some noise. You can play yourself with this demo [clicking here](http://app.flowhub.io/#example/04847249319d2326fa92).

<iframe class="vine-embed" src="https://vine.co/v/ME1wdVX16iB/embed/simple?audio=1" width="480" height="480" frameborder="0"></iframe><script async src="//platform.vine.co/static/scripts/embed.js" charset="utf-8"></script>

This simple demo was presented by Forrest in his last [Assembly
talk](http://www.forresto.com/2014/08/the-toybox-and-the-toolbox/). It
illustrates how we are combining audio and visuals in NoFlo. 

It uses [noflo-webaudio](http://github.com/automata/noflo-webaudio), our
wrapper library to the Web Audio API. [Web Audio
API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API) defines a
"signal-flow graph" where audio sources connect to processors and can be
manipulated on a sample-accurate base. How to map such "signal-flow graph" to
NoFlo? Having worked with [noflo-canvas](http://github.com/noflo/noflo-canvas)
we wanted to explore if the same design and semantics used on it could work
with Web Audio.

In [noflo-canvas](http://github.com/noflo/noflo-canvas), each component
generates lispy commands that are lazy-evaluated in a complex component
(*Draw*). We are doing the same for [noflo-
webaudio](http://github.com/automata/noflo-webaudio). In this way, we have
some components like *Oscillator* and *Gain* that sends lispy commands
like the following:

```
{"type": "gain", 
 "input": [{"type": "oscillator", "frequency": 440.0},
           {"type": "oscillator", "frequency": 660.0}]
 0.8}
```

which, again, maps to a lispy representation like

```
(gain ((oscillator 440)
       (oscillator 660))
      0.8)
```

Each time a component input (like *Oscillator*'s frequency) changes, it
sends an updated command as its output. The *Play* component gets all those
commands and takes care of how to plug them together and update the parameters
when needed.

The major difference is that [noflo-canvas](http://github.com/noflo/noflo-
canvas) follows a "redraw the entire canvas everytime" paradigm while [noflo-
webaudio](http://github.com/automata/noflo-webaudio) can't reconnect all the
audio nodes everytime: most of the time the audio graph doesn't change, just
the parameters. So *Play* should be smart enough to walk through the
received commands and decide which should be reconnected (like *Oscillators* and
*AudioFile*) and which should has just its parameter updated.

The JSON representation of such signal-flow graphs remembers a declarative
paradigm. We are exploring a Web Audio library called
[Flocking](http://flockingjs.org/) which makes possible to define signal-flow
graphs in a declarative way that maps directly in the way we are dealing with
[noflo-canvas](http://github.com/noflo/noflo-canvas) and [noflo-
webaudio](http://github.com/automata/noflo-webaudio) for now. So we should
have an usable [noflo-flocking](http://github.com/automata/noflo-flocking)
soon.

We already have support for Web Audio API in Android (both Firefox and Chrome)
so we can expect mobile music instruments in NoFlo in a near future!

<iframe src="//player.vimeo.com/video/102201555?title=0&amp;byline=0&amp;portrait=0&amp;color=c9ff23" width="800" height="535" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

We started the [noflo-three](http://github.com/automata/noflo-three)
components library to [Three.js](http://threejs.org) in this meanwhile too. I
guess the same design we used for [noflo- webaudio](http://github.com/automata
/noflo-webaudio) can be applied to a scene graph like that used in
[Three.js](http://threejs.org). We are also making some nice generative stuff
with [noflo-canvas](http://github.com/noflo/noflo-canvas) that we will love to
share soon.
