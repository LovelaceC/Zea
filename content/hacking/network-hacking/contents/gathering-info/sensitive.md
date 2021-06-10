---
title: Gathering Sensitive Information About Connected Devices
type: default
layout: page
child: Cracking
fold: Network Cracking
---

Nmap is the second program that we are going to look. It is a huge tool and has
several uses. Nmap is used to gather information aboyt any device. Using Nmap,
we can gather information about any client that is within or outside our
network, and we can gather information about clients just by knowing their IP.
Nmap can be used to bypass firewalls, as well as all kinds of protections
and security measures. In this sections, we are going to learn some of the basic
Nmap commands that can be used to discover all clients that are connected to
our network, and also discover the open ports on these clients.

With Nmap we can also specify an IP range as a target, so let's execute a basic
Nmap scan against all my subnet.

The first Nmap scan we are going to execute is called "_Ping Scan_", this scan
will check if a client is alive, by specifying a subnet we can also map
our current network. To execute a ping scan using Nmap against my subnet, just
execute in a terminal:

```bash
jinx@system:~$ nmap -sn 192.168.1.1/24

Starting Nmap 7.70 ( https://nmap.org ) at 2021-02-27 18:45 GMT
Nmap scan report for 192.168.1.3
Host is up (0.086s latency).
MAC Address: B4:E6:2A:99:B7:A0 (LG Innotek)
Nmap scan report for 192.168.1.7
Host is up (0.030s latency).
MAC Address: D0:16:B4:58:72:FA (Unknown)
Nmap scan report for 192.168.1.12
Host is up (0.039s latency).
MAC Address: FE:5D:CD:9C:6D:44 (Unknown)
Nmap scan report for 192.168.1.252
Host is up (0.00030s latency).
MAC Address: 00:00:CA:01:02:03 (Arris Group)
Nmap scan report for 192.168.1.254
Host is up (0.0025s latency).
MAC Address: 9C:C8:FC:4D:10:CC (Unknown)
Nmap scan report for 192.168.1.4
Host is up.
Nmap done: 256 IP addresses (6 hosts up) scanned in 2.58 seconds
```

As you can see, Nmap returns to us all the connected clients, their MAC address,
their IP address and, potentially, their vendors.

The next scan we are going to learn is called "_Quick Scan_", this is slighlty
slower than the _Ping Scan_, but in Quick Scan, we will get more information
than the _Ping Scan_.

```bash
jinx@system:~$ nmap -F 192.168.1.1/24

Starting Nmap 7.70 ( https://nmap.org ) at 2021-02-27 18:47 GMT
Nmap scan report for 192.168.1.3
Host is up (0.0016s latency).
Not shown: 99 closed ports
PORT     STATE SERVICE
3000/tcp open  ppp
MAC Address: B4:E6:2A:99:B7:A0 (LG Innotek)

Nmap scan report for 192.168.1.6
Host is up (0.0036s latency).
All 100 scanned ports on 192.168.1.6 are closed
MAC Address: 80:58:F8:FF:30:5A (Motorola Mobility, a Lenovo Company)

Nmap scan report for 192.168.1.7
Host is up (0.0056s latency).
All 100 scanned ports on 192.168.1.7 are closed
MAC Address: D0:16:B4:58:72:FA (Unknown)

Nmap scan report for 192.168.1.12
Host is up (0.021s latency).
All 100 scanned ports on 192.168.1.12 are closed
MAC Address: FE:5D:CD:9C:6D:44 (Unknown)

Nmap scan report for 192.168.1.252
Host is up (0.00030s latency).
All 100 scanned ports on 192.168.1.252 are closed
MAC Address: 00:00:CA:01:02:03 (Arris Group)

Nmap scan report for 192.168.1.254
Host is up (0.0021s latency).
Not shown: 96 closed ports
PORT     STATE    SERVICE
80/tcp   open     http
443/tcp  open     https
5000/tcp open     upnp
8081/tcp filtered blackice-icecap
MAC Address: 9C:C8:FC:4D:10:CC (Unknown)

Nmap scan report for 192.168.1.4
Host is up (0.000040s latency).
Not shown: 99 closed ports
PORT   STATE SERVICE
80/tcp open  http

Nmap done: 256 IP addresses (7 hosts up) scanned in 22.15 seconds
```

