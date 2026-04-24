Collaborative Code Editor

A real-time collaborative code editor built with React and Node.js, supporting codebase creation, owner-based authentication, live chat, and seamless collaboration. Powered by Yjs for conflict-free real-time synchronization and JWT for secure authentication.

Features

Codebase Creation & Management: Create and manage codebases with secure ownership.

Authentication: JWT-based secure login and access control.

Role-Based Access: Codebase owners can grant or restrict permissions.

Real-Time Collaboration: Multiple users can edit simultaneously with conflict resolution powered by Yjs.

Live Chat: Built-in communication channel for contributors within the same codebase.

Database Integration: MongoDB used for storing user data, authentication tokens, and codebase metadata.

Tech Stack
Frontend

React.js – UI development

Yjs – Real-time collaboration layer

WebSockets / WebRTC – Communication

Backend

Node.js with Express.js – API and server logic

JWT – Authentication and authorization

MongoDB – Database for users, sessions, and codebases

Additional Tools

Socket.IO – Real-time messaging and synchronization

Bcrypt – Password hashing for security

System Design
1. Architecture

The system follows a client-server model with real-time synchronization:

Client (React + Yjs): Handles editor rendering, collaboration states, and live updates.

Server (Node.js + Express): Manages authentication, API endpoints, codebase metadata, and chat integration.

Database (MongoDB): Stores user credentials, JWTs, chat history, and codebase information.

2. Workflow

User Authentication

Users log in via JWT authentication.

Owner-based authentication controls who can access or modify a codebase.

Code Collaboration

Yjs CRDT ensures real-time sync of code edits.

Conflict-free merges allow multiple contributors to edit the same file simultaneously.

Live Chat

Socket.IO enables real-time messaging inside a codebase session.

Data Storage

MongoDB holds user data, codebase metadata, and chat history.

Code changes are synchronized across clients via Yjs documents rather than stored directly in MongoDB, reducing server load.


+-------------------+       +------------------+       +------------------+
|   React Client    | <-->  |   Node.js API    | <-->  |     MongoDB      |
|  (Code Editor +   |       | (Express + JWT)  |       | (User + Metadata)|
|   Yjs + Socket.IO)|       |                  |       |                  |
+-------------------+       +------------------+       +------------------+
         |                          |
         |                          |
         +---------- Live Chat ------+

         <img width="1280" height="625" alt="image" src="https://github.com/user-attachments/assets/a4254ff1-5d7c-4e04-b7ff-3b97db5f7f2a" />
<img width="1280" height="579" alt="image" src="https://github.com/user-attachments/assets/031587d1-90d8-4555-8350-f509cd5f6037" />

