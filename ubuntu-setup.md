# Ubuntu Setup

## Requirements

You must be running either of the two most recent LTS versions - 18.04 or 20.04.

## What to install

### Google Chrome

1. Using your default internet browser, navigate to the [Google Chrome Download]
   page.
2. Download and run the installer.
3. When prompted, set Google Chrome as your default internet browser.

[Google Chrome Download]:https://www.google.com/chrome/

### Visual Studio Code

1. Using Google Chrome, navigate to the [VS Code Download] page.
2. Download and run the Linux `.deb` installer.

[VS Code Download]:https://code.visualstudio.com/Download

### rbenv & Ruby

1. Run the following commands in your Ubuntu terminal to install `rbenv`:

```shell
   sudo apt install git curl libssl-dev libreadline-dev zlib1g-dev autoconf bison build-essential libyaml-dev libreadline-dev libncurses5-dev libffi-dev libgdbm-dev
   curl -fsSL https://github.com/rbenv/rbenv-installer/raw/HEAD/bin/rbenv-installer | bash
   echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
   echo 'eval "$(rbenv init -)"' >> ~/.bashrc
   echo 'export EDITOR="code --wait"' >> ~/.bashrc
   source ~/.bashrc
```

1. Run the following commands in your Ubuntu terminal to install the correct
   version of Ruby and the gems you'll be using in the course:

```shell
   rbenv install 2.5.1
   rbenv global 2.5.1
   rbenv rehash
   gem install bundler pry byebug
   gem install rails -v 5.2.3
   rbenv rehash
```

### PostgreSQL & SQLite

1. Run the following commands in your Ubuntu terminal to install PostgreSQL:

```shell
   sudo apt-get install postgresql libpq-dev
   sudo service postgresql start
   source ~/.bashrc
```

> Note that you will need to run the command `sudo service postgresql start`
> every time you restart the virtual machine. We recommend creating an alias for
> this and any other commands you find yourself running on a regular basis.

2. Run the following commands in your Ubuntu terminal to create a new PostgreSQL
   user:

   > Note that you need to replace `your_username` with the username that you
   > created for your Ubuntu virtual machine

```shell
   sudo -u postgres psql
   CREATE USER your_username WITH SUPERUSER CREATEROLE CREATEDB REPLICATION;
   ALTER ROLE your_username WITH BYPASSRLS;
   CREATE DATABASE your_username;
   \q
```

3. Run the following command in your Ubuntu terminal to install SQLite:

```shell
   sudo apt-get install sqlite3 libsqlite3-dev
```

### nvm & Node.js

1. Run the following commands in your Ubuntu terminal to install `nvm` and the
   correct version of Node.js:

```shell
   curl -sL https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh -o install_nvm.sh
   bash install_nvm.sh
   nvm install 14
   nvm use 14
   source ~/.bashrc
```
