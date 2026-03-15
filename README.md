 Spring Boot WebSocket Notification Project
 Project Overview

This project shows how to create real-time communication using WebSocket in Spring Boot.

Normally in web applications, the client sends a request and the server responds.
But in WebSocket, the server can send messages to clients instantly without waiting for a request.

In this project:

A client sends a message to the server.

The server receives it.

The server sends that message to all connected clients.

This is useful for chat apps, live notifications, or live updates.

 Technologies Used

Java

Spring Boot

Spring WebSocket

STOMP Protocol

SockJS

Maven

 Project Dependencies

Dependencies are written in pom.xml.

1. Spring Web

Used to create web applications and REST APIs.

<dependency>
 <groupId>org.springframework.boot</groupId>
 <artifactId>spring-boot-starter-web</artifactId>
</dependency>
2. Spring WebSocket

Used to enable real-time communication between client and server.

<dependency>
 <groupId>org.springframework.boot</groupId>
 <artifactId>spring-boot-starter-websocket</artifactId>
</dependency>
3. Thymeleaf

Used to create HTML pages for the frontend.

<dependency>
 <groupId>org.springframework.boot</groupId>
 <artifactId>spring-boot-starter-thymeleaf</artifactId>
</dependency>
📁 Project Structure
src
 └── main
      ├── java
      │     └── com.websocket
      │            ├── config
      │            │     └── WebSocketConfig.java
      │            │
      │            ├── controller
      │            │     └── NotificationController.java
      │            │
      │            └── NotificationSystemApplication.java
      │
      └── resources
            └── templates
                  └── index.html
 How the Project Works (Step by Step)
🔹 Step 1: Enable WebSocket

In the configuration class we enable WebSocket using:

@EnableWebSocketMessageBroker

This tells Spring Boot that WebSocket messaging will be used in the project.

🔹 Step 2: Configure WebSocket

File:

WebSocketConfig.java

This class configures:

WebSocket endpoint

Message broker

Client communication

Example:

config.enableSimpleBroker("/topic");
config.setApplicationDestinationPrefixes("/app");
Explanation
Path	Meaning
/app	client sends message to server
/topic	server sends message to clients
🔹 Step 3: WebSocket Endpoint

In configuration we create an endpoint:

registry.addEndpoint("/ws").withSockJS();

This endpoint is used by clients to connect to WebSocket.

Client connection URL:

http://localhost:8080/ws
🔹 Step 4: Create Controller

File:

NotificationController.java

This controller handles messages from clients.

Example:

@MessageMapping("/sendMessage")
@SendTo("/topic/notifications")
Explanation
Annotation	Purpose
@MessageMapping	receives message from client
@SendTo	sends message to all clients
Method Example
public String sendMessage(String message){
    System.out.println("Message: " + message);
    return message;
}

Flow:

Client sends message

Server receives message

Server broadcasts message to all clients

🔄 Message Flow
Client
   │
   │ send message
   ▼
/app/sendMessage
   │
   ▼
Server Controller
   │
   │ broadcast
   ▼
/topic/notifications
   │
   ▼
All Connected Clients
▶️ How to Run the Project
1. Clone the project
git clone your-project-link
2. Run the project
mvn spring-boot:run

or run the main class:

NotificationSystemApplication.java
3. Open browser
http://localhost:8080
 Where This Project Can Be Used

This project idea can be used in:

Chat applications

Live notifications

Stock market updates

Order status updates

Multiplayer games

 Conclusion

This project demonstrates how to build a real-time notification system using Spring Boot WebSocket.

WebSocket allows instant communication between server and clients, which is very useful for modern applications.
