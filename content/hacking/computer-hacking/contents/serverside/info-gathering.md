---
title: Basic Information Gathering
type: default
layout: page
child: Cracking
fold: Computer Cracking
---

The first step into the server-side attacks is information gathering.

Information gathering is very important, because it will show us the operating
system of the target, the installed programs and the running services, the ports
associated with the services and so much more.

From the installed and running services on our target, we can try and get into
the system. We can do this by trying default passwords, for example, another
thing that we can do, is that, there are a lot of people that install services
and misconfigure them and we can abuse of it.

Sometimes, the services installed on a server, are aimed to let people to gain
remote access to that computer so that they can change things without the need
of being in front of that computer, those services obviously need to have some
security implementations and people often misconfigure these services, so we can
take advantage of these misconfigurations and gain access to these computers.

Another problem with these services, is that some of them might even have
backdoors and we will see an example of that, and a lot of them would have
some vulnerabilities such as remote buffer overflows or code execution
vulnerabilities that allow us to gain full access to that computer.

The simplest way of doing this, is by using a tool that we have already seen
before which is Nmap. We can use Nmap using the IP of our target, we get a list
of all the services that our target is running and then we will look in the
internet for each one of them and see if they contain any vulnerabilities.

We have seen how to use Nmap before, but I just want to convey the idea of that
anything is a computer, for example, Metasploitable is actually a Linux
distribution that contains and runs a web server, therefore, we can make use of
it as a website, if you want to get the IP address of an actual website, all you
have to do is just do a ping, for example, if we are targeting Facebook, all we
have to do is to execute:

```bash
ping facebook.com
```

And we'll get an output like:

```bash
PING  (69.171.250.35) 56(84) bytes of data.
64 bytes from edge-star-mini-shv-01-any2.facebook.com (69.171.250.35): icmp_seq=1 ttl=55 time=21.0 ms
64 bytes from edge-star-mini-shv-01-any2.facebook.com (69.171.250.35): icmp_seq=2 ttl=55 time=20.5 ms
64 bytes from edge-star-mini-shv-01-any2.facebook.com (69.171.250.35): icmp_seq=2 ttl=55 time=20.5 ms
64 bytes from edge-star-mini-shv-01-any2.facebook.com (69.171.250.35): icmp_seq=2 ttl=55 time=20.5 ms
64 bytes from edge-star-mini-shv-01-any2.facebook.com (69.171.250.35): icmp_seq=2 ttl=55 time=20.5 ms
```

And you can see that the Facebook's IP address is 69.171.250.35 and now we will
be able to run Nmap against it and gain a list of all the running services on
Facebook. Obviously, we are not going to do that, as we are not allowed to do
so, what we are going to do, is to execute Nmap against our Metasploitable
machine.

We are going to run Nmap as we have been doing it so far, we are going to
execute an Agressive scan against our target. So we are going to execute:

```bash
nmap -A -v [IpOfYourTarget]
```

With that command we will run a verbose agressive scan using nmap, all we have
left to do is to replace "[IpOfYourTarget]" with the IP address of our
Metasploitable machine, which in my case is "192.168.1.12" so the final command
would look like the following:

```bash
nmap -A 192.168.1.12
```

Once the scan has finished you will see a lot of open ports, a lot of services.
What I advise you to do is to, literally, go port by port reading what it is and
searching on the internet the name of the program they are running.

For example, we have the port 21 open in our Metasploitable machine, that's an
FTP port. FTP is a service that allows people to upload or download files from
the server remotely.

Usually, FTP services use a username and a password but you can see that, nmap
tells us that the installed FTP server (_vsftpd 2.3.4_) has been misconfigured
and it allows anonymous FTP login, that means, that you will be able to log in
without a password, all you have to do is to download an FTP client (or use
`ftp` on Linux) and you will be able to connect using the Metasploitable's IP
and the port 21. I am not going to explain this, because it is very simple, you
just have to - literally - download the application and connect to it.

What else you can do, is search the name of the service in the
internet and see if it has any issues, if it has any misconfigurations, if it
has any known code execution exploits. I know that if you search the name of
the ftp service of Metasploitable on the internet, you will find out that it has
a backdoor installed, it literally came with a backdoor when it was released.

For now, I would like to show you something simpler as we are just beginning
with this section. As I said, you need to go one by one searching the services
and checking if they have any misconfigurations or any known exploits.

What I am going to do, is look the port _512_. Let's assume that we went on them
one by one, we couldn't find anything and we reach the 512 TCP port, we are
going to copy the name of the service running on this port (_netkit-rsh rexecd_)
. So literally, I don't know what is this so I am going to copy it and search
for this on the internet.

We are going to have a look on the first result that we'd usually got when we
search for this ([this page](http://t2sde.org/packages/netkit-rsh)).

Once we open that page, if we read a little we will be able to see that the 
service running on port 512 is a remote execution program, that means that, if 
we manage to log in through this service, we will be able to execute commands on 
the target computer and it uses the RSH rlogin, that's a program that ships with
Linux that allows you, similar to SSH, to execute remote commands on the target
computer.

Let's go one page back and let's see how we can connect to this, first, let's 
see what comes into the _netkit-rsh_ packet, to know what it comes with, let's
search for that name _netkit-rsh_.

The first result that we'd usually get is a page from Ubuntu, and as we know, 
Metasploitable is based on Ubuntu, so let's open
[this page](https://packages.ubuntu.com/source/xenial/netkit-rsh).

In that page, you'd be able to see that the service we are targetting right now 
uses a package called _rsh-client_ to connect, so that is the package that you 
need to install to connect to this service.

So now let's go to our pentesting distribution and let's install _rsh-client_. 
In case you are using a distribution based on Debian, you'd run the following 
command:

```bash
sudo apt-get install rsh-client
```

Once it is installed, we are going to use the program `rlogin` to login into 
this service, because remember that the first page told us that it uses the
rlogin program to facilitate login process.

So let's execute _rlogin_, but as we don't know how to use this program, we will
run first _rlogin --help_ to see how we can use it.

```bash
$ rlogin --help
Usage: rlogin [OPTION...] HOST
Starts a terminal session on a remote host.

  -4, --ipv4                 use only IPv4
  -6, --ipv6                 use only IPv6
  -8, --8-bit                allows an eight-bit input data path at all times
  -d, --debug                set the SO_DEBUG option
  -e, --escape=CHAR          allows user specification of the escape character,
                             which is ``~'' by default
  -E, --no-escape            stops any character from being recognized as an
                             escape character
  -l, --user=USER            run as USER on the remote system
  -?, --help                 give this help list
      --usage                give a short usage message
  -V, --version              print program version

Mandatory or optional arguments to long options are also mandatory or optional
for any corresponding short options.

Report bugs to <bug-inetutils@gnu.org>.
```

You can see that by using the argument _-l_ we can specify a username and that 
without the need of specifying an argument, we can set the host we want to 
connect to which is our target IP address.

So we are going to execute:

```bash
rlogin -l root 192.168.1.12
```

So we can try to access to our Metasploitable device as root, take in account 
that _root_ represents the user with the most privileges on the system. Once we 
execute that command, we now will be login in the Metasploitable device, so we 
can now execute commands with root access.
