---
layout: post
title: React Crypto Messenger Pt. 1
date: 2017-07-19 10:44
categories:
---

This tutorial is not meant to go over all the fine grain details of getting up and going on RN, there are plenty of wonderful tutorials on that. 
I want to show how we can quickly prototype a concept using RN and Ruby on Rails 5.  

## Setup

Upon starting the tutorial I ran into a problem with the installation of RN.
The solution was to set the node_modules/.bin in my path, which was found in ~/.config/yarn/global/

### Project Layout

This is perhaps the most subjective part of all and for anyone new to RN projects this can be overwhelming. And if you are anything like me I want to make sure I am setting things.
 
I have been walking through a tutorial on react native which is quite nice http://learn.handlebarlabs.com/courses/175915/lectures

> Note: Things I dislike about the node environment. I know the idea of a bunch of components all get plugged together to and all can be configured differently is a grand idea from 
a modularity stand point but the concepts of npm are just plain overwhelming. There are som many packages where would one even know where to start? It is slightly rediculous and quite frankly
frustrating.  


### Tools

  1. Visual Studio
    1. ESLint
    1. Flow Support for VS Code
    1. React-Native-Tools

### Callouts 

In the root of the directory there are two distinct files one is `index.android.js` and `index.ios.js` both of which are the entry point for each of the applications.

> Used [this blog](http://artsy.github.io/blog/2017/07/06/React-Native-for-iOS-devs/) as a great getting started tutorial\

> Fantastic [resource](http://www.reactnativeexpress.com) 
