---
layout: post
title: State of React Native
image: /blog/images/state-of-react-native.jpg
date: 2017-08-02 14:05
categories:
---

This blog post is not 100% directed towards React Native but on the 
entire stack of React Native. I recently started working on a project 
which explores React Native. I followed a wonderful 
[tutorial](https://learn.handlebarlabs.com/courses/175915) which, at the
time, was only a couple months old. This should not seem like a big 
deal but in the world of [Node.js](https://nodejs.org/en/) it is and 
that is exactly what I want to touch on today.

## My Take on Native Development

I have been developing both iOS and Android native mobile applications
for a couple years now and the most frustrating aspect is the "That's
the way you do it" mentality \*cough\*Apple\*cough\*. Apple provides a
lot of snippets and example applications that illustrate how one could
build an application. However, the issues that they do not emphasize are
testability and a concise project structure which both lead to good
architecture. The promotion of good practices such as
[Separation of Concerns](https://en.wikipedia.org/wiki/Separation_of_concerns)
and
[Inversion of Control](https://en.wikipedia.org/wiki/Inversion_of_control)
are not conveyed to the audience. Perhaps these techniques are not the
responsibility of Apple and Google but that is not what we are here to
talk about; we'll save that for another day. For anyone that has done
any iOS development you have already come across the issues of Massive
View Controllers. Not only are good practices not promoted but actually
implementing a good architecture is difficult especially if your
application relies on Core Data; it is an up hill battle. There are many
different attempts at clean architecture but none are revered as the
standard. In short, while writing native applications it seems overly
exhausting to be a good developer.  

## My Take on React Native

React Native is all the buzz right now. Is it a fad or is it here to
take over the majority of traditional native development? We shall see.
Regardless of the answer, I currently get calls from recruiters all the
time now because of my mobile development experience. Later to realize
the potential client really wants a React Native developer. So,
reluctantly I jumped into React Native development. Now, keep in mind I
despise JavaScript, so I went into this project with a chip on my
shoulder. All and All, I must say that I was pleasantly surprised at how
much I liked development with React Native; it was very enjoyable to write
code. Separation of concerns was trivial. I used
[Redux](http://redux.js.org/), which was also fantastic! However, there
are definitely some frustrations and concerns about using React Native.

### Frustrations

---

#### Dependency Hell

For anyone new to the Node.js ecosystem, simply put, it is a bunch of
small packages plugged together to create a larger package. With that
comes a lot of decisions to make. Most of the decisions have already
been made for you because of the dependencies of your dependencies but
you still need to make a choice on what first order dependencies you
will be using. If you are like me, you will probably want to vet out
your dependencies before using them. So, let's use a real example. Let's
say we want to use a package for forms in our new React Redux
application. Go to 
[npm](https://www.npmjs.com/search?q=keywords:react-redux%20form&page=1&ranking=optimal)
and search react redux forms, go ahead I'll wait. How many results did
you get? When I did it at the time of writing this post it was 43
packages. Where do we even start with vetting out which package to use.
As you could imagine this happens a lot and it can be overwhelming.
There are several factors I consider before pulling in a dependency one
of which is getting a general feel for the support for the dependency
itself (this is not the only thing I consider but for the sake of
brevity we will simply consider support). 

#### Editors

Another frustration I had to overcome was choosing and setting up an
editor. First question, what editor do I use? Well there is the well
known [Sublime Text](https://www.sublimetext.com/3), the new Github
built [Atom](https://atom.io/), don't forget the Facebook React plugin
[Nuclide](https://nuclide.io/) for Atom, and then there is
[Visual Studio Code](https://code.visualstudio.com/). I naturally went
to Atom with the Nuclide plugin; seems like the best tool for the job.
Well, after about an hour I found myself frustrated with the
intellisense, maybe I didn't have it setup right? So, I decided to give
VS Code a try and to my surprise it had better intellisense support for
React than Nuclide. With the exception of a couple nuances VS Code has
worked surprisingly well.

All these editors have one thing in common, they all have a large set of
plugins that can be leveraged. These plugins are all apart of the
Node.js ecosystem, which is managed by using npm. Surprise! We are going
to have the same type of issues we already covered with dependency hell
and all the fun that comes with it. But one other thing that seems to
fail me is understanding how to properly configure all the plugins that
are needed to get the editor working the way I want. I still don't have
a "perfect" setup.

### Concerns

---

#### Early Adoption

React Native is still very young and the npm packages are even younger
and there are a lot of the same packages trying to solve the same
problems. As mentioned before the amount of packages can be
overwhelming, to say the least. Furthermore, one of the issues that I
encountered when going through a 5 month old tutorial is the packages
used in the tutorial were all out of date. One of the packages I was
trying to use from the tutorial was not updated to work with the latest
version of React Native. Good thing there are 100 other packages just
like it ;)

#### Native Operating System Update

Anyone that is experienced in mobile application development knows the
release cycles for Android and iOS Operating System releases. For anyone
new to the game here is an overview. Android and iOS operating systems
are announced about the same time every year, May - June time-frame.
Because of Android's
[fragmentation problem](https://developer.android.com/about/dashboards/index.html#Platform)
this issue is not so pressing unless you are always on the heels of
supporting the latest and greatest features. iOS on the other hand is
much more concerning. One of the nice things about developing for Apple
is the extremely high adoption rate of the newest OS. This is a double
edge sword though. Because the adoption rate is so high
([check out how fast iOS 10 was adopted](https://mixpanel.com/trends/#report/ios_10))
you must also be on top of making sure your application can support the
latest OS, which is only about 6 months from initial announcement to 85%
adoption in production. So the big concern is, at what pace will a
package be able to keep up with the ever changing React Native
ecosystem? This means, at very least, ever year React Native will need
to be updated, which could take some time. Let's say you are using
package X in your application. Package X depends on React Native 
releasing its updates so that package X can be updated. Once the 
developers of package X finally release their updates you can start
implementing it in your application, and that assumes package X is still
supported. Assume happy path and this still could significantly reduce
your OS preparation window.

#### Longevity

With any dependency, longevity is a concern that is always on my mind
and this is typically why I do not opt for anything but pure native
development. With companies such as Facebook, AirBNB, and Artsy backing
the survival of React Native there can be some security that it isn't
going anywhere anytime soon. But that is a big scary assumption, don't
forget about [Parse](https://en.wikipedia.org/wiki/Parse_(platform)).
Nothing is guaranteed! 

#### React Native License

I hesitated even bringing up the
[React License](https://github.com/facebook/react/issues/7293) because
there are so many other places to read the on going debate but I need to
touch on one small topic. 

No matter the true intention of the license verbiage one thing is for
sure, you better run this by your clients or your own legal department
before using React Native. Look, the last thing you would ever want is
to be months into development when all of a sudden Seth from the legal
department storms in screaming "Please tell me we aren't using React
Native!" I am not saying there is anything scary about what Facebook has
in its fine print but the legal department where you are working might
not like it. It is just good to get it cleared first.

### Conclusion

This post may seem like I am trying to sway people from using React
Native but I assure you that I am not. There are a lot of benefits I
found while working with React Native, the most important one being how
enjoyable and easy it was to write good clean code. React Native is not 
a [golden hammer](http://wiki.c2.com/?GoldenHammer) but yet another tool
to keep in our shed. It does not solve every problem, nor should it, but
if you plan on developing an API driven application I would put some
serious thoughts into using React Native as your tool of choice.