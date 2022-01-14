# **Logging into an account on ieng6** #

## Installing VScode ##

Go to the VScode website [here](https://code.visualstudio.com/) and follow the instructions. There is a dropdown to show the different possible versions (macOS, Windows, Linux). Download the *Stable* build.

![Image](VSCodeInstall.png)

Then boot up VSCode. It should look something like this:

![Image](VSCodeOpened.png)

---
## Remotely Connecting ##

First, *if you are on Windows* set up [OpenSSH](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse)

![Image](OpenSSHWindows.png)

Then find your ieng6 account (CSE15L in this case) [here](https://sdacs.ucsd.edu/~icc/index.php).

![Image](ieng6AccountLookup.png)

Next, we will connect remotely in VSCode. With VSCode open, open a new terminal either through the top left of VSCode or `ctrl` or `cmd` and `+`. Input the command `ssh cs15lwi22##@ieng6.ucsd.edu` in the terminal but with your ieng6 account id instead of the **##**. `ssh` means secure shell, which is what you will be using. You will receive some messages upon logging in for the first time. Type *yes* and type your password when prompted. Your terminal should look similar (**not exactly**) to this:

![Image](SSHLogin.png)

---
## Trying Some Commands ##

Some useful commands that you can try include:

`cd <directory>` change directory

`ls <directory (blank implies current directory)>` list (files and directories)

`pwd` print working directory

`mkdir <new directory>` make directory

`cp <file>` copy

![Image](TryingSomeCommands.png)

To log out:

`Ctrl` or `Cmd` + `D` or run `exit`

---
## Moving Files with `scp` ##

blah

---
## Setting an SSH Key ##

blah

---
## Optimizing Remote Running ##

blah
