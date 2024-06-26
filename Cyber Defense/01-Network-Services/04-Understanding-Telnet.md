# Understanding Telnet
> Raj Pastagiya | 05/11/2023

### What is Telnet?
- Telnet is an application protocol which allows you, with the use of a telnet client, to connect to and execute commands on a remote machine that's hosting a telnet server.  
- The telnet client will establish a connection with the server. The client will then become a virtual terminal- allowing you to interact with the remote host.  

### Replacement  
- Telnet sends all messages in clear text and has no specific security mechanisms. Thus, in many applications and services, Telnet has been replaced by SSH in most implementations.  
   
### How does Telnet work?
- The user connects to the server by using the Telnet protocol, which means entering **"telnet"** into a command prompt. The user then executes commands on the server by using specific Telnet commands in the Telnet prompt. You can connect to a telnet server with the following syntax: **"telnet \[ip] \[port]"

# Quiz Section
- What is Telnet
> **Answer:** application protocol

- What has slowly replaced Telnet?
> **Answer:** SSH

- How would you connect to a Telnet server with the IP 10.10.10.3 on port 23?
> **Answer:** telnet 10.10.10.3 23

- The lack of what, means that all Telnet communication is in plaintext?
> **Answer:** encryption