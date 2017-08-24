---
title : "Day 2 in the Reactor"
layout : post
excerpt : "2nd day of my journey studying react"
image : /assets/image/react-logo.png
tags : 
    - post
    - react
---
# First Post coming in at 10 AM
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