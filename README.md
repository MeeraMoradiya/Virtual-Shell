# Virtual-Shell
Client runs command that actually executes on server and response is sent back. Multiple clients can run at the same time

## Description

The server process and the client process will run on two different machines and the communi-
cation between the two processes is achieved using Sockets.

The server task can be summarized as follows :
• The server must start running before any client, and wait for connections.
• When the server gets a client, forks and, let the child process take care of the client in
a separate function, called serviceClient, while the parent process goes back to wait for
the next client. In particular, the server is capable to service multiple clients at the same
time.

• Then, the server’s child process
1. uses "dup2()" to swap screen for socket
2. gets in an infinite loop then :
– reads a shell command-line (ended by new line) from client,
– if the client has closed its sockets then, the server’s child quits.
– otherwise, it assembles the command and its arguments before excuting it using
exec() system call,

The client process connects to the server, then </br>
• gets into an infinite loops
1. reads a command-line from keyboard,
2. if command is "quit", closes socket and quits
3. otherwise, send command-line to server,
4. Then, reads command output from socket and displays them on the screen

## How to Run 
1. Open terminal and run below command in bash shell
~~~
sh m_server.c
~~~

2. Open other terminal with bash shell and run below command
~~~
sh client4.c
~~~

3. Now type command and press enter.This command will be executed on server and output will be shown in client shell. Type 'quit' to turn off client

