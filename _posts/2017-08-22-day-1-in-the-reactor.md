---
title : "Day 1 in the Reactor"
layout : post
excerpt : "1st day of my journey studying react"
image : /assets/image/react-logo.png
tags : 
    - post
    - react
---
Starting out with react, I quickly noticed one thing. React is heavily based on ES6 features, from the predominant use of arrow functions to classes and the spread operator. It also borrows a lot of principles from the functional programming world, particularly immutability.


So basically React is a library for manipulating the HTML DOM. Historically, manipulating the DOM requires use of the JavaScript DOM API which can be a bit frustrating. React strives to make DOM manipulation easier and also faster. What impressed me about React from the onset is how it creates a virtual DOM based on JavaScript object literals. This allows the programmer to simply concentrate on their JavaScript and not think too much about raw HTML structures. The HTML structures have been well embedded in JavaScript objects. React also allows you to create reusable components for the DOM. I think this feature is truly amazing.
So lets get to the real business.


To use React in a browser, you need two seperate components. The core React library itself and the React DOM. The core React library handles the virtual DOM and the React DOM library handles the rendering of the virtual DOM into real HTML code for the browser to consume. In the past, the React library and React DOM were all one but eventually seperated because the virtual DOM is now being used for a lot of things such as React Native(A react library for making mobile apps). 


Let's get React in our browser now. We will be importing React from a CDN.
``` html
<script src='https://unpkg.com/react@15.4.2/dist/react.js'></script> <!-- The core library -->
<script src='https://unpkg.com/react-dom@15.4.2/dist/react-dom.js'></script><!-- The rendering library -->
```

This should succesfully import React into our browser. Now let's create our first element