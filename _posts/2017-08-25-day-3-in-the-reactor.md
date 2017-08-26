---
title : "Day 3 in the Reactor"
layout : post
excerpt : "3nd day of my journey studying react"
image : /assets/image/react-logo.png
tags : 
    - post
    - react
---

## Babel

*Therefore its name is called Babel, because there the Lord confused the language of all the earth; and from there the Lord scattered them abroad over the face of all the earth.
— Genesis 11:1–9*

This is a bible story of men who tried building a tower to reach the Heavens. The Lord came down and changed their languages so they wouldn't understand each other. From there came confusion, and they abandoned the building project and scattered across the face of the earth.


Well, that's JavaScript today. One hot mess of different things, from libraries to frameworks. Biggest community I've ever seen. Today we have so many browsers that don't work the same. Some understand ES6 and some don't. And even some understand ES6 in different ways creating a situation where your code wont act the same across different browsers. Babel is a library that aims to end this. Babel *transpiles* your ES6 code to ES5. All modern browsers support ES5 well enough. This allows us to feel comfortable writing our good ES6 code which can be translated to ES6 for browsers that don't understand it. Babel also performs another very important task. It translates something called JSX into pure React code. Okay I didn't tell you, but well i didn't know. You can write React using a different and easier syntax called JSX. The browser does not understand JSX so we need to transpile it to Pure React, code which the browser understands before we can run it. So let's add Babel to our project. For now we will render in our browser. I understand this isn't the best way but for now, we will use it and once we totally understand the concepts, we can start rendering stuff server-side and not in the browser. All we need to do is add Babel's CDN to our browser

```javascript
<script src='https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.29/browser.js'></script>
```

Another slight change, the script tag we are going to be writing our React code in has to be tweaked a little bit, like this

```javascript
<script type="text/babel">
	
</script>
```

This allows Babel to know what to transpile. Now let's get into JSX

## JSX
JSX is a preprocessor that allows us to use good ol' XML in our JavaScript code. JSX looks a lot like HTML. Of course, you can use React without JSX, it's what we've been doing the whole time but JSX just makes it easier. Let's try it out

Pure React
```javascript
React.DOM.ul(
	{className : 'myList'}, 
	React.DOM.li(null, 'foo'),
	React.DOM.li(null, bar)
) 
```

JSX
```javascript
<ul className='myList'>
	<li>foo</li>
	<li>bar</li>
</ul>
```

Looks just like HTML right..? I found a really good introduction to JSX [here](https://facebook.github.io/react/docs/introducing-jsx.html)
