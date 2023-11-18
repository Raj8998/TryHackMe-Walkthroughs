# FTP
> Raj Pastagiya | 18/11/2023

### **What is FTP?**
File Transfer Protocol (FTP) is, as the name suggests , a protocol used to allow remote transfer of files over a network. It uses a client-server model to do this, and- as we'll come on to later- relays commands and data in a very efficient way.

### ****How does FTP work?****
- A typical FTP session operates using two channels:
	- a command (sometimes called the control) channel
	- a data channel.
- As their names imply, the command channel is used for transmitting commands as well as replies to those commands, while the data channel is used for transferring data.
- FTP operates using a client-server protocol. The client initiates a connection with the server, the server validates whatever login credentials are provided and then opens the session.
- While the session is open, the client may execute FTP commands on the server.  

### **Active vs Passive**
- The FTP server may support either Active or Passive connections, or both. 
	- In an Active FTP connection, the client opens a port and listens. The server is required to actively connect to it. 
	- In a Passive FTP connection, the server opens a port and listens (passively) and the client connects to it. 
- This separation of command information and data into separate channels is a way of being able to send commands to the server without having to wait for the current data transfer to finish. If both channels were interlinked, you could only enter commands in between data transfers, which wouldn't be efficient for either large file transfers, or slow internet connections.

# Quiz Section \[Understanding FTP]
- What communications model does FTP use?
> client-server

- What's the standard FTP port?
> 21

- How many modes of FTP connection are there?
> 2

# Quiz Section \[Enumerating FTP]
- How many **ports** are open on the target machine?
> 2

- What **port** is ftp running on?
> 21

- What **variant** of FTP is running on it?
> vsftpd

- Great, now we know what type of FTP server we're dealing with we can check to see if we are able to login anonymously to the FTP server. We can do this using by typing "_ftp [IP]_" into the console, and entering "anonymous", and no password when prompted.
	- What is the name of the file in the anonymous FTP directory?
> PUBLIC_NOTICE.txt

- What do we think a possible username could be?
> mike


# Exploiting FTP
- **Types of FTP Exploit**
	- Similarly to Telnet, when using FTP both the command and data channels are unencrypted. Any data sent over these channels can be intercepted and read.
	- With data from FTP being sent in plaintext, if a man-in-the-middle attack took place an attacker could reveal anything sent through this protocol (such as passwords). An article written by [JSCape](https://www.jscape.com/blog/bid/91906/Countering-Packet-Sniffers-Using-Encrypted-FTP) demonstrates and explains this process using ARP-Poisoning to trick a victim into sending sensitive information to an attacker, rather than a legitimate source.
	- When looking at an FTP server from the position we find ourselves in for this machine, an avenue we can exploit is weak or default password configurations.  
- **Method Breakdown**
	- So, from our enumeration stage, we know:
		- There is an FTP server running on this machine  
		- We have a possible username  
	- Using this information, let's try and **bruteforce** the password of the FTP Server.
- **Hydra**
	- Hydra is a very fast online password cracking tool, which can perform rapid dictionary attacks against more than 50 Protocols, including Telnet, RDP, SSH, FTP, HTTP, HTTPS, SMB, several databases and much more. Hydra comes by default on both Parrot and Kali, however if you need it, you can find the GitHub [here](https://github.com/vanhauser-thc/thc-hydra).  
	- The syntax for the command we're going to use to find the passwords is this:
		- **"hydra -t 4 -l dale -P /usr/share/wordlists/rockyou.txt -vV 10.10.10.6 ftp"**

# Quiz Section \[Exploiting FTP]
- What is the password for the user "mike"?
> pasword

- What is ftp.txt?
> THM{y0u_g0t_th3_ftp_fl4g} 