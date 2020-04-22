---
title: "Chat Room"
description: "A Java peer-to-peer chatroom where people can send messages and communicate with each other"
layout: post

media-folder: "ChatRoom"
featured: "ft.jpg"
skills: [Java, Unit Testing, Concurrency, Networking]
---
*Application built with **Java**.*

*Application and source code available on <a href="https://github.com/abdullahibneat/p2p-chat-room">GitHub</a>.*

ChatRoom was part of the Advanced Programming course at University. The objective of the course was to introduce us to Networking, Concurrency and Unit Testing to develop more complex and robust programs.

![{{ post.title }}](https://i.imgur.com/Chp5wys.png)

The requirement was to produce a program that allows the finding of a root of given functions with the option to choose different root finding techniques while using different data structures. The requirements were as follows:

- Network must be peer-to-peer, allowing communication between all members
- New members only need to provide an ID, a port to listen to, and port and IP address of an existing member.
- The first member to join is the coordinator, and they must be notified about this.
- The network must be able to select a new coordinator when the previous coordinator becomes unavailable

I started by creating a simple terminal based application. By asking for an IP address and a port from the user, I was able to establish a communication between two users. At this stage, having identified the ServerSocket as a component that listens for incoming connection requests at all times, I run it in its own thread so to not block the main thread. Due to the simplicity of the implementation the each user would need to add new users manually, by typing the command `/add ADRESS:PORT`.

So far I've been using PrintWriters to send data among users. This was a constraint since commands cannot be automated to make the manual adding of users redundant. Therefore, I switched to the ObjectOutputStream, which allows me to send Java objects over the network. I implemented a class to store the details of a member (i.e. username, IP address and port), and in the ServerThread I check for objects that are received by the client:

- String: A message was received by someone else in the group. Show it to the user
- Member: Someone connected to the group, so add them in the background and notify the user about the new user

The messages could have been improved further. Instead of relying on strings, which could be manipulated by the sender, I created another class, Message, which contains the details about the sender of the message, the time it was sent, and the contents of the message.

The final program can be visualized in the following flow charts:

![{{ post.title }}]({{ site.url  }}/{{ site.media-folder }}/{{ page.media-folder }}/1.jpg)

For testing the program, I used the JUnit framework to perform automated tests. Prior to implementing such tests, I would launch a few instances of the program, and ensure that communications were not affected by any changes I would make. Before writing my tests, I needed to adjust the Client to have an option to disable the GUI. This was quite achieved by simply adding a parameter to the constructor that controls the visibility of the JFrame.

Tests include:

- Group formation, connection and communication, where a group should be correctly formed connecting with all members where all members can communicate without any error.
- Group state maintenance: the state of the group must be maintained correctly. This includes recording of the messages exchanged among members of the group
- Coordinator selection: automatically choose the coordinator when the existing coordinator disconnects abnormally.

This coursework taught me how network programs are written, and how multi-threading can be used to increase the efficiency of software. It also shone a light on the difficulties of using Threads, since tests need to be written in such a way to allow threads to complete their task before asserting values.