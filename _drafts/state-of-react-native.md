---
layout: post
title: State of React Native
date: 2017-07-27 08:52
categories:
---

This blog post is not 100% directed towards React Native but on the 
entire stack on RN. I recently started working on a project which 
explores React Native. I followed a wonderful tutorial 
[TODO: insert link] which, at the time, was only a couple months old.
This should not seem like a big deal but in the world of node it is and 
that is exactly what I want to touch on today.

## My Take on Native Development

I have been developing both iOS and Android native mobile applications for a couple years now and the thing I found the most difficult to overcome was the "That's the way you do it" mentality. 
*cough*Apple*cough*. There are a lot of snippets and example applications that illustrate how one could build an application. However, the issues that they do not emphasize, and arguably most important, are, testability, which leads to architecture and also includes project structure.
The promotion of good practices such as Separation of Concerns[TODO: insert link] is not conveyed to the audience. For anyone that has done any iOS development you have already come across the issues of Massive View Controllers.
Not only are good practices not promoted but actually implementing a good architecture is difficult. There are many different attempts at clean architecture but none are revered as the defecto. In short, it is exhausting being a good developer while writing native applications.  

## Getting Started

For anyone new to Nodejs the ecosystem, simply put, is a bunch of small packages plugged together to create a larger package. With that comes a lot of decisions to make. Most of the decisions have already been made for you because of the dependencies of your dependencies 
but you still need to make a choice on what dependencies you will be using. If you are like me, you will probably want to vet out your dependencies before using them. So, let's use a real example. Let's say we want to use a package for forms in our new react redux. 
Go to [npm](https://www.npmjs.com/search?q=keywords:react-redux%20form&page=1&ranking=optimal) and search react redux forms, I'll wait. How many results did you get? When I did it at the time of writing this post it was 43 packages. Where do we even start with vetting out which package to use. 
As you could imagine this happens a lot and it can be overwhelming. This 

### Frustrations

### Conclusion


> Topics:
  1. Node modules; what ones do I use? Why are there so many of the same package? What happens if the package I use stops being supported.
  1. Editors? Atom, Nuclieus, Sublime Text, Visual Studio. And then there is the setup. How do you get the correct setup to leverage tooling correctly.
  1. JavaScript, oh JavaScript. Although, ES6 is leaps and bounds better than JavaScript 4. However, it is not official and you must rely on tools such as Babel. 
  1. Native Mobile Development, I talking to you Apple, Promotes bad development practices, makes it incredibely difficult to follow "good" development practices. React Native was enjoyable because it was so simple to be a good developer. 
 