---
layout: essay
type: essay
title: "Design Patterns: Why Blueprints Matter"
date: 2025-04-24
published: true
labels:
  - Design Patterns
  - Software Architecture
  - Factory Pattern
---

<img width="300px" class="rounded float-start pe-4" src="../img/design-patterns/blueprint.png">

## Let’s imagine we’re construction workers

Let’s imagine we were construction workers trying to design a building we plan to put up. To start the construction, it would be foolish to try to build everything from the ground up, guessing and checking what things work and what things won't. Another issue this might solve is that we may have different ideas of how to implement the same concept.

The answer to this is **Design Patterns**. Because this has been an issue in the past, those before us have created a blueprint that solves many of these problems.

## So what do design patterns do?

This is the application of design patterns. These “blueprints” ensure things like reusable designs, clear understanding & readability, testability, and many more. Even though it may seem obvious right now how important design patterns are to the production of any software, I didn't always understand this.

## A real example: user roles in a final project

During the final project, we track different types of Users. For example, a client can have the role of regular user or admin. This is accessible across the entire app so that we don't have to keep reinitializing it each time that we need to access the data.

This implementation of having the user defined once and accessible over the entire app is a part of the **Factory Pattern**.

> “Define an interface for creating an object, but let subclasses decide which class to instantiate. Factory Method lets a class defer instantiation to subclasses.”  
> — *Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides*, in *Design Patterns: Elements of Reusable Object-Oriented Software*

## Why this matters

This is important to the application because otherwise, every part of the app must know how to build the user and its types. Additionally, if the data were to ever be changed then we would only need to implement it in one location and have it be applied everywhere—keeping everything in sync and avoiding cross-overs.

## Conclusion

Whether you're building a skyscraper or a scalable software system, starting with blueprints matters. Design patterns aren't just abstract academic ideas — they're practical, time-tested solutions that help teams speak the same language and build more effectively. Learning and applying them early saves time, prevents miscommunication, and leads to cleaner, more maintainable code.
