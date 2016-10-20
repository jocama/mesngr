# mesngr
The goal of this project is to create a secure shell messanging app. Developers should use wolfssl to secure the connection (https://github.com/wolfSSL/wolfssl/).

## Requirements
The following are customer requirements for the sucessful implementation of mesngr. Like most customer requirements, some of them may seem a bit strange. While it's not a good project management policy, in this case, the customer is always right.

### Base
<ol start="1">
<li>mesngr should consist of a client application and a server application</li>
<li>the target system is Ubuntu 14.04.5 Trusty Tahr</li>
<li>the application should be delivered in a tarball or a branch of this repo</li>
<li>mesngr must use wolfssl to secure the connection (https://github.com/wolfSSL/wolfssl/). See examples @ https://github.com/wolfSSL/wolfssl/tree/master/examples for more details on how to secure the connection with wolfssl. Your application can use TCP, SCTP, or even UDP.</li>
<li>while wolfSSL does have python and Java usage layers, PLEASE use c or c++. Do not use Java or python.</li>
</ol>
### Server
The server useage should be similar to: `./mesngr_svr port`
<ol start="6">
<li>mesngr server should be able to accept and service multiple connections simultaneously</li>
<li>mesngr server must use a self signed certificate of at least 2048bits</li>
<li>mesngr server should run on a port specified in the command line</li>
<li>mesngr server must keep track of active (connected) users, though it does not need to persist users past a connection</li>
<li>mesngr server is not required to log anything. Preferably, errors would be written to a log or the console, though.</li>
</ol>
### Client
The client usage should be similar to: `./mesngr userid server port`
<ol>
<li>mesngr users should be able to specify their userid. If the userid is currently in use, the server should respond with a connection error.</li>
<li>mesngr users should be able to specify the server (ip or name) and port where the server is running via the command line.</li>
<li>mesngr users should be able to invite other users to chat with by entering an id (something like chat user1). If the messaged user is not in another conversation and accepts the invite. The two users enter into a private chat, which cannot be interrupted until one user enters quit.</li>
</ol>

## Usage Scenarios
### Ideal Case
Start the server (`./mesngr_svr 8443`)  
Start a client (assuming localhost: `./mesngr user1 localhost 8443`)  
Start another client (assuming localhost: `./mesngr user2 localhost 8443`)  
Enter `chat user1` on client2  
On client1: "chat with user2?" enter `y`  
Send messages back and forth  
Start a 3rd client  
On client3 enter `chat user2` -- should display "user2 is busy. try again later"  
On client1 enter quit.  
On client3 enter `chat user2`  
On client2 display: "chat with user1?" enter `y`   
test messaging  
Quit client 2 and 3  
