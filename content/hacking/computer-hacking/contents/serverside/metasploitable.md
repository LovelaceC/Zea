---
title: Installing Metasploitable
type: default
layout: page
child: Hacking
fold: Computer Hacking
---

In the next lessons, we are going to start talking about server-side attacks, we
are going to learn what a server is and we are going to talk about it in detail,
but before we jump into this, we need to have a computer or a machine that acts
as a server so that we can try to hack into it. Similar to the way that we had a
Windows machine to practise attacks that we can launch against normal users, we
need to have another virtual machine that behaves like a server, so that we can
practise server-side attacks against it, and see how we can hack into servers.

The machine that we are going to use is called Metasploitable and it's a virtual
machine that's built on Linux and it contains a few services that are typically
used by servers, it also contains several web applications that act like
normal websites and use the same technologies used by normal servers and normal
web applications.

We are going to install this machine and in the future, we are going to use it
as a target to learn how to hack into servers, and how to hack into websites.
You can download Metasploitable
[here](https://information.rapid7.com/metasploitable-download.html). Before
you can download Metasploitable you will have to fill your information in the
form, you can just make up names, take in account that you can't use average
"@gmail.com" addresses it will return an error saying something like "it must
be a valid company email", if you do not have a company you can use a fake
email in that field, all you have to do is write a name "at" ("@") and any
company name you want, for example, _jinxcgco@libreacademia.gq_. Once you
have filled up that form, you can click the "Download Metasploitable Now"
button and the Metasploitable download fill start.

Once it is downloaded, we are going to have a zip file, you will have to
uncompress it by executing:

```bash
unzip -q file.zip
```

For example:

```bash
unzip -q Metasploitable.zip
```

In that directory you will see a bunch of files, we are going to import it
into VirtualBox. To do so, let's open up virtual box, click the "New" button
on the top-left corner of the program, set it a name, "_Metasploitable_", for
example, in "Type" choose "Linux" and hit continue. When you get to the
RAM assignation section note that Metasploitable won't require that much
amount of RAM, so setting 768 megabytes should be enough. Then, we are going
to choose the option "Use an existing virtual hard disk file" and click
in the folder icon so you can look for the Metasploitable file in your computer.
Once the File chooser has prompt up, go to the Metasploitable directory and
select "Metasploitable.vmdk" then click Open and Create.

After you import the Virtual Hard Disk file into the newly created virtual
machine, we are ready to start Metasploitable, so you can now click the "Start"
button on the top bar and once it boots up, it will boot up as a normal
Linux installation would do and it will also ask you for credentials so you can
login into Metasploitable, both the default username and password for this
machine is "_msfadmin_".

