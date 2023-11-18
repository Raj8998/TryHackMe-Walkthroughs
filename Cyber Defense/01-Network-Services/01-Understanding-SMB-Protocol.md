# Understanding SMB Protocol
> Raj Pastagiya | 05/11/2023

### What is SMB?
- SMB - Server Message Block Protocol - is a client-server communication protocol used for sharing access to files, printers, serial ports and other resources on a network.
- Servers make file systems and other resources (printers, named pipes, APIs) available to clients on the network. Client computers may have their own hard disks, but they also want access to the shared file systems and printers on the servers.
- The SMB protocol is known as a response-request protocol, meaning that it transmits multiple messages between the client and server to establish a connection. Clients connect to servers using TCP/IP (actually NetBIOS over TCP/IP as specified in RFC1001 and RFC1002), NetBEUI or IPX/SPX.

### What runs SMB?
- Microsoft Windows operating systems since Windows 95 have included client and server SMB protocol support. Samba, an open source server that supports the SMB protocol, was released for Unix systems.

# Quiz Section

- What does SMB stand for?
> Server Message Block


- What type of protocol is SMB?
> Response-request


- What do clients connect to servers using?
> TCP/IP


- What systems does Samba run on?
> Unix