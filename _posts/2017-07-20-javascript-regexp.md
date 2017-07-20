---
title : "Regular /E*x[pre].ssions/"
image : 
layout : post
excerpt : "Regular Expressions in JavaScript"
tags : 
    - tutorial
    - javascript
---
For a very long time Regular Expressions were hell for me. I saw them as some nasty garbled text that had no meaning and the first I tried learning them, I got really confused and simply avoided them for as long as I could.
When I finally decided to learn them, I realised with some good concentration I was writing my own pieces of 'garbled text'. 

Regular Expressions are simply a way to match specific strings in a large block of strings. It's very handy if you had a large essay file and needed to find some specific strings in the essay. Let's begin.

You can create a regex in Javascript in two ways;

### Using a regex literal
```javascript
var regexp = /abcde/
``` 

### Using a constructor function
```javascript
 var regexp = new RegExp('abcde')
```
It's advisable to use the regex literal if your regexp is going to be fixed throughout the life of your program and because the Javascript interpreter compiles it at once while it is better to use the constructor function if your regexp wont be fixed and is obtained from an external source, let's say user input.

When you create a regexp, it is made an object meaning you can use methods on it. An example is the test method which returns true or false depending on whether the match is found. 

### Example
```javascript
 var regexp = /abc/
 console.log(regexp.test('abc')) //This returns true
 console.log(regexp.test('happy')) //This returns false
```

In the above code, we run the test method with the argument 'abc'. It checked this argument with the string stored in our regexp and when our string was matched, it returned true.
You can see it returned false on our second test because the string stored in our regexp variable was not matched in the 'happy' text.

Regular Expressions make use of certain keywords to indicate the action you want to take and I will try to take you through them one by one.
