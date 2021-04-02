# Windows Setup

Welcome Windows users! Your operating system comes from a different lineage than
most operating systems, Windows has it's roots in MS-DOS and Windows NT, while 
macOS and Linux both are "Unix" style operating systems. We will be using the
Unix command line in this course so everyone in class is using the same command
line tools and programs. Windows does not include a unix style system by default
so we are doing to use a add-on piece of Microsoft Technology called "Windows
Subsystem for Linux".

## WSL

Windows Subsystem for Linux is a Linux Virtual Computer that you run on your
PC. It gives you all the same tools and command line utilities that your
mac and Linux using classmates use.

To install WSL you must have a specific version of Windows 10.

> For x64 systems: Version 1903 or higher, with Build 18362 or higher.

If you do not have this version or cannot update to this version, please
contact an instructor.

## Installing WSL 2

Future versions of Windows will include an automatic installer for WSL, but
for now you will have to use the manual install instructions:

[Windows Subsystem for Linux Installation Guide for Windows 10](https://docs.microsoft.com/en-us/windows/wsl/install-win10#manual-installation-steps)

Follow this guide to install WSL 2 and Ubuntu Linux. We recommend installing Ubuntu 18.04 LTS, found [here](https://www.microsoft.com/store/apps/9N9TNGVNDL3Q).

## Tips for using WSL

You will launch the Ubuntu terminal when the instructions in our curriculum tell
you to open a Terminal.

You should always store your code files in your Ubuntu home directory and not in
your Windows users home directory on your C: drive. Many of the tools we use
will perform better and be more stable if the files exist on the Ubuntu filesystem.

If you do need to access the files in your Ubuntu home directory from Windows
Explorer you can type `Windows + R` to bring up the run command dialog and type
`\\wsl$\home\<your-user>` replacing `your-user` with your Ubuntu user name (you
can find this out by typing `whoami` at your Ubuntu terminal prompt.)

If you want to access your Windows hard drive from Ubuntu you can use the path
`/mnt/c` inside of the Ubuntu virtual machine.

If you ever need to restart the Ubuntu virtual machine, you need to open a
Powershell window and run the following command:

```shell
wsl --shutdown
```

Next time you open the Ubuntu terminal it will start the virtual machine back up.

## Install everything else

Now that you have WSL installed you can install all the rest of these tools in
this order:

### Google Chrome

1. Using your default internet browser, navigate to the [Google Chrome Download] page.
2. Download and run the installer.
3. When prompted, set Google Chrome as your default internet browser.

[Google Chrome Download]:https://www.google.com/chrome/

### Visual Studio Code

1. Using Google Chrome, navigate to the [VS Code Download] page.
2. Download and run the Windows installer.

[VS Code Download]:https://code.visualstudio.com/Download

### rbenv & Ruby

1. Run the following commands in your Ubuntu terminal in order to install `rbenv`
```shell
   sudo apt install git curl libssl-dev libreadline-dev zlib1g-dev autoconf bison build-essential libyaml-dev libreadline-dev libncurses5-dev libffi-dev libgdbm-dev
   curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-installer | bash
   echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
   echo 'eval "$(rbenv init -)"' >> ~/.bashrc
   echo 'export EDITOR="code --wait"' >> ~/.bashrc
   source ~/.bashrc
```

2. Run the following commands in your Ubuntu terminal in order to install the correct version of Ruby and the gems we'll be using in the course
```shell
   rbenv install 2.5.1
   rbenv global 2.5.1
   rbenv rehash
   gem install bundler pry byebug
   gem install rails -v 5.2.3
   rbenv rehash
```

### PostgreSQL & SQLite

1. Run the following commands in your Ubuntu terminal in order to install PostgreSQL
```shell
   sudo apt-get install postgresql libpq-dev
   sudo service postgresql start
   source ~/.bashrc
```
> Note that you will need to run the command `sudo service postgresql start` every time you restart the virtual machine. We recommend creating an alias for this and any other commands you find yourself running on a regular basis.

2. Run the following commands in your Ubuntu terminal in order to create a new PostgreSQL user
> Note that you need to replace `your_username` with the username that you created for your Ubuntu virtual machine
```shell
   sudo -u postgres psql
   CREATE USER your_username WITH SUPERUSER CREATEROLE CREATEDB REPLICATION;
   ALTER ROLE your_username WITH BYPASSRLS;
   CREATE DATABASE your_username;
   \q
```

3. Run the following command in your Ubuntu terminal in order to install SQLite
```shell
   sudo apt-get install sqlite3 libsqlite3-dev
```

### nvm & Node.js

1. Run the following commands in your Ubuntu terminal in order to install `nvm` and the correct version of Node.js
```shell
   curl -sL https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh -o install_nvm.sh
   bash install_nvm.sh
   nvm install 10.13.0
   nvm use 10.13.0
   source ~/.bashrc
```
