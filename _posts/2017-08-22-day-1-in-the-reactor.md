---
title : "Day 1 in the Reactor"
layout : post
excerpt : "1st day of my journey studying react"
image : /assets/image/react-logo.png
tags : 
    - post
    - react
---
# First Post coming in at 8:23 AM

Starting out with react, I quickly noticed one thing. React is heavily based on ES6 features, from the predominant use of arrow functions to classes and the spread operator. It also borrows a lot of principles from the functional programming world, particularly immutability.


So basically React is a library for manipulating the HTML DOM. Historically, manipulating the DOM requires use of the JavaScript DOM API which can be a bit frustrating. React strives to make DOM manipulation easier and also faster. What impressed me about React from the onset is how it creates a virtual DOM based on JavaScript object literals. This allows the programmer to simply concentrate on their JavaScript and not think too much about raw HTML structures. The HTML structures have been well embedded in JavaScript objects. React also allows you to create reusable components for the DOM. I think this feature is truly amazing.
So lets get to the real business.


To use React in a browser, you need two seperate components. The core React library itself and the React DOM. The core React library handles the virtual DOM and the React DOM library handles the rendering of the virtual DOM into real HTML code for the browser to consume. In the past, the React library and React DOM were all one but eventually seperated because the virtual DOM is now being used for a lot of things such as React Native(A react library for making mobile apps). 


Let's get React in our browser now. We will be importing React from a CDN.
``` html
<script src='https://unpkg.com/react@15.4.2/dist/react.js'></script> <!-- The core library -->
<script src='https://unpkg.com/react-dom@15.4.2/dist/react-dom.js'></script><!-- The rendering library -->
```

This should succesfully import React into our browser. Now let's create a Hello World.


```html
<script>
	var element = React.createElement('h1', null, 'Hello World')
</script>
```

The createElement method uses 3 arguments. The first is the element to be created, the second is the element's properties and the third is the child property. In this situation we do not want out element to have any properties so we keep it at *null*. Remember this is just the virtual DOM. To be able to successfully render this into the browser, we need to use the ReactDOM library. So let's some add some code to render our virtual DOM into the real stuff. 

```html
<script>
	ReactDOM.render(element, document.getElementById('react-container');
</script>
```

The first argument is the virtual DOM we want rendered and the second argument, we use a selector to tell ReactDOM where to render the virtual DOM to.

You can check out the entire code [here](https://gist.github.com/raajable/c29750b60ce39641e71e77c28cb942ec).

# Second Post coming in at 1:04PM
## Automation
React is purely Javascript based, meaning we can use Javascript data structures to build HTML elements. Let's look at an example. Let's say we wanted to create a list of all the provisions we need for school. With normal HTML we do it like this
```html
<html>
<head>
	<title>Provisions</title>
</head>
<body>
	<ul class="provisionList">
		<li>Gari</li>
		<li>Shito</li>
		<li>Rice</li>
		<li>Groundnuts</li>
	</ul>
</body>
</html>
```

This example here is static, in normal html. What if we wanted to change any of the provisions, let's say remove Gari because we've already bought it. We need to go into our HTML and take out the *<li>* tag containing Gari. In HTML our data is closely binded with our code. Let's try doing this in React.

```html
<!DOCTYPE html>
<html>
<head>
	<title>Provision</title>
</head>
<body>
	<div id='react-container'></div>
	<!-- We import the React and ReactDOM library -->
	<script src='https://unpkg.com/react@15.4.2/dist/react.js' type="text/javascript"></script>
	<script src='https://unpkg.com/react-dom@15.4.2/dist/react-dom.js' type="text/javascript"></script>
	<script type="text/javascript">
		const provisions = ['Gari', 'Shito', 'Rice', 'Groundnuts'] //We create a data structure to hold our provisions

		//Let's build the elements now
		var provisionsElement = React.createElement('ul', {className : 'provisionsElement'}, 
            provisions.map((provision, i) => React.createElement('li', {className : i}, provision))
			)

		//Time to render
		ReactDOM.render(provisionsElement, document.getElementById('react-container'));
	</script>
</body>
</html>
```