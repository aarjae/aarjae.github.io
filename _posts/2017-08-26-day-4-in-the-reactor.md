---
title : "Day 4 in the Reactor"
layout : post
excerpt : "4th day of my journey studying react"
image : /assets/image/react-logo.png
tags : 
    - post
    - react
---

So today I decided to put all my React knowledge to use. Components and some JSX. So I figured I do something that React fixes so well, rendering lots of data. I got some tech articles data from [Lists](https://lists.design). It's a website that gives tons of real world JSON data for use in your mockups.

I downloaded some tech articles JSON, changed the extension to *.js* and assigned the whole data to a variable called articles then imported it into my browser using the *script* tag.

You can download the new js file from [here](https://github.com/raajable/theReactor/blob/master/day4%20-%20Rendering%20tons%20of%20data/articlestech-en.js) if you don't wanna go through all that. But it's worth checking out that site by the way.

Now that we have some data we can render, we will set out building two components. A menu component and an article component. We will use stateless functional methods to pull it off, well, mainly cos we want to dodge the headache of *this*, haha..

Let's build our menu component
```javascript
const Menu = ({pageTitle, articles}) =>
			<div>
				<h1 className="title">{pageTitle}</h1>
				{articles.map((article, i) =>
					<Article key={i} data={article.data}>
					</Article>
				)}
			</div>
```

Note that I destructured the *pageTitle* and *articles* properties that way we don't have to type *props.pageTitle* and *props.articles* each time we want to use those properties. We used JSX to create an *h1* heading and we started iterating through our data with map. On each data we reach in the array, we call an *Article* component and set properties, the first being the key then the data, which is the article itself. Note that we are using an Article component we have not created yet. Let's do that now

```javascript
const Article = ({key, data}) =>
			<article>
				<h1>{'Article'}</h1>
				<p>{data}</p>
			</article>
```

We created an article component with prop arguments of key and data. Note that I destructured the arguments again so we don't have to type *props* each time. I then created an h1 element with a simple string of Article and a p element to hold the article data. You will realise all the arguments the Article component is using was passed in as properties by the Menu component. Get the whole idea?


Now we render.
```javascript
ReactDOM.render(
			<Menu pageTitle="Random Tech Articles" articles={articles}/>,
			document.getElementById('react-container')
		)
```

We render with JSX too!. We add the Menu component with a pageTitle property which is a string and an articles property which is our JSON data. And we are done...


This is really amazing, we are creating re-usable components and we can mix them up anyhow we want! Also our data is very well seperated from our code, so there is no problem when the data changes. As long as the JSON property names don't change and even if they do, we just change a few variables in our code and we are done!

You can pick up the entire code of this example from [here](https://github.com/raajable/theReactor/tree/master/day4%20-%20Rendering%20tons%20of%20data)		