As you can see, now Nmap shows to use the open ports on each one of the
discovered devices. My router has several open ports, 80, 443, 5000 and
8081 and also, there's a client (192.168.1.4) with an open port "80".

Now, let's take a look at the "_Quick Scan Plus_", which take the "_Quick Scan_"
one step further. It's going to be slower than the "_Quick Scan_", but it will
show us the programs that are running on the open ports and its operating
system.

```bash
jinx@system:~$ nmap -sV -O -F 192.168.1.1/24

Starting Nmap 7.70 ( https://nmap.org ) at 2021-02-27 18:51 GMT
Nmap scan report for 192.168.1.3
Host is up (0.0014s latency).
Not shown: 99 closed ports
PORT     STATE SERVICE VERSION
3000/tcp open  http    LG smart TV http service
MAC Address: B4:E6:2A:99:B7:A0 (LG Innotek)
Device type: general purpose
Running: Linux 3.X|4.X
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4
OS details: Linux 3.2 - 4.9
Network Distance: 1 hop

Nmap scan report for 192.168.1.6
Host is up (0.0038s latency).
All 100 scanned ports on 192.168.1.6 are closed
MAC Address: 80:58:F8:FF:30:5A (Motorola Mobility, a Lenovo Company)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop

Nmap scan report for 192.168.1.7
Host is up (0.033s latency).
All 100 scanned ports on 192.168.1.7 are closed
MAC Address: D0:16:B4:58:72:FA (Unknown)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop

Nmap scan report for 192.168.1.12
Host is up (0.032s latency).
All 100 scanned ports on 192.168.1.12 are closed
MAC Address: FE:5D:CD:9C:6D:44 (Unknown)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop

Nmap scan report for 192.168.1.252
Host is up (0.00030s latency).
All 100 scanned ports on 192.168.1.252 are closed
MAC Address: 00:00:CA:01:02:03 (Arris Group)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop

Nmap scan report for 192.168.1.254
Host is up (0.0021s latency).
Not shown: 96 closed ports
PORT     STATE    SERVICE         VERSION
80/tcp   open     http            lighttpd
443/tcp  open     ssl/http        lighttpd
5000/tcp open     upnp            MiniUPnP 1.9 (UPnP 1.1)
8081/tcp filtered blackice-icecap
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port5000-TCP:V=7.70%I=7%D=2/27%Time=603A94CF%P=x86_64-pc-linux-gnu%r(Ge
SF:nericLines,130,"\x20501\x20Not\x20Implemented\r\nContent-Type:\x20text/
SF:html\r\nConnection:\x20close\r\nContent-Length:\x20149\r\nServer:\x20Re
SF:dHatEnterpriseServer/6\.10\x20UPnP/1\.1\x20MiniUPnPd/1\.9\r\nExt:\r\n\r
SF:\n<HTML><HEAD><TITLE>501\x20Not\x20Implemented</TITLE></HEAD><BODY><H1>
SF:Not\x20Implemented</H1>The\x20HTTP\x20Method\x20is\x20not\x20implemente
SF:d\x20by\x20this\x20server\.</BODY></HTML>\r\n")%r(GetRequest,123,"HTTP/
SF:1\.0\x20404\x20Not\x20Found\r\nContent-Type:\x20text/html\r\nConnection
SF::\x20close\r\nContent-Length:\x20134\r\nServer:\x20RedHatEnterpriseServ
SF:er/6\.10\x20UPnP/1\.1\x20MiniUPnPd/1\.9\r\nExt:\r\n\r\n<HTML><HEAD><TIT
SF:LE>404\x20Not\x20Found</TITLE></HEAD><BODY><H1>Not\x20Found</H1>The\x20
SF:requested\x20URL\x20was\x20not\x20found\x20on\x20this\x20server\.</BODY
SF:></HTML>\r\n")%r(RTSPRequest,138,"RTSP/1\.0\x20501\x20Not\x20Implemente
SF:d\r\nContent-Type:\x20text/html\r\nConnection:\x20close\r\nContent-Leng
SF:th:\x20149\r\nServer:\x20RedHatEnterpriseServer/6\.10\x20UPnP/1\.1\x20M
SF:iniUPnPd/1\.9\r\nExt:\r\n\r\n<HTML><HEAD><TITLE>501\x20Not\x20Implement
SF:ed</TITLE></HEAD><BODY><H1>Not\x20Implemented</H1>The\x20HTTP\x20Method
SF:\x20is\x20not\x20implemented\x20by\x20this\x20server\.</BODY></HTML>\r\
SF:n")%r(HTTPOptions,138,"HTTP/1\.0\x20501\x20Not\x20Implemented\r\nConten
SF:t-Type:\x20text/html\r\nConnection:\x20close\r\nContent-Length:\x20149\
SF:r\nServer:\x20RedHatEnterpriseServer/6\.10\x20UPnP/1\.1\x20MiniUPnPd/1\
SF:.9\r\nExt:\r\n\r\n<HTML><HEAD><TITLE>501\x20Not\x20Implemented</TITLE><
SF:/HEAD><BODY><H1>Not\x20Implemented</H1>The\x20HTTP\x20Method\x20is\x20n
SF:ot\x20implemented\x20by\x20this\x20server\.</BODY></HTML>\r\n")%r(FourO
SF:hFourRequest,123,"HTTP/1\.0\x20404\x20Not\x20Found\r\nContent-Type:\x20
SF:text/html\r\nConnection:\x20close\r\nContent-Length:\x20134\r\nServer:\
SF:x20RedHatEnterpriseServer/6\.10\x20UPnP/1\.1\x20MiniUPnPd/1\.9\r\nExt:\
SF:r\n\r\n<HTML><HEAD><TITLE>404\x20Not\x20Found</TITLE></HEAD><BODY><H1>N
SF:ot\x20Found</H1>The\x20requested\x20URL\x20was\x20not\x20found\x20on\x2
SF:0this\x20server\.</BODY></HTML>\r\n");
MAC Address: 9C:C8:FC:4D:10:CC (Unknown)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.70%E=4%D=2/27%OT=80%CT=7%CU=40190%PV=Y%DS=1%DC=D%G=Y%M=9CC8FC%T
OS:M=603A9505%P=x86_64-pc-linux-gnu)SEQ(SP=CB%GCD=1%ISR=CB%TI=Z%CI=Z%TS=7)S
OS:EQ(SP=CB%GCD=1%ISR=CB%TI=Z%CI=Z%II=I%TS=7)OPS(O1=M5B4ST11NW3%O2=M5B4ST11
OS:NW3%O3=M5B4NNT11NW3%O4=M5B4ST11NW3%O5=M5B4ST11NW3%O6=M5B4ST11)WIN(W1=389
OS:0%W2=3890%W3=3890%W4=3890%W5=3890%W6=3890)ECN(R=Y%DF=Y%T=40%W=3908%O=M5B
OS:4NNSNW3%CC=N%Q=)T1(R=Y%DF=Y%T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=Y%DF=
OS:Y%T=40%W=3890%S=O%A=S+%F=AS%O=M5B4ST11NW3%RD=0%Q=)T4(R=Y%DF=Y%T=40%W=0%S
OS:=A%A=Z%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R
OS:=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=
OS:AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%
OS:RUD=G)IE(R=Y%DFI=N%T=40%CD=S)

Network Distance: 1 hop

Nmap scan report for 192.168.1.4
Host is up (0.000052s latency).
Not shown: 99 closed ports
PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.38 ((Debian))
Device type: general purpose
Running: Linux 2.6.X
OS CPE: cpe:/o:linux:linux_kernel:2.6.32
OS details: Linux 2.6.32
Network Distance: 0 hops

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 256 IP addresses (7 hosts up) scanned in 105.22 seconds
```

As you might remember, in the previous scan we saw that the client "192.168.1.4"
had an open port "80" but we didn't know what service was being executed on that
port, now we know that "192.168.1.4" is a device running linux and executing a
web server "Apache httpd 2.4.38".
