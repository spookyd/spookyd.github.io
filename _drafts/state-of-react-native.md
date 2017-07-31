---
layout: post
title: State of React Native
image: /blog/images/state-of-react-native.jpg
date: 2017-07-27 08:52
categories:
---

This blog post is not 100% directed towards React Native but on the entire stack on RN. I recently started working on a project which explores React Native. I followed a wonderful tutorial [TODO: insert link] which, at the time, was only a couple months old. This should not seem like a big deal but in the world of node it is and that is exactly what I want to touch on today.

## My Take on Native Development

I have been developing both iOS and Android native mobile applications for a couple years now and the thing I found the most difficult to overcome was the "That's the way you do it" mentality. 
\*cough\*Apple\*cough\*. There are a lot of snippets and example applications that illustrate how one could build an application. However, the issues that they do not emphasize are testability, which leads to good architecture and also includes concise project structure.
The promotion of good practices such as Separation of Concerns[TODO: insert link] is not conveyed to the audience. For anyone that has done any iOS development you have already come across the issues of Massive View Controllers.
Not only are good practices not promoted but actually implementing a good architecture is difficult. There are many different attempts at clean architecture but none are revered as the defecto. In short, it is exhausting being a good developer while writing native applications.  

## My Take on React Native

React Native is all the buzz right now. I get calls from recruiters all the time now because of my mobile development experience. Later to realize the potential client really wants a React Native developer. So, reluctently I jumped into React Native development. Now, keep in mind I despised JavaScript, so I went into this with a chip on my shoulder and I must say that I was pleasently suprised at how mush I enjoyed it; it was very enjoyable to write code. Separation of concerns was trivial. I used [Redux](), which was also fantastic! However, there are definitly some frustrations and concerns about using React Native.

### Frustrations

---

#### Dependency Hell

For anyone new to Nodejs the ecosystem, simply put, is a bunch of small packages plugged together to create a larger package. With that comes a lot of decisions to make. Most of the decisions have already been made for you because of the dependencies of your dependencies 
but you still need to make a choice on what dependencies you will be using. If you are like me, you will probably want to vet out your dependencies before using them. So, let's use a real example. Let's say we want to use a package for forms in our new react redux. 
Go to [npm](https://www.npmjs.com/search?q=keywords:react-redux%20form&page=1&ranking=optimal) and search react redux forms, I'll wait. How many results did you get? When I did it at the time of writing this post it was 43 packages. Where do we even start with vetting out which package to use. 
As you could imagine this happens a lot and it can be overwhelming. There are several factors I consider before pulling in a dependency one of which is getting a general feel for the support for the dependecy itself (this is not the only thing I consider but for the sake of breviety we will simply consider support). 

#### Editors

Another frustration I had to overcome was choosing and setting up an editor. First question, what editor do I use? Well there is well known Sublime Text [TODO: INnsert link](), the new Github built Atom [TODO: INnsert link](), don't forget the Facebook React plugin [Nuclieus]() [TODO: INnsert link](), and then there is [Visual Studio Code] [TODO: INnsert link](). So, I naturally went to Atom with the Nuclieus plugin; seems like the best tool for the job. Well, after about an hour I found myself frstrated with the intellisense, maybe I didn't have it setup right? So I decided to give Visual Studio Code a try and to my suprise it had better intellisense support for React than Nuclieus. With the exception of a couple nuances VS Code has worked suprisingly well.

One thing all these editors have in common is they all have a suite of plugins that can be leveraged. These plugins are all apart of the nodejs ecosystem, aka npm. Suprise! We are going to have the same type of issues we already covered with dependency hell and all the fun that comes with it. But one other thing that seems to fail me is understanding how to properly configure all the plugins that are need to get the editor working the way I want. 

### Concerns

---

#### Early Adoption

React Native is still very young and the npm packages are even younger and there is a lot of them. As mentioned before the amount of packages can be overwhelming to say the least. Furthermore, one of the issues that I encountered when going through a 5 month old tutorial is the packages used in the turtorial were all out of date. One of the packages I was trying to use from the tutorial was not updated to work with the latest version of React Native. Good thing there are 100 other packages just like it ;)

#### Native Operating System Update

Anyone that is not new to mobile application development knows the release cycles for Android and iOS Operating System releases. For anyone new to the game here is an overview. Android and iOS operating systems are announced about the same time every year, May - June timeframe. Because of Androids [fragmentation issue](TODO: insert link) this issue is not so pressing unless you are always on the heels of supporting the latest and greatest features. iOS on the other hand is of much more concern. One of the nice but things about developing for Apple is the extremely high adoption rate of the newest OS. This is a double edge sword though. Because the adoption rate is so high [TODO: link to mixpanel stat]() you must also be on top of making sure your application can support the latest OS, which is only about 6 months from initial announcement to 85% adoption. So the big concern is, at what pace will a package be able to keep up with the ever changing React Native ecosystem? This means, at very least, ever year React Native will need to be updated, which could take some time. Once React Native has been updated some package X that you use in your app may need to be updated but can't really be updated reliably until the latest version of React Native has been published. Once package X is finally released you can start implementing it in your application and thats even if package X is still supported. Which in turn, significantly reduces your OS preparation window.

#### Longevity

This concern is always on my mind with any dependency and is typically why I do not opt for anything but pure native development. With companys such as Facebook, AirBNB, and Artsy backing the survival of React Native there can be some security that it isn't going anywhere anytime soon. But be that is a big scary assumption, don't forget about [Parse](https://en.wikipedia.org/wiki/Parse_(platform)). Nothing is guarenteed! 

#### React Native Patent

I hestated even bringing this up because there are so many other places to read the on going debate but I felt I need to just to touch on one small topic. No matter the true intention of the lawsuite verbage one thing is for sure, you better run this by your clients or your own legal department before pulling in React Native. Look the last thing you would ever want is to be months into development when all of a sudden Seth from the legal department storms in saying "Please tell me we aren't using React Native!" I am not saying there is anything scary about what Facebook has in its fine print but the legal department you are working for might not like it. It is just good to get it cleared first.

### Conclusion

This post may seem like I am trying to sway people from using React Native but I assure you that I am not. There are a lot of benefits I found while working with Reat Native, the most important one being how enjoyable it was to write good clean code. React Native is not a golden hammer (TODO: insert link)[] but yet another tool to keep in our shed. It does not solve ever problem, nor should it, but if plan on developing an API driven application I would put some serious thoughts into using React Native as your tool of choice.