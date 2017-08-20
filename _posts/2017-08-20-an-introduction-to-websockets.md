---
title : "A beginner's introduction to websockets in Express"
layout : post
excerpt : "Websockets and Express"
tags : 
    - tutorial
    - socket.io
    - node.JS
---
![websockets](/assets/image/websocket-heading.gif)


When thinking about websockets, the first thing to come to mind is *real-time*. How do you push a notification
to your client on the client-side. How do you send a client a message or tell them something new has happened, in that same moment it happened. Well websockets are your answer.


# The problem
Historically, the HTTP standard has strictly stuck to the client-server model where one side of a connection acts as the client and the other side acts as the server. The client makes requests and the server responds. That's it. The server can never make a request, only the client is able to do that. All the server ever does is respond to requests. Okay, imagine you have a weather application that notifies a client whenever a storm may occur. Your web application pulls in the weather info, does it's magic to retrieve the data and realises there is a storm coming. It has to notify the client now!. But wait, a server cannot initiate a connection. Till the client makes a request, the server cannot pass a message to it. Your application is useless.

Let's explore one way we could fix this problem. How about we just insert some javascript into the client's page that automatically makes a request every 5 seconds. That's very possible. It's called polling. Constantly sending a request to the server so that once a server has something to respond with, the client will make a request in that timeframe and the server will be able to respond with the message. Now there are many problems with this particular solution, mainly performance. You see, everytime the client makes a request 
it sends in the HTTP headers(Cookies, Session data, etc). It does this each time, the same headers. The server is going to have to spend time making sense of all this data when in fact, in this situation, such data is useless to the server. All of this results in wasted CPU time. Of course, in a very small application, this may not be a problem at all, but once the application becomes larger and larger, imagine a billion users sending useless requests to your server every 5 seconds. That's scary...


# Websockets to the rescue!
Websockets is a new HTTP thing that fixes this problem. With websockets, a client makes a request to the server. The server responds with a special HTTP header called *Upgrade* that asks the client to accept to keep an open connection with the server. This connection is constantly open, HTTP headers are not sent each time and the server can push data to the client at any time an event is triggered on it's side. This is easier. There is no polling, no useless requests. Data is only pushed across the wire when it's relevant. Now let's get to making a basic websocket happen. We are not going to be using HTTPs *WebSocket API*, instead we are going to be using a wrapper around this API called [Socket.IO](https://socket.io). Socket.IO takes all the pain of cross-browser compatibility away and makes using websockets relatively easier. Let's begin


First let's create a new Express project, the npm ritual. Create a folder and open a terminal to it and run
> npm init
We add all the required info then we download the modules we need, express, ejs and socket.io
> npm i --save express ejs socket.io

Let's create a basic express server and add socket.io functionality
``` javascript
const express = require('express'),
	  app = express(), //Instantiating an express server
	  http = require('http').Server(app), //Passing the express instance to http
	  io = require('socket.io')(http); //Adding socket.io and passing the http object as an argument


app.get('/', function(req, res){
	res.sendFile('index.html')
});

http.listen(3000);
```

Socket.IO is event based. Let's add an event handler that prints to the screen.

```javascript
io.on('connection', function(socket){
    console.log('A user connected!');
})
```

Remember websockets only work when the client agrees to the connection, so we need to add some code client side to make this happen. We create an index.html file and add this

```html
 <script src='/socket.io/socket.io.js'></script>
        <script>
            var socket = io();
        </script>
```

This         