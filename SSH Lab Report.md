# Accessing A Remote Computer via SSH

Many CSE courses use course-specific accounts to log on to remote computers where students 
can remotely run code and do other tasks. There are several steps needed to be completed beforehand
for this to work.

## Installing VSCode (Visual Studio Code)

Visual Studio Code is an IDE (Integrated Development Environment) that in a nutshell allow you to write, compile, run, and debug your code alongside a vast array of other features. 
I personally prefer to use IntelliJ Idea (which I'm using to write this right now), but you can use any other IDE that allows terminal and remote access. Both IntelliJ and VSCode have a similar way of connecting via SSH using the terminal.

You can get VSCode from the website here: https://code.visualstudio.com/

When you are finished installing VSCode, you should be able to see a window similar to this when you open it.

![VSCode Welcome](/ssh_lab_report_resources/VSCode%20Welcome%20Window.png)

## Remotely Connecting

Now that we have an IDE (VSCode) ready to go, the next step is making sure we have OpenSSH installed on our personal computer. OpenSSH
is a remote administration protocol that allows users to access and modify their remote servers. For us, we'll be connecting to the `ieng6` account that many CSE students have access to based on their course.

To download OpenSSH: [Click Here :)](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse)

The next step is to look up your course-specific account for CSE15L using the link below:

https://sdacs.ucsd.edu/~icc/index.php

Once you retrieve your account, open up a terminal in VSCode by clicking on the `Terminal` option in the top-left tool-bar:

![VSCode Terminal Option](/ssh_lab_report_resources/VSCode%20Terminal%20Option.png)

Your terminal will look something like this:

![VSCode Terminal](/ssh_lab_report_resources/VSCode%20Terminal.png)

In your terminal, you will type out `ssh cs15lwi22apd@ieng6.ucsd.edu` with the thre letters after 22 replaced by the letters in your course-specific account. The first time you connect to the account, you will get a message body like this:

> The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 

There is nothing to worry about here unless you encounter this message when you are connecting to a server you often connect to which could indicate that someone else is trying to listen in the connection or manipulate it.

So, type yes and hit enter. It will then ask you for your password. The whole process should look something like this after you enter your password:

![Connected to ieng6 account](/ssh_lab_report_resources/Post%20Password.png)

There you have it! You are now officially connected to a computer in the CSE basement that will run any commands you run in your terminal.

## Trying Some Commands