# Python GUI ChatRoom With Call Functions

A lightweight, chat and voice application built with Python. This project features a server for broadcasting group text messages and a Peer to peer (P2P) routing protocol for voice calls. It utilizes TCP sockets for text communication and the `vidstream` library for voice calls, all in a custom Tkinter GUI.

## Features

*   **Group Text Chat:** Users can join a central server chatroom and broadcast text messages to all connected clients instantly.
*   **Peer to Peer Voice Calling:** Users can select a specific active user from the interface and start a private voice call.
*   **Server Routing & IP Injection:** The server acts as a router. When a call is started, it intercepts the signal, puts the sender's IP address onto the packet, and routes it only to the target user. 
*   **Dynamic Port Allocation:** To prevent OS-level socket lockouts (like Windows `TIME_WAIT`), the client generates randomized, unique audio ports for every single voice call.
*   **Auto-Updating User List:** The server automatically detects client connections/disconnections and broadcasts updated active user lists to all clients.
*   **Very Modular:** The codebase separates the Model (Socket Networking), View (Tkinter UI), and Audio subsystems, using a central Controller (`Main.py`) to manage threads and calls safely.

## Limitations

*   **User to User Audio Only:** Because the application uses direct Peer to Peer connections for voice data, audio calls are limited to two users. Group voice calling is not supported.
*   **No NAT Traversal:** The application does not utilize STUN/TURN servers. So it can only work in a local setting on 1 network.
*   **Enterprise Network Restrictions:** When running on massive networks (like Company or University Wi-Fi), clients must be on the exact same subnet for P2P audio to connect.

## Getting Started (Installation & Usage)

Follow these steps to get the chat application running perfectly on your local machine or across a network with friends.

### 1. Prerequisites
Before you begin, ensure you have the following installed on your computer:
*   **Python 3.x:** (Download from [python.org](https://www.python.org/))
*   **Required Libraries:** install those libraries in your python: vidstream, tkinter and threading (should already come in python by default, install if they arent.), socket.

### 2. Installation
Download all the files in this repository and put them all in one folder.

### 3. Usage
1. Run server.py in its own dedicated terminal, it should display "Listening on xxx.xxx.xxx.xxx (your IP address):5555"
2. Run Main.py (the client) in its own dedicated terminal or make someone else run it on their PC.
3. Enter the IP address the server gave you into its entry field on the screen ( delete the 127.0.0.1 and input your own server ip, leave the port as is). then enter your own username then click the "connect" button.
4. Repeat steps 2 and 3 for all other clients.
5. the chat will appear normally where you can send messages. and the call and end call buttons as well.
6. If you want to do a call, click on a user in the "active users" list and click the "start call" button.
7. a Pop up message will appear for the user who is being called asking them to accept or decline the call, if they accept you and them will be connected and be able to voice call with each other.
