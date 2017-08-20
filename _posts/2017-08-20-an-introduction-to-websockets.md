---
title : "A beginner's introduction to websockets in Express"
layout : post
excerpt : "Websockets and Express"
tags : 
    - tutorial
    - socket.io
    - node.JS
---
![websockets](assets/image/websocket-heading.gif)
When thinking about websockets, the first thing to come to mind is *real-time*. How do you push a notification
to your user on the client-side. How do you send a user a message or tell them something new has happened, in that same moment it happened. Well websockets are your answer.

# The problem
Historically, the HTTP standard has strictly stuck to the client-server model where one side of a connection acts as the client and the other side acts as the server. The client makes requests and the server responds. That's it. The server can never make a request, only the client is able to do that. All the server ever does is respond to requests