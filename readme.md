---
title: Document Object Model
type: lesson
duration: 1
authors:
    creators: Jesse Shawl (DC)
    editors: John Master (DC), Matt Scilipoti (DC)
competencies: Programming, Javascript
---


# The Document Object Model (DOM)

## Learning Objectives
- Explain the DOM: its value and its structure
- Introduce the role, utility, and pros/cons of JQuery
- Access DOM Elements using relative selection
- Access DOM Elements using query selectors
- Create, Read (access), Update (content and attributes), and Destroy DOM elements

## Framing (10 minutes)

> Why study JS?

> What does "it runs in the browser" mean? Why is this something that we would want to do?

> We've talked about values (primitive types and objects) and the language constructs for creating our own. We have also alluded to / used some values which are available to us in the "environment". What is an example?

> What is the most annoying thing about websites?

> What is HTML / a Document (in terms of the web) and how to we represent it?

## Introducing the DOM (10 minutes)

JavaScript is the lingua franca of the web. Since it's advent in 1995 as a neat but hastily delivered browser feature from Netscape it has revolutionized the web and by extension the world.
Foundational to the success (existence) of this revolution is a clunky and confusing API called the DOM, the Document Object Model.
The DOM's conception was organic and as its importance grew was standardized.

The DOM is best understood through use so we will waste little time before diving in but if you are interested in a more complete / formalized description, check out [CSS Tricks: What is the DOM?](https://css-tricks.com/dom/) and [MDN Intro to the DOM]( https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction )

### Representing the Document

The document is the content of our webpage which is encoded into our HTML. The HTML we write is one representation of this.

> What structure does HTML take? (hint: think of parent / child relationships between elements)
> [ hint 2 ](http://hakim.se/experiments/css/domtree/)

An HTML document (like so many other things in programming) is a tree. We will think of it as a tree of elements:

![Element Tree](http://www.tuxradar.com/files/LXF118.tut_grease.diagram.png)

It is important to note though, that there are separate element and text nodes:

![HTML as a tree](http://www.cs.toronto.edu/~shiva/cscb07/img/dom/treeStructure.png)

![HTML more tree like](http://www.cs.toronto.edu/~shiva/cscb07/img/dom/treeStructureAlternate.png)

We will generally interact with elements and consider the text something belonging to the element but remember to keep in mind actual implementation

## JQuery (10 minutes)

Historically the DOM's implementation was inconsistent across browsers (while not entirely vanished, this is much less of a problem between modern browsers) and many of it's methods are lengthy.

By addressing both of these issues and smoothing other rough edges of JS in the browser, a library called JQuery became phenomenally popular.

Today we will introduce JQuery methods alongside their "vanilla" JS counterparts and let you compare.

Keep in mind that JQuery methods cannot be used on regular DOM elements and vanilla properties and methods are not available on JQuery elements, though the conversion is easy. Explore this early

> Have you heard of JQuery? What are your preconceptions?

> What could the advantages of bringing in a library be? What could the disadvantages be?

### Loading Libraries

> What is a JS library?

How we load our code is an enormously interesting problem that is actually one of the biggest focuses of modern web development.
For the time being, we will be using sourced script tags which will make a request of the necessary JS file and load it into the browser environment.
We do this using a script tag. [Crockford on Script Tags](http://javascript.crockford.com/script.html) 

Just the same way that we link a local file with `<script src="./script.js"></script>`, we can load a remotely hosted file by providing a url to `src`: `<script src="https://code.jquery.com/jquery-3.2.1.js"></script>`

A browser loads a page by reading HTML and rendering it to the screen. 
When a script tag is encountered, reading and rendering of the HTML is put on hold until the script is loaded, parsed, and evaluated.
On a slow connection or when the file takes a long time to run this can cause a significant delay to rendering. Weak UX, sad!
For this reason, we link script tags at the end of the file so that at least the user has something nice to look at as the scripts load.

> Why does loading scripts at the end make me a little uneasy? (John's personal opinion -- would love to be contradicted)

## Accessing Element Objects (60 minutes)
When interacting with the DOM, we will primarily be interfacing with [[      <li class="red">red</li>][Element Objects]]

The `document` object is exposed on the global object, `window`. This is the top level or root element object

If you haven't already, clone this repo. Open `docs/index.html` in your browser and open the developer console. JQuery has been imported from the HTML. 

The document has several entry points to the page's content including `.head` and `.body`

### Relative Selection (20 minutes)
There are several properties that every element has which reference the elements proximate to it:

- `.children` (jquery: `.children()`)
- `.childNodes`
- `.firstChild`
- `.lastChild`
- `.previousSibling` (jquery: `.prev()`)
- `.nextSibling` (jquery: `.next()`)
- `.parentElement` (jquery: `.parent()`)

jquery only:
- `.siblings()`
- `.parents()`

![Node Relations]( https://www.w3schools.com/xml/navigate.gif ) 

In order to use jquery methods, we need to construct a jquery object. This is done by passing an element to the jquery constructor function.
To get the jquery document element we evaluate `$(document)`. 
To get the underlying DOM element we use the get method and provide an index (jquery objects all act as collections). So (`$(document).get(0) === document`)

#### You Do (5 minutes)

Use google throughout and talk with your neighbors about confusing parts of documentation. 
Docs are written precisely using sometimes confusing syntax; this is necessary and a good thing but takes some getting used to

Spend a few minutes navigating our simple list using these properties and methods in the console.
Evaluate frequently to keep you bearings and remember to use the up/down arrows to navigate your history.


### Query Selection (10 minutes)

> Why is relative traversal from the top level an unmaintainable approach to element selection?

Fortunately, we have some much easier method of accessing elements.

#### By Id
`document.getElementById(id)`

#### By Tag
`document.getElementsByTagName(tagName)`

#### By Class
`document.getElementsByClassName(className)`

#### By Selector <-- USE THIS ONE
`document.querySelector(selector)` and `document.querySelectorAll(selector)` use CSS selectors to target elements.
This is the primary means by which jquery selects elements: `$(selector)`.  

> What's the difference between `querySelector` and `querySelectorAll`? How does `$(selector)` behave?

> Why would we use any of the other selectors?

#### You Do (5 minutes)
Play with that same list, now using query selectors. Spend some time perusing the jquery docs and the MDN documentation on these functions.
As always, discuss what you find with your neighbors -- explaining these ideas in your own words is as valuable as using them

### BREAK (10 minutes)

### You Do: Selecting DOM elements (20 minutes)

https://github.com/ga-wdi-exercises/js-dom-quotes

## Accessing the document (10 min)

`document`
  - `document.head`
  - `document.body`

Each web page loaded in the browser has its own document object. The Document interface serves as an entry point to the web page's content

### Element attributes

`document.body`
  - .children
  - .childNodes
  - .firstChild
  - .lastChild
  - .nextSibling
  - .parentElement
  - .parentNode

Methods are available on any element.

### Methods for selecting elements

- document.getElementById
- document.getElementsByTagName
- document.getElementsByClassName
- document.querySelector
- document.querySelectorAll

## You Do: Selecting DOM elements (10 min)

https://github.com/ga-wdi-exercises/js-dom-quotes

## Altering DOM Elements (5 min)

- [.textContent](https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent)
- .innerHTML
- .setAttribute(name, value);
- .id
- .classList.toggle (add, remove, contains)
- .style

## You do: Logo hijack (15 min)

1. Open up www.google.com in Chrome or Firefox, and open up the console.
- Store the url to the Yahoo logo in a variable.
- Find the Google logo and store it in a variable.
- Modify the source of the logo IMG so that it's a Yahoo logo instead.
- Find the Google search button and store it in a variable.
- Modify the text of the button so that it says "Yahooo!" instead.

Bonus: Add a new element between the image and the search textbox, telling the world that "Yahoo is the new Google".

## Creating/Removing DOM Elements (1 min)

- [Document.createElement](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement)
- [Node.appendChild](https://developer.mozilla.org/en-US/docs/Web/API/Node/appendChild)
- Node.removeChild

## Break (5 min)

## Events (10 min)

What is an event?
http://eloquentjavascript.net/14_event.html

- .onclick
- .addEventListener
  - click
  - mouseover
- .preventDefault()

## Examples

- [jessica hische](http://jessicahische.is/)
- [color scheme switcher](https://github.com/ga-wdi-exercises/color-scheme-switcher)

## Conclusion (5 min)

1. What is the difference between a method and an attribute?
2. What is the difference between `onclick` and `addEventListener?`

## Break (10 min)
---

## Homework

Pixart: https://github.com/ga-wdi-exercises/pixart_js


## References
- https://developer.mozilla.org/en-US/docs/Web/API/Event

[![Build Status](https://travis-ci.org/ga-wdi-lessons/js-dom.svg?branch=master)](https://travis-ci.org/ga-wdi-lessons/js-dom)
