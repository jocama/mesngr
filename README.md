# mesngr
The goal of this project is to create a secure shell messanging app. Developers should use wolfssl to secure the connection (https://github.com/wolfSSL/wolfssl/).

## Requirements
The following are customer requirements for the sucessful implementation of mesngr. Like most customer requirements, some of them may seem a bit strange. While it's not a good project management policy, in this case, the customer is always right.
### Base
1. mesngr should consist of a client application and a server application
2. the target system is Ubuntu 14.04.5 Trusty Tahr
3. the application should be delivered in a tarball or a branch of this repo
4. mesngr must use wolfssl to secure the connection (https://github.com/wolfSSL/wolfssl/). See examples @ https://github.com/wolfSSL/wolfssl/tree/master/examples for more details on how to secure the connection with wolfssl. Your application can use TCP, SCTP, or even UDP. 
5. while wolfSSL does have python and Java usage layers, PLEASE use c or c++. Do not use Java or python.
### Server
The server useage should be similar to: ./mesngr_svr port
5. mesngr server should be able to accept and service multiple connections simultaneously
6. mesngr server must use a self signed certificate of at least 2048bits
7. mesngr server should run on a port specified in the command line
8. mesngr server must keep track of active (connected) users, though it does not need to persist users past a connection
9. mesngr server is not required to log anything. Preferably, errors would be written to a log or the console, though.
### Client
The client usage should be similar to: ./mesngr userid server port
10. mesngr users should be able to specify their userid. If the userid is currently in use, the server should respond with a connection error.
11. mesngr users should be able to specify the server (ip or name) and port where the server is running via the command line.

## Usage Scenarios
### Ideal Case
