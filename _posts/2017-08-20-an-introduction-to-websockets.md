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
When a connection is opened, the connection event is fired. The connection object is passed to the socket variable. A websocket is alive in the socket object
Remember websockets only work when the client agrees to the connection, so we need to add some code client side to make this happen. We create an index.html file and add this

```html
 <script src='/socket.io/socket.io.js'></script>
        <script>
            var socket = io();
        </script>
```

This starts socket.io on the client side and we are in business. When we run our app, we get *A user connected* printed to the screen. Each time we open a new tab and connect, it prints. A websocket is alive. There are other built in events for the socket object such as *disconnect*. Let's try it out.  

```javascript
socket.on('disconnect', function(){
    console.log('A user disconnected!');
})
```

When we open a tab and connect, *A user connected* prints to our console. When we close the tab, *A user disconnected* is printed out to our console. Our websocket is working!. What makes socket amazing is you can create your own events, once those events are triggered, you can push some data to the client or to the server. It works both ways!. Let's create a timer that fires a storm event 5 seconds after the client makes a request and make the client fire back an event to show they have received it.


First we need to create an event and the message, server side
```javascript
io.emit('storm', 'A storm is coming') //The first argument is the event name, second is the message
```

We plug it into a timer function then plug it into the connection event. At the end we should have something like this

```javascript
io.on('connection', function(socket){
	console.log('A new client has connected');
	socket.on('disconnect', function(){
		console.log('A client has disconnected');
	})

    //The timer function to emit the event 5 seconds after client connects
	setTimeout(function(){
		io.emit('storm', 'A storm is coming!')
	}, 5000);
		
})
```

Then we plug in a space in our client side for the message to show when the server sends it.Lets also plug in jquery to make this a bit easier!
```html
<p id = 'message'></p>
 <script src='/socket.io/socket.io.js'></script>
 <script src="https://code.jquery.com/jquery-1.11.1.js"></script>
        <script>
            var socket = io();
            //Storm event handler
            socket.on('storm', function(msg){
                $('#message').append(msg) //This adds the msg variable which contains the message in our event
            })
        </script>
```

There!. Once you start the app and open the page, a websocket will be created. 5 seconds later, the storm event will be emitted by the server. On emission, the storm event handler in our client will be triggered and add the message to our paragraph tag. The message should then pop up on our page. Let's take this a bit further and send a message to our server that we received it. Same process, we emit an event on the client side, create an event handler on the server side to handle that event. Well, talk is cheap, let me show you the code


The event is emitted client side
```javascript
socket.emit('received', 'The storm message has been well received!');
```

The event is caught server side
```javascript
socket.on('received', function(msg){
    console.log(msg)
})
```

When we run our app again, the storm message should show client side and the server should spit out a message into the console that our storm message was well received!



This is the [code](https://github.com/raajable/socketIO-example) of the entire example. Happy coding!
