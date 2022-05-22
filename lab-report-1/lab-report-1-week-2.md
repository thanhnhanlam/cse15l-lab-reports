# Week 2 Lab Report

## Logging into a course-specific account on `ieng6`

In this tutorial, you will learn how to log into a course-specific account on `ieng6`.

### 1. Installing VSCode

Go to https://code.visualstudio.com/Download. Click on the button corresponding to your operating system (macOC, Windows, or Linux) to download Visual Studio Code: 

![VSCode Download Webpage][Download VSCode]

Follow the instructions to install VSCode. Once installed, opening VSCode should look like this (yours might be a little different depending on your settings): 

![VSCode Screenshot][VSCode Screenshot]

### 2. Remotely Connecting

You can find your course-specific account for CSE15L at https://sdacs.ucsd.edu/~icc/index.php. 

Enter you username and Student ID in the corresponding input fields, then click `Submit`: 

![CSE Account Lookup Tool][Account Lookup Tool]

You will be able to see your course-specific account: 

![Course-Specific Account][CSE Account]

Open the terminal in VSCode. You can press ``Ctrl + ` `` or go to `Terminal` > `New Terminal` to open the terminal: 

![New Terminal Button][New Terminal Button]

To connect to the course-specific account on `ieng6`, run the following command in your terminal with your username instead of `cse15lsp22xxx`: 

`ssh cse15lsp22xxx@ieng6.ucsd.edu`

You will be prompted to write your password. Enter your password (nothing will be displayed as you type).

![SSH Login][SSH Login]

Your computer (client) should now be connected to a computer in the CSE basement (server).

### 3. Trying Some Commands

Try running the following commands both on your computer and on the remote server: 
* `cd`
  * `cd` means "change (working) directory", but will do nothing because the path is not specified
* `cd ~`
  * this command will go to the home directory (represented by `~` or `~/`)
* `pwd`
  * `pwd` means "pring working directory" and will print the path of the working directory
* `ls -a`
  * this command will display all the content of the current working directory (in alphabetical order)
* `ls -at`
  * this command will display all the content of the current working directory in chronological order
* `ls -lat`
  * this command will display a list of all the content of the current working directory in chronological order in the form of a list
  * `-lat` is the combination of `-a`, `-l`, and `-t`
* `cp /home/linux/ieng6/cs15lsp22/public/hello.txt ~/`
  * `cp` will copy the specified file `/home/linux/ieng6/cs15lsp22/public/hello.txt` to the specified location `~/`
* `cat /home/linux/ieng6/cs15lsp22/public/hello.txt`
  * `cat` means "concatenate` and will display the content of the specified file
* `exit`
  * this commands logs you out of the remote server
  * alternatively, you can use the command `logout` or press `Ctrl + D`

![Running the Commands][Run Commands]

### 4. Moving Files with `scp`

In this step, you will copy files from you computer to the remote server. Create a file called "WhereAmI.java" with the following program: 
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

![WhereAmI.java][Program File]

Run it on your computer's terminal using `javac WhereAmI.java`, then `java WhereAmI`.

In order to copy files from your computer to the remote server, your working directory has to be the one containing the file you want to copy. 
Run the following command in the client to copy "WhereAmI.java" to the server's home directory (`~/`): 

`scp WhereAmI.java cs15lsp22xxx@ieng6.ucsd.edu:~/`

`cs15lsp22xxx` should be your username.

Enter your password when prompted to do so.

Login to `ieng6` and verify that "WhereAmI.java" is on the server by running the command `ls`.

Run the program on the server with `javac WhereAmI.java`, then `java WhereAmI`.

![Copy the File and Run the Program Remotely][Run SCP]

### 5. Setting an SSH Key

To avoid entering your password every you run the command `scp`, you can use ssh keys. 
To create a public/private rsa key pair, in the client, execute the following command in the client: 
`ssh-keygen`

If you are on Windows, run this command instead: 
`ssh-keygen -t ed25519`

When prompted to enter a file in which to save the key, input the path with your client's username instead of `<user-name>`: 

`/Users/<user-name>/.ssh/id_rsa`

You will be prompted to enter a passphrase, but you should leave it empty (press `Enter`).

The private key (id_rsa) and the public key (id_rsa.pub) have been created in the ".ssh" directory of your local computer.

You now need to copy the public key only to the ".ssh" of your user account on the server.
On the server, create a ".ssh" directory with: 

`mkdir .ssh`

`exit` the server.

![Generate SSH-Key Pair][SSH Keys] 

Then, on the client, copy the public key using: 

`scp /Users/<user-name>/.ssh/id_rsa.pub cs15lsp22xxx@ieng6.ucsd.edu:~/.ssh/authorized_keys`

where `<user-name>` is your username on your client.

You should now be able to use the commands `ssh` and `scp` without being required to enter your password: 

![Login Without Password][Login Without Password]

### 6. Optimizing Remote Running

There are ways to copy a file from the client to the server more quickly. 
- Instead of typing previous commands, you can use the up arrow to recall the last command that was run (keep pressing the arrow to recall even older commands). 
- You can run many commands at the same time by adding a `;` between them. 
- If you add a command in quotes `""` after `ssh`, the client will access the remote account, then run the command and exit the account.
  
After making a local edit to "WhereAmI.java", you can copy the updated file to the server and run it on the server with the following command: 
`scp WhereAmI.java cs15lsp22xxx@ieng6.ucsd.edu:~/;ssh cs15lsp22xxx@ieng6.ucsd.edu "javac WhereAmI.java; java WhereAmI"`

![Optimized Command][Optimized Command]

---

Sources Used: Lab 1 Writeup and Lab 1 group notes

---

Replace `cs15lsp22xxx` by your user account's username on the remote server.
  
Replace `<user-name>` by the username of your local computer.

[Download VSCode]: images/download-vscode.png
[VSCode Screenshot]: images/vscode.png
[Account Lookup Tool]: images/account-lookup.png
[CSE Account]: images/cse-account-lookup.png
[SSH Login]: images/ssh-login.png
[Exit Server]: images/exit-server.png
[New Terminal Button]: images/new-terminal-button.png
[Run Commands]: images/run-commands.png
[Program File]: images/program-file.png
[Run SCP]: images/run-scp.png
[SSH Keys]: images/ssh-keys.png
[Login Without Password]: images/login-without-password.png
[Optimized Command]: images/optimized-command.png
