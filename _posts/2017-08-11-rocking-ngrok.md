---
title : "Rocking ngrok on linux!"
image : /assets/image/ngrok-cover.png
layout : post
excerpt : "Ngrok with node"
tags : 
    - tutorial
    - ngrok
    - ubuntu
---

Ever wanted to use your device as a web server..?
Ever wanted to quickly show some work on your localhost to a team member somewhere on the planet and you were
forced to deploy your code to Heroku or some other free hosting?

Ngrok to the rescue!

Ngrok is basically a tool that allows you to turn your computer into a web server. All you need to do is
run it and it provides with you with a public url you can use to access your localhost over the internet.
Let's try to access a node app running on localhost with ngrok now.

## Setting Up ngrok on Linux 
First you head over to [the ngrok website](https://ngrok.com/download) and download the executable for 
your device. You unzip it and you have a single file called ngrok. We need to set the permissions to allow
it run as an executable. Open the terminal and run 
> sudo chmod a+x

Once you are done, you simply run
> ./ngrok

Ngrok should spit out a long list of stuff. Great, ngrok is working great. Let us set up a simple express
app on localhost and start serving it over the web. This is my file

``` javascript
const express = require('express');
const app = express();

app.get('/', function(req, res){
    res.send('Hello World')
});

app.listen(3000);
```
