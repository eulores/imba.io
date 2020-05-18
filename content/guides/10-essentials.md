---
title: Essentials
multipage: true
---

# Language

Basic syntax stuff about the language

## Basics

### Indentation

### Implicit self

## Strings

## Numbers

## Regular Expressions

## Functions

## Classes

## Control Flow

### if

### elif

### switch

### try/catch

## Loops and Iteration

### for in

### for of

### for own of

### while

### until

## Import and Export

## Async and Await

## Decorators

## Elements

## Expressions

Conditionals and loops are also expressions

# Elements

```imba
let element = <div.main> "Hello"
console.log 'Hello there'
```

The above declaration might look strange at first. DOM elements are first-class citizens in Imba. We are creating a *real* dom element, with the className "main" and textContent "Hello".

Let's break down the basic syntax before we move on to more advanced examples. Since setting classes of elements is very common, imba has a special shorthand syntax for this. You declare classes by adding a bunch of `.classname` after the tag type. You can add multiple classes like `<div.large.header.primary>`. Can you guess how to set the id of a tag? It uses a similar syntax: `<div#app.large.ready>`.

> In all the examples we include a minimal stylesheet inspired by [tailwind.js](https://tailwindcss.com/)

> Imba does not use a virtual DOM. The example above creates an actual native div element.

> The props are compiled directly to setters. Explain tabIndex and tabindex difference.

> Defining attributes - when it is needed?

### Properties

```imba
<input type="text" value="hello">
```

```imba
var data = {name: "jane"}
<input type="text" value=data.name>
```

### Classes
Classes are set with a syntax inspired by css selectors:
```imba
<div.font-bold> "Bold text"
```
Multiple classes are chained together:
```imba
<div.font-bold.font-serif> "Bold & serif text"
```
If you want to set classes only when some expression is true you can use conditional classes:
```imba
var featured = yes
var archived = no
<div .font-bold=featured .hidden=archived> "Bold but not hidden"
```

To set dynamic classes you can use `{}` interpolation:
```imba
var state = 'done'
var marks = 'font-bold'
var color = 'blue'

<div.p-2 .{marks} .{state} .bg-{color}-200> "Bolded with bg-blue-200"
```

### Styling

```imba
<div.(font-weight:700)> "Bold text"
```

### Children

Indentation is significant in Imba, and elements follow the same principles. We never explicitly close our tags. Instead, tags are closed implicitly by indentation. So, to add children to an element you simply indent them below:

```imba
<div>
	<ul>
		<li> 'one'
		<li> 'two'
		<li> 'three'
```
When an element only has one child it can also be nested directly inside:
```imba
<div> <ul>
	<li.one> <span> 'one'
	<li.two> <span> 'two'
	<li.three> <span> 'three'
```

## Conditionals and Loops

Since tags are first-class citizens in the language, logic works here as in any other code:
```imba
var seen = true
<div>
	if seen
		<span> "Now you see me"
	else
		<span> "Nothing to see here"
```

If we have a dynamic list we can simply use a `for in` loop:

```imba
import {todos} from './data.imba'

# ---
<ul> for todo in todos
	<li.todo> <span.name> todo.title
```

Here's an example with more advanced logic:

```imba
import {todos} from './data.imba'

# ---
<div>
	for todo,i in todos
		# add a separator before every todo but the first one
		<hr> if i > 0 
		<div.todo .line-through=todo.done>
			<span.name> todo.title
			if !todo.done
				<button> 'finish'
```

> `for of` and `for own of` loops also supported for iteration

# Components

[Article](/articles/components.md)


# Rendering

- Mention how elements update / re-render
- Mounting an element vs mounting with a function
- Explain `imba.commit!`

Very important concept to grasp. 


## Rendering an Element into the DOM

```imba
imba.mount <div.main> "Hello World"
```

# Handling Events

[Article](/articles/events.md)

# Binding Data

[Article](/articles/binding-data.md)

# Managing State

[Article](/articles/managing-state.md)
