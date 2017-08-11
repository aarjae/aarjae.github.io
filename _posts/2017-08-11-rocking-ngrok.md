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
your device. Then you sign up. You will be given an authtoken after you sign up. We shall use that later
Unzip the file you downloaded and you will have a single file called ngrok. We need to set permissions to allow
it run as an executable. Open the terminal in the directory and run 
> sudo chmod a+x

Once you are done, you simply run
> ./ngrok

ngrok should spit out a long list of stuff. Great, ngrok is working. Let us set up a simple express
app called server.js on localhost and start serving it over the web. This is my code

``` javascript
const express = require('express');
const app = express();

app.get('/', function(req, res){
    res.send('Hello World')
});

app.listen(3000);
```

In this example, we set up a simple node server on ``` localhost:3000 ```. Normally you can only access this own 
your own machine. Time to put it up on the web!.

Run the node app
> node server.js

Then you head over to the ngrok directory. We need to set up the authtoken given to us on the ngrok site.
Let's presume our authtoken is YD7838DH8D
We do that like this in the ngrok directory
> ./ngrok authtoken YD7838DH8D

That should set up our authtoken. Now we need to tell ngrok to make available our Express app which is 
running on port 3000 to a public url. You do that like this 
> ./ngrok http 3000

A neat CLI dashboard should appear. Something like this 
![ngrok-cli](/assets/image/ngrok-dashboard.png)

The web interface is the link to a graphical dashboard in your browser to monitor server analytics
The Forwarding entry is a link to access your Express app over the internet

![final](/assets/image/ngrok-final.png)

All we need to do is copy that `Forwarding` link and we can share it with friends to access our express app
from anywhere in the world!


Cheers, enjoy!
