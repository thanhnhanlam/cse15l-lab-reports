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

![Public Key on User Account][Public Key User Account]
![Public Key on Github][Public Key Github]

![Private Key][Private Key]

![Git Commands][Git Commands]

[Commit From the Git Commands][Commit]

* ### Copy whole directories with scp -r

![SCP markdown-parse Directory to ieng6 Account][SCP Directory]
![Logging into ieng6 Account and Running Tests][Tests]

![SCP Directory and Run Tests in One Line][SCP Tests Command]
![Results of the One Line Command][SCP Tests Results]

[Config Before]: ../image/lab-report-3/config-before.png
[Config After]: ../image/lab-report-3/config-after.png
[SSH Login]: ../image/lab-report-3/ssh-login.png
[SCP]: ../image/lab-report-3/scp.png
[Public Key User Account]: ../image/lab-report-3/public-key-user-account.png
[Public Key Github]: ../image/lab-report-3/public-key-github.png
[Private Key]: ../image/lab-report-3/private-key.png
[Git Commands]: ../image/lab-report-3/git-commands.png
[SCP Directory]: ../image/lab-report-3/scp-directory.png
[Tests]: ../image/lab-report-3/tests.png
[SCP Tests Command]: ../image/lab-report-3/scp-tests-command.png
[SCP Tests Results]: ../image/lab-report-3/scp-tests-results.png

[Commit]: https://github.com/thanhnhanlam/markdown-parser/commit/8fc320bd6cb38505197931bf19887dbd37c1793d
