Spring Boot WebSocket Notification System
Overview


    This project shows how to build a real-time notification system using Spring Boot and WebSocket.
     In normal web applications, the client sends a request and the server responds.
     But in WebSocket, the server can send messages to clients instantly without waiting for a request.

In this project:


    A client sends a message to the server
    The server receives the message
    The server sends that message to all connected clients

This type of system is useful for:


    Chat applications
    Live notifications 
     Real-time updates

Project Tutorial (Video)


    If you want to understand how this project works step-by-step, you can watch this tutorial video:
    https://youtu.be/sqYqyr6EpAU?si=Ja7gmzAMZQXY9oQQ
    

Project Architecture

    Client (Browser)
      ↓
    WebSocket Connection
      ↓
    Spring Boot Application
      ↓
    Notification Controller
      ↓
     Message Broker
      ↓
    Broadcast Message
      ↓
    All Connected Clients
    

Technologies Used

       Backend
    Spring Boot
    Spring Web
    Real-time Communication
    Spring WebSocket
    STOMP Protocol
    SockJS

Frontend

 
     HTML
    JavaScript
    Build Tool
    


Maven

     Project Structure
     src/main/java/com/notifications
     config
      WebSocketConfig
    controller
        NotificationController

    main
      NotificationSystemApplication 
    resources
       templates
        index.html

        
Important Concepts
    WebSocket

    WebSocket allows two-way communication between client and server.
    The connection stays open, so the server can send messages to the client at any time.


This is useful for:

    live updates
    messaging systems
    notification systems


STOMP Protocol

    This project uses STOMP messaging protocol with WebSocket.
    STOMP helps manage messages between the client and server using topics and subscriptions.


WebSocket Configuration

    WebSocket configuration is written in:

         WebSocketConfig.java
         

This class does three main things:

      Enable WebSocket communication

     Configure message broker

    Create WebSocket connection endpoint


Important paths used in the project:

     Client sends message to:

     /app/sendMessage


Server sends message to clients:

     /topic/notifications

    WebSocket connection endpoint:

    /ws

    

SockJS is also used to support browsers that do not support WebSocket.

    Message Flow

    Step 1
     Client sends a message

    ↓

    Step 2
     Server receives the message in the controller

    ↓

    Step 3
     Server broadcasts the message

    ↓

    Step 4
     All connected clients receive the message instantly


Example

    User sends message

    Hello Server

    Server broadcasts

    Hello Server

    All connected users receive the message.


Running the Project
Prerequisites

     You need:

     Java 17+

     Maven

     1 Clone the project
     git clone https://github.com/sheetalrajkumariri/websocket-notification-system.git
    2 Go to project folder
    cd websocket-notification-system
    3 Run the project
     mvn spring-boot:run

    or run the main class:


NotificationSystemApplication

        4 Open the application

       Open browser and go to:

     http://localhost:8080
     

Now you can send and receive real-time messages.

    Key Features

    Real-time messaging using WebSocket

    Server can send messages instantly

    Multiple clients receive the same message

    STOMP messaging protocol support

    Simple Spring Boot architecture

    What You Learn From This Project

    From this project you can learn:

     How WebSocket works in Spring Boot

     How to send messages between client and server


How to broadcast messages to multiple users

    How to build real-time applications


Summary

     This project demonstrates how to build a real-time notification system using Spring Boot WebSocket.

     WebSocket allows instant communication between server and clients, which is very useful for modern web applications.
