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

In your terminal, you will type out `ssh cs15lwi22apd@ieng6.ucsd.edu` with the three letters after 22 replaced by the letters in your course-specific account, and press enter. The first time you connect to the account, you will get a message body like this:

> The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 

There is nothing to worry about here unless you encounter this message when you are connecting to a server you often connect to which could indicate that someone else is trying to listen in the connection or manipulate it.

So, type yes and hit enter. It will then ask you for your password. The whole process should look something like this after you enter your password:

![Connected to ieng6 account](/ssh_lab_report_resources/Post%20Password.png)

There you have it! You are now officially connected to a computer that will run any commands you run in your terminal.

## Trying Some Commands

There are many commands you can run, but for now we will take a look at a select few and try them out.

### `cd ~`

cd stands for "Change Directory" so any time you want to change a directory you type `cd <directory>`, replacing <directory> with the name of the dir you want to navigate to on the current disk.

In the image below I am in a test folder I created using the `mkdir` command.

![Home Dir Command](/ssh_lab_report_resources/home_dir_cmd.png)

As you can see, typing the `~` (tilde) symbol after cd will take me back to the home directory.

### `cd`

![Home Dir Using cd](/ssh_lab_report_resources/home_dir_using_cd.png)

Another thing to note is that you can also navigate back to the home directory by just typing and entering in `cd`

### `ls -lat`

The `ls` command lists all files and directories on the disk. With the `-lat` argument, it displays extra information regarding each file and folder such as the date and time of creation, the account associated, etc.

`ls` command:

![LS Command](/ssh_lab_report_resources/ls_command.png)

vs

`ls -lat` command:

![LS Lat Command](/ssh_lab_report_resources/ls_lat_command.png)

### `ls <directory>`

`ls` with this command argument will list all the files and folders present in the directory you mention

![LS Dir Command](/ssh_lab_report_resources/ls_dir_command.png)

### `cp`

The `cp` command will copy files/folders from one place to another. It has three arguments: `[options] [source] [destination]` where `[source]` is the source path of the file/folder and `[destination]` is the source path the file/folder will be copied to. 

### `cat [file]`

The `cat` command is used to display the contents of a file and also can be used to create a new file by merging multiple files. 


A list of some basic ssh commands can be found here: [Basic SSH Commands](https://www.hostinger.com/tutorials/ssh/basic-ssh-commands)

## Moving Files with `scp`

Let's say we want to move a file or files from our personal computer (client) to the remote computer (server). To do this we can use the `scp` command.

For example, let's create a `.java` file called TestClass with this code, on our own computer in the IDE (Make sure you are on your own client! You can return to your client by entering in `exit`), that we want to execute remotely:

```
public class TestClass {
    public static void main(String[] args) {
        System.out.println("I don't like being moved around you know..");
    }
}
```

You compile the code first by typing `javac TestClass.java` in the terminal and then run it by typing `java TestClass`.

Now, to move the file to our server we in our terminal and from the directory where the file was created we type this command (remembering to use your own username as usual):

`scp TestClass.java cs15lwi22zz@ieng6.ucsd.edu:~/`

You will be again prompted with a password like the time when you logged in. You can then log in to the server and use the `ls` command and will see the file now being there which you can now run using `javac` and `java` as java is installed on the server. 

![SCP Command](/ssh_lab_report_resources/scp_command.png)

We will look at ssh keys in the next part as seen from the image above where I have a key setup

## Setting an SSH Key

As you might have noticed so far, every time we want to perform operations on the server using `scp` we have to either always type or copy-paste our password to gain access. `ssh keys` help avoid this time-consuming and frustrating task by creating two files called the "public key" and the "private key" using the `ssh-keygen` command. The public key can be copied to a place on the server whereas the private key will 
be stored somewhere on the client. The ssh command will then use the key in place of your password automatically, saving you time, unless you decide to create a catchphrase for further protection measures.

Here is what you should type and enter on your side:

![SSH Keygen](/ssh_lab_report_resources/SSH%20Keygen.png)

With the name after `/User/` being the name of your computer that is.

## Optimizing Remote Running

You can run commands on the server without having to log in every time using the `ssh` command.

For example:

`ssh cs15lwi22apd@ieng6.ucsd.edu 'ls test_folder'` will directly run the ls command on the server and print the result on our client. 

You can do this with multiple commands and files that you want to compile and execute by joining together multiple arugments using
semi-colons to seperate them