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

# Second Post coming in at 1:04 PM
### I like to call this one Automation
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

Let's analyse all our code one by one. First we created a data structure, an array to hold all of our provisions and called it *provisions*. Then we set out to build our elements using the method *React.createElement()*. The first argument, *ul* is the name of the element we wish to create. The second argument is the properties. We wish to give our *ul* element a class. In React, the *class* word is reserved so we have to use *className*. The third argument is the children we wish to add to the ul element. Children can range from a string to another element. Inside our *ul* element we wish to create *li* children with each one holding a provision stored in our array. We can easily use the .map method to iterate through each provision in our array and on each provision, we will create a new *li* element to hold the provision. Let's look at this code again.

```javascript
//Create *ul* element, on each item in array, create a child element called *li* to hold that item
React.createElement('ul', {className : 'provisionsElement'}, 
provisions.map((provisions, i) => React.createElement('li', {className : i}, provision))) 
```
Note that we used ES6 arrow functions. This is key because it makes our code cleaner. We also used some functional programming features in here like creating a function that returns a function


React's style is much more handy because now our code has the ability to scale and we can easily change or remove the provision items just by changing the items in the provisions array. Super cool right.

You may grab the code from [here](https://gist.github.com/raajable/9282631bbe3d32d463f54bafdfbe16f7)

# Third Post coming in at 5:18 PM
### Reusability
When thinking about resusability in an Object Oriented Programming World, we think Classes. Classes allow us to describe a thing, then we can create instances of that class called objects. Now enough with the college OOP talk. Let's get to business


Now let's say we have a certain piece of UI that appears so many times on our webpage. Do we hard code the UI each time. Don't Repeat Yourself. Never. React Components to the rescue. With components we can create a class that will create new instances of our component whenever we want it to and if we wanted to go further, we could build components on top of other components through good ol' inheritance!. 
I understand there are several ways to create React components but so far I know of two. 


The common style is using the React.createClass() method. This style is very popular in a lot of codebases around the world but it may be deprecated soon. We don't want to write code that will break soon so let's go for a newer style that makes use of the new ES6 class inheritance feature. Yeeaah, let's be progressive. React already has a blueprint class we can inherit from. It's called React.component so we use create a class and inherit from the React.component class using ES6 style
```javascript
class Provisions extends React.Component 
```
In this piece of code, we created a class and asked it to inherit from React.Component. I think this makes way more sense than using React.createClass() method. Thank you ES6!


Now let's build our class
```html
<!DOCTYPE html>
<html>
<head>
	<title>React Example</title>
</head>
<body>
	<div id='react-container'></div>
	<script src='https://unpkg.com/react@15.4.2/dist/react.js' type="text/javascript"></script>
	<script src='https://unpkg.com/react-dom@15.4.2/dist/react-dom.js' type="text/javascript"></script>
	<script>
		const provisions = ['Gari', 'Shito', 'Rice', 'Groundnuts'];
		class ListProvisions extends React.Component{
			render(){ //A method that returns a function. Hi Functional Programming
				return React.createElement('ul', {className : 'list'}, 
                    this.props.provisions.map((item, i) => React.createElement('li', {className : i}, item))
					)
			}
		}

		const provisionsComponent = React.createElement(ListProvisions, {provisions}, null);
		ReactDOM.render(provisionsComponent, document.getElementById('react-container'));

	</script>
</body>
</html>
```

So let's analyze this nasty piece of code bit by bit. We created a class using the class syntax from ES6
```javascript
class ListComponent extends React.Component
```

Now we create a *render* method that returns a function. This function will run anytime our class is called. We want to create an element that lists our provisions data so we need to put that in the *render* function and return it like this

```javascript
class ListProvisions extends React.Component{
			render(){ 
				return React.createElement('ul', {className : 'list'}, 
                    this.props.provisions.map((item, i) => React.createElement('li', {className : i}, item))
					)
			}
		}
```

Now let's create instances of our class, an object or in React lang a component. We do that by using the *React.createElement()* method like this
```javascript
const provisionsComponent = React.createElement(ListComponent, {provisions}, null);
```

The first argument is the name of the element, in this situation a ReactComponent class. The second is the properties we wish to pass to our class which is the provisions array and the third argument is the children. In this situation we don't want children, so we make it *null*.

Then we render with ReactDOM. You must be familiar with this by now

```javascript
ReactDOM.render(provisionsComponent, document.getElementById('react-container'));
```

The idea behind this system is we can create multiple instances from our *ListComponent* class and render it.

Grab the code from [here](https://gist.github.com/raajable/901aec6e2d006861bf45eebcde184b14)

# Fourth Post coming in at 7:18 PM
### Stateless Functional Components 
So we created React components using classes. This style will remind you of the Object Oriented Programming Paradigm. There is another way to create React components and this style follows the Functional Programming paradigm very closely. So a Stateless Functional Component is a pure function. A pure function takes at least one argument, and returns a new value based on that argument. Note that it does not mutate it's argument, it does not change anything around it's world. This follows closely with the idea of immutability in Functional Programming. Creating a React Component using a function can be done like this
```javascript
const createProvisions = props =>
	React.createElement('ul', {className : 'provisions'}, 
	props.provisions.map((provision, i) => React.createElement('li', {className : i}, provision))
	)
```

That's all, really that's it. Note that our *createProvisions* function takes one argument and returns a function using that argument. So we just create an instance of it, and render like this 

```javascript
const provisionsComponent = React.createElement(createProvisions, {provisions}, null);
ReactDOM.render(provisionsComponent, document.getElementById('react-container'));
```

When React.createElement is run on the function, it picks up the argument from the props object and uses it. 

This style arguably keeps things simpler and I also understand this style is better performance-wise. I still don't know why by the way. Hopefully will figure that out in the coming days.

Check out the whole code [here](https://gist.github.com/raajable/4e048596cfee665ec6a788503caa0d67)