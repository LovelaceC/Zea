---
title: Hacking a Remote Server Using a Basic Metasploit Exploit
type: default
layout: page
---

# Hacking a Remote Server Using a Basic Metasploit Exploit

So far we have seen how to gain access through a misconfigured service to a
remote server. Today, we are going to have an example on a very simple thing,
which is a backdoor.

Some programs or services were shipped or come in with backdoors embedded in
them, we are going to exploit that today and I chose a very basic exploit,
because I want to introduce you to a framework called Metasploit. We are going
to be using that framework a lot, so I wanted something simple to start with and
then, we are going to go deeper into that framework.

First, let me show you how we find that exploit. Again, using the same method
that we have always been using, I performed a scan with Nmap and as said in the
previous lesson, we are going to go on each port and search for them, looking
for exploits or possible misconfigurations.

So, let's search for the first service that Nmap shows to us in the Nmap scan
which is "vsftpd 2.3.4"on the port number 21, let's open up a browser and let's
search for that name followed by the word "exploit", the final term would look
like this: "_vsftpd 2.3.4 exploit_".

As you can see, the first result comes from a website called "Rapid7". Rapid7 is
the company that makes the Metasploit framework, so, let's open up this result
and as you can see, Rapid7 is telling us that this version of vsftpd has a
backdoor command execution, so it allows us, to execute commands on the target
computer that has this service installed, and by using NMap, we discovered that
this program is installed in our Metasploitable machine, that means, that we can
execute commands on the target machine.

Let's talk a little about Metasploit before continuing. Metasploit, as I
mentioned before, is made by Rapid7, it is a huge framework and contains several
exploits, so it allows you to exploit vulnerabilities or even create your own
exploits if you are an expert and you know how to discover and make exploits,
then Metasploit will help you to do that.

For this lesson, we are doing a very simple use of an existing vulnerability.

The commands in Metasploit are very easy:

- **msfconsole** - runs the metasploit framework
- **help** - shows help
- **show [something]** - _something_ can be exploits, payloads, auxiliaries or options
- **use [something]** - use a certain exploit, payload or auxiliary
- **set [option] [value]** - configure [option] to have a value of [value]
- **exploit** - runs the current task/exploit

They might seem a little complicated now, but once you get into it, it becomes
very easy to use and a lot of them are generic commands. I just showed you the
basic and generic commands of Metasploit and then, there are other commands that
you will get used to them in time.

The first command I showed you is **msfconsole** and this basically just
launches the Metasploit program, you can always type **help** at any stage,
and you will get help of the commands and the description on how you can use
them. You can use the **show** command to show something, you can show the
available exploits, you can show the available auxiliaries, the available
payloads, and we will talk about what each one of these mean in the future. You
can use the **use** command to use something that you were shown, for example,
you showed the exploits and you picked a certain exploit that you want to use,
then you use the **use** command and then, you type in the exploit name to run
it. Then, you can use the **set** option, or the **set** command, to set
specific options for the exploit, for example, if you wanted to set the IP
address of your target, you set the IP address by using this command and then
at the end, once you finish configuring your exploit, you can type in exploit
to execute that exploit.

I know this might look a bit vague, but once we use it, it is going to become
very clear to you and we are going to be using these programs and these commands
a lot, so they are going to become very easy and simple to use.

So now, let's keep going at exploiting our Metasploitable machine, let's recap,
we performed a Nmap scan, we looked up for the name of a service and the first
thing that came up is that this service has a backdoor command execution.
Because this is on the Rapid7's website, the vulnerability is exploitable using
Metasploit and the module name that we are going to be using in this lesson is
the one shown in the Rapid7's website, which is
_exploit/unix/ftp/vsftpd_234_backdoor, it made our lives much easier by
providing it on the website, let's copy that name as we are going to use it to
exploit this vulnerability.

Now, let's open up a console and type `msfconsole` and now we are going to do a
**use** and then, put the name of the exploit that we just copied from the
Rapid7's website, so, we are going to use that certain exploit and as you can
see, the name of the "msf >" that appeared when we opened the metasploit console
has changed to "msf exploit(vsftpd_234_backdoor) >".

Now, we are going to use the **show** command to show the options that we need
to set, to do that, we will need to execute:

```bash
show options
```

As I mentioned before, show is a generic command that you can use in a number of
cases, in this case, we are going to show the available options that we can set
for the exploit we chose and we are now using. We'd get an output like the
following:

```bash
Module options (exploit/unix/ftp/vsftpd_234_backdoor):

  Name   Current Setting  Required  Description
  ----   ---------------  --------  -----------
  RHOST                   yes       The target address
  RPORT  21               yes       The target port

Exploit target:

  Id  Name
  --  ----
  0   Automatic
```

As you can see now, the second option is the port that the service is running on
and it's already set to port 21, and this is correct if we go back to Nmap, you
will see that our target's FTP server is running on port 21, so we don't need to
change any of that.

What we need to change is the RHOST, the RHOST is the target IP address, as you
can see under the section "Description", to change the value of that, as I
explained before, we are going to use the **set** command. So, our final command
will be:

```bash
set RHOST [TargetIPAddress]
```

By executing that command we are setting the value of RHOST to
"[TargetIPAddress]" in my case, I'd like to set the value of RHOST to
_192.168.1.12_, so my final command would look like this:

```bash
set RHOST 192.168.1.12
```

We are using _set_ and after _set_, we specify the option name, for example, if
you wanted to change the port, you'd specify as option name _RPORT_ instead of
_RHOST_, but as we are changing the host, we are changing the value of the
option _RHOST_.

What I want to do is to see the options of this exploit again, just to make sure
that the value of _RHOST_ has changed.

```bash
msf exploit (vsftpd_234_backdoor) > show options

Module options (exploit/unix/ftp/vsftpd_234_backdoor):

  Name   Current Setting  Required  Description
  ----   ---------------  --------  -----------
  RHOST  192.168.1.12     yes       The target address
  RPORT  21               yes       The target port

Exploit target:

  Id  Name
  --  ----
  0   Automatic
```

And as you can see now, the RHOST value has been changed, everthing is ready now
to execute this exploit, to do so, remember, all you have to do is to execute
**exploit**.

Once you execute that, you'll probably get an output like the following:

```bash
[*] 192.168.1.12:21 - Banner: 220 (vsFTPd 2.3.4)
[*] 192.168.1.12:21 - USER: 331 PLease specify the password.
[*] Exploit completed, but no session was created.
```

It seems like the exploit ran, but nothing has happened, we didn't gain
anything, so what we have to do is to run it again and now, you'll have
root access to the target computer.
