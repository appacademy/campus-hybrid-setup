# macOS Setup

## Requirements

You need to be running macOS Mojave or newer in order to follow these instructions.

> IMPORTANT If you have a mac with an Apple Silicon chip, please see the [Apple Silicon addendum] reading before proceeding with these instructions. You can find this 
> out by going to the Apple menu and choosing About this Mac.  If you see
> Chip: Apple then you have an Apple Silicon Mac.
 
[Apple Silicon addendum]:apple-silicon-addendum.md

## What to install

Install all of these pieces in order.

### Google Chrome

1. Using your default internet browser, navigate to the [Google Chrome Download] page.
2. Download and run the installer.
3. When prompted, set Google Chrome as your default internet browser.

[Google Chrome Download]:https://www.google.com/chrome/

### Visual Studio Code

1. Using Google Chrome, navigate to the [VS Code Download] page.
2. Download and run the Mac installer.
3. After installation completes, drag the VS Code app icon into your Applications folder.
4. Run VS Code and open the Command Palette menu option.
5. Type `shell command` into the search bar that pops up and select the option `Shell Command: Install 'code' command in PATH`.

[VS Code Download]:https://code.visualstudio.com/Download

### Xcode CLI & ZSH

1. Run the following commands in your terminal in order to install the Xcode CLI tools and set ZSH as your default shell
```shell
   xcode-select --install
   chsh -s /bin/zsh
```
2. Restart your terminal in order to complete the transition to ZSH

### Homebrew & git

1. Run the following commands in your terminal in order to install Homebrew and `git`
```shell
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
   brew install git
```

### rbenv & Ruby

1. Run the following commands in your terminal in order to install `rbenv`
```shell
   brew install rbenv
   echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.zshrc
   echo 'eval "$(rbenv init -)"' >> ~/.zshrc
   source ~/.zshrc
```

2. Run the following commands in your terminal in order to install the correct version of Ruby and the gems we'll be using in the course
```shell
   rbenv install 2.5.1
   rbenv global 2.5.1
   rbenv rehash
   gem install bundler pry byebug
   gem install rails -v 5.2.3
   rbenv rehash
```

> If you are running the Big Sur version of macOS and are unable to install Ruby version 2.5.1, try installing version 2.5.8 instead!
> If installing rails is throwing an error, try running `brew install shared-mime-info` and trying again.
   
### PostgreSQL & SQLite

1. Using Google Chrome, navigate to the [Postgres.app Download] page.
2. Download and run the Latest Release installer.
3. Run the following command in your terminal in order to access the corresponding CLI tools and install SQLite
```shell
   sudo mkdir -p /etc/paths.d && echo /Applications/Postgres.app/Contents/Versions/latest/bin | sudo tee /etc/paths.d/postgresapp
   brew install sqlite
```
4. Restart your terminal in order to complete the installation

[Postgres.app Download]:https://postgresapp.com/downloads.html

### nvm & Node.js

1. Run the following commands in your terminal in order to install `nvm` and the correct version of Node.js
```shell
   curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.6/install.sh | bash
   source ~/.zshrc
   nvm install 10.13.0
   nvm use 10.13.0
```
