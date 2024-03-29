---
title: Creating a Wordlist
type: default
layout: page
child: Cracking
fold: Network Cracking
---

From the previous lessons, we learn that when it comes to WPA and WPA2 the only
packets that contain some information that can help us with cracking with key
are the handshake packets and in the previous lesson, we learned how to capture
the handshake and store it in a file.

The handshake doesn't contain any information that can help us to recover or
recalculate the WPA key, the information in it can only be used to check whether
a password is valid or not, therefore, what we are going to do is to create a
wordlist, which is basically a big text file that contains a large number of
passwords, then, go through the passwords one by one and use then with the
handshake in order to check whether this password is valid or not. You can
download ready wordlists from the internet, but in this lesson I am going to
show you how to create your own wordlists, and in the next lesson I am going to
explain you how to use the wordlists and the handshake in order to recover the
password.

We are going to use a tool called _Crunch_. This is really handy skill to have
under your belt if you want to be a hacker/penetration tester because you are
going to face a lot of scenarios where a wordlist attack can become very handy.

Using _Crunch_ is very simple, all you have to do is to put the name of the
tool, specify the minimum and maximum number of characters for the passwords to
be generated, then you specify the characters that you want to generate
passwords from, for example, you can put all lowercase characters, all
uppercase, you can put numbers, digits, etcetera, you can also use the
argument_-t_ to give a pattern, for example, let's suppose you are looking at
the person while they are typing their password, and you seen that the password
start with an A, so you can tell crunch that the password starts with an A and
then give me all possible combination of paswords that start with an A and
finally, we use the _-o_ argument to specify the file name where the passwords
are going to be stored. Example:

```bash
crunch 6 8 123abc$ -o wordlist -t a@@@@b
```

The example above would generate a list of passwords that start from six
characters to eight characters and contain the characters _123abc$_, so it's
basically going to create combinations of 123abc$, it is going to store the
generated passwords in a file called wordlist and these passwords will start
with an "a" and finish with a "b".

Now, let's create an actual wordlist.

Let's fire up a terminal and execute _crunch_, I want to generate passwords of a
minimum of 6 characters and a maximum of 8, I also want it to contain
combinations of abc12 (note that you can specify the combinations of what you
want, character - _+-\/_ - uppercase and lowercase letter -_aBCqDgh_), I want to
store the generated wordlist in a file called _test.txt_. The entire command
looks like this:

```bash
crunch 6 8 abc12 -o test.txt
```

Remember:

```bash
crunch [MinimumLengthOfThePassword] [MaximumLengthOfThePasswords] [CharactersWeWantPasswordsToContain] -o [FileToStoreWordlistsIn]
```

Crunch returned us the following output:

```bash
Crunch will now generate the following amount of data: 4250000 bytes
4 MB
0 GB
0 TB
0 PB
Crunch will now generate the following number of lines: 484375

crunch: 100% completed generating output
```

As you can see, crunch generated 448000 passwords, it is a 4 MB worth file and
it is store in a file called _test.txt_. Now, let's create another wordlist
using a pattern, for that I will copy the command we entered before:

```bash
crunch 6 8 abc12 -o test.txt
```

I will change its maximum size to 6 (so every password will be only six
characters) and we are going to append the _-t_ option to specify a pattern, I
will tell it that I want the passwords to always start with an a and end with a
b.

```bash
crunch 6 6 abc12 -o test.txt -t a@@@@b
```

And I get the following output:

```bash
Crunch will now generate the following amount of data: 4375 bytes
0 MB
0 GB
0 TB
0 PB
Crunch will now generate the following number of lines: 625 

crunch: 100% completed generating output
```

As you can see now, the number of generated password is much less, it's only
625, because we've narrowed down the possibilities of passwords.

Now, I recommend you to read the manual of _crunch_ to see all the available
options to create much more advanced wordlists.
