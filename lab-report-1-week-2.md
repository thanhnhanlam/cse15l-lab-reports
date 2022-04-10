# Week 2 Lab Report

## Logging into a course-specific account on `ieng6`

In this tutorial, you will learn how to log into a course-specific account on `ieng6`.

### 1. Installing VSCode

Go to https://code.visualstudio.com/Download. Click on the button corresponding to your operating system (macOC, Windows, or Linux) to download Visual Studio Code: 

![VSCode Download Webpage][VSCode Download Webpage]

Follow the instructions to install VSCode. Once installed, opening VSCode should look like this (yours might be a little different depending on your settings): 

![VSCode Screenshot][VSCode Screenshot]

### 2. Remotely Connecting

You will need your course-specific account for CSE15L. You can find it at https://sdacs.ucsd.edu/~icc/index.php. 

Enter you username and Student ID in the corresponding input fields, then click `Submit`: 

![Account Lookup Tool][Account Lookup Tool]

You will then find your course-specific account: 

![Course-Specific Account][Course-Specific Account]

Open the terminal in VSCode. You can press ``Ctrl + ` `` or go to `Terminal` > `New Terminal` to open the terminal: 

![New Terminal Button][New Terminal Button]

To connect to the course-specific account on `ieng6`, run the following command in your terminal with your username instead of `cse15lsp22xxx`: 

`ssh cse15lsp22xxx@ieng6.ucsd.edu`

You will be prompted to write your password. Enter your password (nothing will be displayed as you type).

![]

Your computer (client) should now be connected to a computer in the CSE basement (server).

### 3. Trying Some Commands

Try running the following commands both on your computer and on the remote server: 
* `cd ~`
* `cd`
* `ls -lat`
* `ls -a`
* `cp /home/linux/ieng6/cs15lsp22/public/hello.txt ~/`
* `cat /home/linux/ieng6/cs15lsp22/public/hello.txt`

You can then exit the remote computer by running the command `exit`: 

![Exit Remote Computer][Exit Server]

### 4. Moving Files with `scp`

In this step, you will copy files from you computer to the remote server. Let's start by creating a file called "WhereAmI.java" with the following program: 
```
class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}
```

Run it on your computer's terminal with `javac WhereAmI.java`, then `java WhereAmI`.

In order to copy files from your computer to the remote server, your working directory has to contain the file you want to copy. 
Run the following command in the client to copy "WhereAmI.java" to the server's home directory (`~/`): 

`scp WhereAmI.java cs15lsp22xxx@ieng6.ucsd.edu:~/`

`cs15lsp22xxx` should be your username.

Enter your password when prompted to do so.

Login to `ieng6` and verify that "WhereAmI.java" is on the server by running the command `ls`.

Run the program on the server with `javac WhereAmI.java`, then `java WhereAmI`.

### 5. Setting an SSH Key

To avoid entering your password every you run the command `scp`, you can use ssh keys. 
To create a public/private rsa key pair, in the client, execute the following command in the client: 
`ssh-keygen`

If you are on Windows, run this command instead: 
`ssh-keygen -t ed25519`

When prompted to enter a file in which to save the key, input the path with your client's username instead of "<user-name>": 
`/Users/<user-name>/.ssh/id_rsa`

You will be prompted to enter a passphrase, but you should leave it empty (press `Enter`).

The private key (id_rsa) and the public key (id_rsa.pub) have been created in the ".ssh" directory of your computer.

You now need to copy the public key only to the ".ssh" of your user account on the server.
On the server, create a ".ssh" directory with: 
`mkdir .ssh`

`logout` (`Ctrl + D`) of the server. Now, on the client, copy the public key using: 
`scp /Users/<user-name>/.ssh/id_rsa.pub cs15lsp22xxx@ieng6.ucsd.edu:~/.ssh/authorized_keys`
where "<user-name>" is your username on your client.

You should now be able to use the commands `ssh` and `scp` without being required to enter your password: 

### 6. Optimizing Remote Running

There are other ways to copy a file from the client to the server more quickly. 
Instead of typing previous commands, you can use the up arrow. 
You can run many commands at the same time by adding a `;` between them. 
If you add a command in quotes `""` after `ssh`, the client will access the remote account, then run these commands and exit the account.

[VSCode Download Webpage]: screenshot-installing-vscode-webpage.png
[VSCode Screenshot]: screenshot-vscode.png
[Account Lookup Tool]: 
[Course-Specific Account]: 
[Exit Server]: 
[New Terminal Button]: screenshot-new-terminal-button.png

Guidelines
include the steps you took to log into a course-specific account on ieng6 
with at least 6 screenshots (of what each step looked like)
2-3 sentences for each step describing what you did
