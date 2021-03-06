# Lab Report 3

* ### Streamlining ssh Configuration

The config file at `~/.ssh/config` on my computer was: 

![Config Before Editing][Config Before]

I edited it on Visual Studio Code to make the alias shorter, so I changed `ieng6.ucsd.edu` to `ieng6`.

![Config After Editing][Config After]

I was then able to login into my remote account through `ssh` using just the alias `ieng6`.

![SSH Login Using the Alias][SSH Login]

Similarly, I could `scp` a file using this alias.

![SCP a File Using the Alias][SCP]

* ### Setup Github Access from ieng6

The public key is stored at `~/.ssh/id_ed25519_github.pub` of my user account.

![Public Key on User Account][Public Key User Account]

I added the public key to my Github account in `Settings` -> `SHH and GPG keys` -> `SSH keys`.

![Public Key on Github][Public Key Github]

The private key is stored in the same directory as the public, at `~/.ssh/id_ed25519_github`.

![Private Key][Private Key]

After adding my SSH key to the ssh-agent (running `$ eval "$(ssh-agent -s)"`, then `ssh-add <path-to-private-key>`) and switching the remote URL from HTTPS to SSH (using `git remote set-url <remote-name> git@github.com:USERNAME/REPOSITORY.git`), I was able to commit and push a change to Github while logged into my ieng6 account.

![Git Commands][Git Commands]

[Commit From the Git Commands][Commit]

* ### Copy whole directories with scp -r

`scp -r` can copy recursively the markdown-parse directory and its content to my ieng6 account. 
Here I copy my working directory from my local computer into the `markdown-parse` directory of my ieng6 account. 
The `markdown-parse` directory on my remote account is created because it does not exist yet.

![SCP markdown-parse Directory to ieng6 Account][SCP Directory]

After logging into my ieng6 account using `ssh`, I can go to the `markdown-parse` directory and run the tests.

![Logging into ieng6 Account and Running Tests][Tests]

All these commands: 
* `scp -r` to copy the directory,
* `ssh` to connect to the ieng6 account, 
* `cd` to go to the directory, 
* `javac` to compile the code, and 
* `java` to run the tests.

can be united into one: 

`scp -r . ieng6:~/markdown-parse;ssh ieng6 "cd markdown-parse;/software/CSE/oracle-java-17/jdk-17.0.1/bin/javac -cp ./:./lib/junit-4.13.2.jar:./lib/hamcrest-core-1.3.jar MarkdownParseTest.java;/software/CSE/oracle-java-17/jdk-17.0.1/bin/java -cp ./:./lib/junit-4.13.2.jar:./lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest"`.

![SCP Directory and Run Tests in One Line][SCP Tests Command]

This single command copies the `markdown-parse` directory and runs the tests.

![Results of the One Line Command][SCP Tests Results]

[Config Before]: images/config-before.png
[Config After]: images/config-after.png
[SSH Login]: images/ssh-login.png
[SCP]: images/scp.png
[Public Key User Account]: images/public-key-user-account.png
[Public Key Github]: images/public-key-github.png
[Private Key]: images/private-key.png
[Git Commands]: images/git-commands.png
[SCP Directory]: images/scp-directory.png
[Tests]: images/tests.png
[SCP Tests Command]: images/scp-tests-command.png
[SCP Tests Results]: images/scp-tests-results.png

[Commit]: https://github.com/thanhnhanlam/markdown-parser/commit/8fc320bd6cb38505197931bf19887dbd37c1793d
