---
title : "Day 2 in the Reactor"
layout : post
excerpt : "2nd day of my journey studying react"
image : /assets/image/react-logo.png
tags : 
    - post
    - react
---
### Spotlight on ReactDOM
Yesterday I learnt React and ReactDOM are two seperate things. React itself being the core library with a virtual DOM represented in JavaScript data structures and ReactDOM being the library that handles converting this virtual DOM into real HTML elements for the browser to consume. Let's take a look at the ReactDOM and how it works further.


Rendering an element is the most costly DOM operation. It takes a relatively large amount of CPU time and ReactDOM tries to keep re-rendering as minimal as possible. Let's say we had our provisions list 

```html
<!DOCTYPE html>
<html>
<head>
	<title>React</title>
</head>
<body>
	<ul class="provisions">
		<li>Gari</li>
		<li>Shito</li>
		<li>Rice</li>
		<li>Groundnuts</li>
	</ul>
</body>
</html>
```

And we want to change the Gari and Shito provisions to Sardine and Milk respectively. Does ReactDOM render everything all over again once you change the elements..? No, it doesn't. ReactDOM compares the old component to the new one, looks at the differences between the two and only changes the elements that are different. This keeps rendering as minimal as possible and keeps React fast.

### React Factories - It just got easier :)
So far we only know how to create elements using the React.createElement() method. Well there is an easier way that allows us to abstract some little details away. Let's check it out. This is what we know now
```javascript
React.createElement('h1', null, 'Hello World')
```

And this is using a React factory
```javascript
React.DOM.h1(null, 'Hello World')
```

Haha ;)



