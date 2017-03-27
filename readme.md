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

## Framing (5 min)

The [**D**ocument **O**bject **M**odel](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
is a programming interface for HTML.


An HTML *document* is available for us to manipulate as an object, and this object is structured like a tree:

Not like [this tree](http://hakim.se/experiments/css/domtree/).

More like this:

![](http://www.tuxradar.com/files/LXF118.tut_grease.diagram.png)

Or this:

```
html
└── head
│   ├──title
│   ├──meta
│   ├──link[rel="stylesheet"]
|   └──script[type="text/javascript"]
|
└── body
    ├── header
    │   ├── h1
    │   └── nav
    └── section.simplicity
    |   └── h2
    │   └── article
    ├── section.life
    |   └── h2
    │   └── article
    │       └── block_quote
    │       └── block_quote
    └── footer
```

Let's look at the structure of [a page](https://github.com/ga-wdi-exercises/js-dom-quotes/blob/master/index.html)

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
