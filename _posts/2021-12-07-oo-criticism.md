---
layout: post
title: "Video Notes on OOP"
---

### Brian Will - Object Oriented Programming is Bad

[![IMAGE ALT TEXT](http://img.youtube.com/vi/QM1iUe6IofM/0.jpg)](https://www.youtube.com/watch?v=QM1iUe6IofM&ab_channel=BrianWill "Object-Oriented Programming is Bad")

#### Why Did Object-Oriented Programming Proliferate?
- GUI programming in 90's was easily expressible through the language of "things".
- abc.xyz syntax created a clear way to identify and autocomplete the available methods on an object.

#### Encapsulation - The Core Purpose of OOP
- The OOP and FP methodologies appear to be centered around handling mutable state.
  * The former segregates mutable state into discrete units (objects) that hide prevent direct interactions with that state, only allowing mutation through methods (a public interface)
  * The latter minimizes ("FP-style") or eliminates mutable state entirely (true FP)

#### Whats Wrong With This?
- While all objects encapsulate state, these objects themselves make up the state of the objects that use them. That is, in order for an object A to make use of another object B, object A must retrieve and store a reference to object B. Object B now IS the state of object A, and because objects are responsible for their own state, object A is not responsible for object B.
- This becomes a giant graph of shared state between objects, as new objects come in and begin modifying the state of shared objects.
- There are many OO patterns seek to solve this flaw. As an example - god objects that contain all other objects in the app. 
  * I've never worked with this pattern per se, but it sounds reminiscent of React/Angular component, with the god object being the top level App component. Indeed, communicating large app-wide state changes is so difficult when you try to pass state up to a parent, then down to another child, that you have tools like Redux to make this easier.
- However, these OO patterns are never actually enforced by the OO language, they are just that - patterns. They can be broken for convenience or implemented haphazardly and poorly (and they usually are).

#### Whats The Solution?
- Brian Will argues that global mutable state should be avoided (true) but also that if necessary, mutable state can be modified in a procedural way.
  * Brian is a Go programmer, so probably hasn't interacted much with Haskell, Scala or monads. Functions that need to have a side effect (i.e. modify global state) can represent that side effect by returning a monadic effect type. For a great example, **see Bartosz Milewski's implementation of a monoidal logging type [here](https://www.youtube.com/watch?v=i9CU4CuHADQ&ab_channel=BartoszMilewski).**
