# Enumerating SMB
> Raj Pastagiya | 05/11/2023

## SMB Enumeration Tools and Techniques
- Typically, there are SMB share drives on a server that can be connected to and used to view or transfer files.

#### Port Scanning
- Use Nmap to scan for open ports. If SMB/samba is running then TCP 139/445 ports will be open.
	- Although it is surely possible that other than 139/445 ports are open serving for SMB/samba.
	- Here 139 port is NetBios (NBT over IP) and 445 port is SMB over IP. Both the ports can be actively used for the same purpose (Enumerating SMB).

#### SMB Enumeration Tool: Enum4Linux
- Enum4Linux is basically a wrapper around the tools in the Samba package and makes it easy to quickly extract information from the target pertaining to SMB.
- The syntax of Enum4Linux is nice and simple: **"enum4linux \[options] ip"**

|**TAG**|**FUNCTION**|
|----|---|
|-U|get userlist|  
|-M|get machine list|  
|-N|get namelist dump (different from -U and-M)|
|-S|get sharelist|  
|-P|get password policy information|  
|-G|get group and member list|
|-a|all of the above (full basic enumeration)|

# Quiz Section
- Conduct an **nmap** scan of your choosing, How many ports are open?
> **Answer:** 3
> **Command to Run:** `nmap -p- --min-rate=10000 $ip`


```nmap log
Host is up (0.15s latency).
Not shown: 65532 closed tcp ports (reset)
PORT    STATE SERVICE
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 11.73 seconds
```

- What ports is **SMB** running on?
> 139/445

- Let's get started with Enum4Linux, conduct a full basic enumeration. For starters, what is the **workgroup** name?
> **Answer:** workgroup
> **Command to Run: ** `enum4linux -a $ip`

- What comes up as the **name** of the machine?
> **Answer:** polosmb

- What operating system **version** is running?
> **Answer:** 6.1

- What share sticks out as something we might want to investigate?
> **Answer:** profiles