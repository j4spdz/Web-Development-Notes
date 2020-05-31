<!-- omit in TOC -->
# Browser Rendering

<!-- omit in TOC -->
## Contents

- [Critical Rendering Path](#critical-rendering-path)
  - [1. Rendering Sequence (Construction)](#1-rendering-sequence-construction)
    - [DOM](#dom)
    - [CSSOM](#cssom)
  - [2. Layout operation](#2-layout-operation)
  - [3. Paint operation](#3-paint-operation)
  - [4. Compositing operation](#4-compositing-operation)
- [JavaScript and CSS can block critical rendering path](#javascript-and-css-can-block-critical-rendering-path)
  - [Embedded Javascript and CSS](#embedded-javascript-and-css)
  - [External stylesheets](#external-stylesheets)
  - [External Javascript files](#external-javascript-files)
- [Tips to reduce blocking](#tips-to-reduce-blocking)
  - [HTML](#html)
  - [CSS](#css)
  - [JS](#js)
  - [Optimizing Network and Delivery](#optimizing-network-and-delivery)
- [Misc](#misc)
  - [DOMContentLoaded](#domcontentloaded)
  - [Resource Prefetching](#resource-prefetching)
  - [Dev Tools](#dev-tools)

## Critical Rendering Path

### 1. Rendering Sequence (Construction)

When a web page is loaded, the browser first reads the TEXT HTML and constructs DOM Tree from it. Then it processes the CSS whether that is inline, embedded or external CSS and constructs the CSSOM Tree from it. After these trees are constructed, then it constructs the Render-Tree from it. Once the Render-Tree is constructed, then the browser starts the printing individual elements on the screen.

#### DOM

DOM is a high-level Web API provided by the browser to efficiently render a webpage and expose it publically for the developer to dynamically manipulate DOM elements for various purposes.

#### CSSOM

CSSOM, a tree-like structure to compute styles based on CSS cascading rules. Unlike DOM API, CSSOM is kept hidden from the user.

### 2. Layout operation

The layout consists of the size of each node in pixels and where (position) it will be printed on the screen.

### 3. Paint operation

Layers are drawn on the browser separately.

Inside each layer, the browser fills the individual pixels with whatever visible property of the element is like border, background colour, shadow, text, etc. This process is also called as rasterization.

### 4. Compositing operation

Each layer is broken down into different tiles which then will be drawn on the screen by the GPU.

## JavaScript and CSS can block critical rendering path

### Embedded Javascript and CSS

Browser constructs the DOM by parsing HTML from top to bottom, with embedded javascript and CSS parsed synchronously

### External stylesheets

Until external CSS is downloaded and parsed, the browser will not render anything on the screen. CSSOM construction will be blocked and DOMContentLoaded event won’t be fired by the browser.

### External Javascript files

DOM construction is stopped until external .js file(s) downloaded and parsed. Do note that parsing and DOM building may be halted until CSSOM is ready.

## Tips to reduce blocking

### HTML

- Load style tags in the head
- Load script right before end of body
  
### CSS

- Only load what is needed
- Above the fold loading
  >i.e. load styles for what is currently seen while the rest loaded later
- Media Attributes
- Less Specificity

### JS

- Load scripts asynchronously
- Defer loading of scripts
- Minimise DOM manipulation
- Avoid long running Javascript
  
[Async vs Defer](https://stackoverflow.com/questions/10808109/script-tag-async-defer)

### Optimizing Network and Delivery

- Reduce download size by minimising files and image sizes
- Reduce number of files by bundling such as webpack

## Misc

### DOMContentLoaded

DOMContentLoaded can be safely fired when both DOM and CSSOM is constructed and Render-Tree is about to be constructed.

> _DomContentLoaded VS window.onload_
>
>**DOMContentLoaded** marks a point where all external JavaScript is parsed and DOM is fully ready. **window.onload** marks a point where external stylesheets and files are downloaded and our webpage is completely ready.

### [Resource Prefetching](https://css-tricks.com/prefetching-preloading-prebrowsing/)

Easy to misuse, and different browsers have different performance metrics for them.

### Dev Tools

- View main thread activities in a table to sort activities based on which ones took up the most time.
- Analyze frames per second (FPS) to measure whether your animations truly run smoothly.
- Monitor CPU usage, JS heap size, DOM nodes, layouts per second, and more in real-time with the Performance Monitor.
- Capture screenshots while recording to play back exactly how the page looked while the page loaded, or an animation fired, and so on.
- View interactions to quickly identify what happened on a page after a user interacted with it.
- Find scroll performance issues in real-time by highlighting the page whenever a potentially problematic listener fires.
- View paint events in real-time to identify costly paint events that may be harming the performance of your animations.
- View main thread activity to view every event that occurred on the main thread while you were recording.
