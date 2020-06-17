---
layout: post
title: WebGL basics
---

For me, WebGL as always been something that sounds exciting, but in reality never find a use for. Here I try to summarize the basics.

WebGL is basically a version of OpenGL that runs in the browser. It starts with you creating a `canvas` element in your DOM, and then initialize a WebGL context on it. Much like how most OpenGL programs are written in C/C++, you write all your WebGL method calls in Javascript, which accesses the underlying WebGL state machine. [This](https://webgl2fundamentals.org/webgl/lessons/resources/webgl-state-diagram.html) is a great illustration of how it works under the hood, and is also a great way to visualize how OpenGL and graphics programming work in general.

## From GPU to Screen

At a very simple level, a GPU takes in data about vertices, run that through the vertex shader to output vertices that should be somewhere in your canvas; then for every pixel/fragment (not interchangeable but conceptually similar) on the canvas, it runs through the fragment shader to get an output color. Therefore, vertex shader and fragment shader are the two programs that actually gets executed on the GPU. in WebGL, you give javascript these two programs usually in the form of a String object, which gets compiled and linked by the CPU, and then loaded to the GPU. WebGL2 adds support for Compute Shaders, which can operate on other things besides vertices and fragments, and [this](https://github.com/9ballsyndrome/WebGL_Compute_shader) project has some interesting showcases of projects using Compute Shader.

## Limitations

Recent GPU advancements have been orders of magnitude faster than CPU, but few has adopted WebGL in production websites. I think the main limitations are Inter-operability and ease of development. The most annoying thing is that your WebGL rendering is limited to be on the canvas, and inside the canvas you do not get any information about the outside world, like how other HTML elements are rendered and aligned, or even get input from the user. You have to manually work with the communication between the two, and it can be quite frustrating because we are used to letting the browser handle how the DOM is rendered, and suddenly we need to be a lot more specific about alignment and positioning if we don't want responsive layout to mess up your WebGL graphics. You also have to work with lack of native debugging and the different syntax of WebGL programs, and the performance benefits are only apparent when you are operating on large enough data that the overhead of compiling WebGL programs and loading data to GPU becomes insignificant.

## Frameworks

If you want to take the abstraction up a level, we have [Three.js](https://threejs.org), which is a nice middle-ground between writing OpenGL method calls and using a full Game Engine. It handles basic geometry and simple shaders for you so you can write most things in Javascript. Traditional game engines like Unity also has support for WebGL, but then you are completely leaving the realm of web programming.
