# macOS Setup

**IMPORTANT**  
These instructions are for Macs **without** an Apple Silicon (M1) chip. You can
find out if you have this chip by going to the Apple menu and choosing `About
This Mac`. If you see `Chip: Apple`, then you have an Apple Silicon Mac and
should follow the `Apple Silicon (M1) Setup` instead. (See the left-hand sidebar
menu.)

## Requirements

You need to be running macOS Mojave or newer to follow these instructions.

## Installing the software

Install all of the following software in order.

### Google Chrome

1. Using your default internet browser, navigate to the [Google Chrome Download]
   page.
2. Download and run the installer.
3. When prompted, set Google Chrome as your default internet browser.

[Google Chrome Download]: https://www.google.com/chrome/

### Visual Studio Code

1. Using Google Chrome, navigate to the [VS Code Download] page.
2. Download and run the Mac installer.
3. After installation completes, drag the VS Code app icon into your
   Applications folder.
4. Run VS Code and open the Command Palette menu option.
5. Type `shell command` into the search bar that pops up and select the option
   `Shell Command: Install 'code' command in PATH`.

[VS Code Download]: https://code.visualstudio.com/Download

### Xcode CLI & ZSH

1. Run the following commands in your terminal to install the Xcode CLI tools
   and set ZSH as your default shell

   ```text
   xcode-select --install
   chsh -s /bin/zsh
   ```

2. Restart your terminal to complete the transition to ZSH

### Homebrew & git

1. Run the following commands in your terminal to install Homebrew and `git`:

   ```text
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
   brew install git
   ```

2. Run the following commands in your terminal to initialize your `git`
   configuration. (Replace `"Your Name"` and `"Your Email"` with your actual
   name and email--respectively--in quotation marks.)

   ```text
   git config --global user.name "Your Name" 
   git config --global user.email "Your Email"
   git config --global init.defaultBranch main
   ```

### rbenv & Ruby

1. Run the following commands in your terminal to install `rbenv`:

   ```text
   brew install rbenv
   echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.zshrc
   echo 'eval "$(rbenv init -)"' >> ~/.zshrc
   source ~/.zshrc
   ```

2. Run the following commands in your terminal to install the correct version of
   Ruby and the gems you'll be using in the course:

   ```text
   rbenv install 3.1.1
   rbenv global 3.1.1
   rbenv rehash
   gem install bundler pry byebug
   gem install rails -v 7.0.3
   rbenv rehash
   ```

   > If installing Rails is throwing an error, try running `brew install
   > shared-mime-info` and trying again.

### PostgreSQL & SQLite

1. Using Google Chrome, navigate to the [Postgres.app Download] page.
2. Download and run the Latest Release installer.
3. Run the following commands in your terminal in order to access the
   corresponding CLI tools and install SQLite:

   ```text
   sudo mkdir -p /etc/paths.d && echo /Applications/Postgres.app/Contents/Versions/latest/bin | sudo tee /etc/paths.d/postgresapp
   brew install sqlite
   ```

4. Restart your terminal to complete the installation.

[Postgres.app Download]: https://postgresapp.com/downloads.html

### nvm & Node.js

1. Run the following commands in your terminal to install `nvm` and the correct
   version of Node.js:

   ```text
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
   source ~/.zshrc
   nvm install 18
   nvm use 18
   ```
