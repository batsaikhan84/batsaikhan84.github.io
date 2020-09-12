---
layout: post
title:      "JS Context"
date:       2020-09-12 02:49:35 +0000
permalink:  js_context
---


In this blog, I would be trying to describe the keyword 'this.' It is the foundation of object oriented programming and absolutely one of the most important concepts that help one to advance their knowledge in javascript. 
As you know, 'this' is the reserved word which means you cannot assign value to 'this.' The value of the 'this' is determined by how function is called. In other words, 'this' references the object that is executing the current function. Without any context, 'this' refers to a global object which in browsers is 'window.' 
```
console.log(this) // window
> window
       Window {parent: Window, opener: Window, top: Window, length: 1, frames: Window, …}

```
As you know, 'window' object is the global and top level object which has a number of properties. In addition, every variable declared in the global scope will be attached to the window object. Let's get back to the topic of 'this'.

Similarly, in a standard function, 'this' refers to a global object as well since the function is executed from the global object. 

```
const movie = {
    name: 'Titanic',
    genre: 'Romance',
	description() {
	    console.log(this)
	    console.log(`${this.name} ${this.genre}`)
    }
}

```
When we call the description function inside the movie object `movie.description()`, you will see this is referring to the object itself. in the first log, it is showing us the entire object that this refers to. In the second log, it printed the name and genre for us. That is because this.name === movie.name and this.genre === movie.genre.
```
{name: "Titanic", genre: "Romance", description: ƒ}
description: ƒ description()
genre: "Romance"
name: "Titanic"
__proto__: Object

Titanic Romance

```
I found this easier to remember what 'this' refers to if you see the line of function or method called, anything left of the function would be this will bind to. 

