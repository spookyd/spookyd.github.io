---
layout: post
title: Data Source Enums with Swift
date: 2017-08-14 16:29
image: /blog/images/data-source-enums-with-swift.jpg
categories: swift
---

I was reviewing some coding examples from Apple and I came across a fun 
sample application called
[Lucid Dreams](https://developer.apple.com/library/content/LucidDreams/Introduction/Intro.html).
The purpose of this sample was to illustrate how to use "Protocol 
Oriented Programming" (POP). Within the example, I came across an 
interesting approach to static tables where you define a nested enum 
declaring the sections.

```swift
    enum Section: Int {
        case preview
        case description
        case numberOfCreatures
        case creature
        case effect
 
        static let count = 5
 
        var numberOfRows: Int {
            switch self {
                case .preview: return 0
                case .description: return 1
                case .numberOfCreatures: return 1
                case .creature: return Dream.Creature.all.count
                case .effect: return Dream.Effect.all.count
            }
        }
 
        /// A user facing title for the section to be used as a section header.
        var title: String? {
            switch self {
                case .description: return "Description"
                case .numberOfCreatures: return "Number of Creatures"
                case .creature: return "Creatures"
                case .effect: return "Effects"
 
                default: return nil
            }
        }
 
        init(at indexPath: IndexPath) {
            self.init(rawValue: indexPath.section)!
        }
 
        init(_ section: Int) {
            self.init(rawValue: section)!
        }
    }
```

> Snippet from Apple's [Lucid Dreams](https://developer.apple.com/library/content/LucidDreams/Listings/LucidDreams_DreamDetailViewController_swift.html#//apple_ref/doc/uid/TP40017334-LucidDreams_DreamDetailViewController_swift-DontLinkElementID_18)

At first glance this does not seem like anything to write home about.
However, when you take a step back and think about what this code does 
for us, it is pretty amazing. Lets discuss some of the benefits.

## The Power

I have been a longtime advocate for [Clean Code](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)
so this approach seems very acceptable. One of the main advantages of 
this pattern is testability. This eliminates the need to mock anything
with life cycles and allows for a simple clean unit test.

A test can now be as simple as:

```swift

    func testDescriptionTitle() {
        XCTAssertNil(DreamDetailViewController.Section.preview.title)    
    }

``` 

Another advantage is the initializers. Since an initializer is provided 
for both the `indexPath` and the `section` we can now eliminate accessor 
code like: 

```swift 
    if index.section == 0 { return "Section title" }
``` 

We get this functionality for free for using the enum.

This power is not limited to the examples above. You will be able to add
what ever methods that make sense for your use case.  

## The Beauty

The beauty of Swift, among other popular languages, is its declarative 
style. If we need to access the sections of the 
`DreamDetailViewController` we can write this in a more natural manner;
`DreamDetailViewController.Section(2).title` or
`DreamDetailViewController.Section.creature.title`. This allows for 
clear intent for the code you are working with. 

## The Dangers

As with everything that seems like a glorious solution there are some 
pitfalls to be aware of when selecting this option.
 
### Inheritance

Inheritance, or lack there of, can be an issue. You may find yourself in 
a situation where you need to add another case to your enum. Well, with 
enums this is not an option. For a use case, lets look at feature 
toggling. For those that do not know, as its name implies, feature 
toggling is the act of toggling a feature but it is done in a more 
elegant way than littering `if` checks every where in your code base. 
One of the ways of providing a "feature" toggle is by creating a factory
that will produce the correct output based on the feature toggle. So, if
we look at the sections enum, lets say we are performing A/B testing and 
we want some people to have an extra section, say Friends. How would we 
do this? If this were a class we could simply create a child class and 
override or provide new functionality.

### Dynamic Table Data

Dynamic table data will cause similar issues but with an added bonus. We
can't store data! Enums are not meant to store any data so by using this 
solution we will end up with something where we are now maintaining the 
data array outside of the sections enum and now we are starting to slip 
back into our old ways of accessing table data.  

## Wrapping Up

There are some ways you can get around the shortcomings of this 
approach. For instance, replacing the enum with a protocol but we'll 
save that for another day. I hope this helps shine a light on how we can 
use enums to encapsulate data source information. Happy Coding!

