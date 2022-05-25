# macOS M1 Setup

**IMPORTANT**  
These instructions are for **Macs with an Apple Silicon (M1) chip**. You can
find out if you have this chip by going to the Apple menu and choosing `About
This Mac`. If you see `Chip: Apple` then you are in the right place: you have an
Apple Silicon Mac.

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
4. Run VS Code and open the `Command Palette` menu option.
5. Type `shell command` into the search bar that pops up and select the option
   `Shell Command: Install 'code' command in PATH`.

[VS Code Download]: https://code.visualstudio.com/Download

### Xcode Command Line Tools

Run the following command in your terminal to install the Xcode CLI tools:

```shell
xcode-select --install
```

### Homebrew

Run the following commands in your terminal to install and configure Homebrew:

```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
```

### `git`

Run the following commands in your terminal to install and initialize your `git`
configuration. (Replace `"Your Name"` and `"Your Email"` with your actual name
and email--respectively--**in quotation marks**.)

```sh
brew install git
git config --global user.name "Your Name" 
git config --global user.email "Your Email"
git config --global init.defaultBranch main
```

### `rbenv`

Run the following commands in your terminal to install and configure `rbenv`:

```shell
brew install rbenv
echo 'eval "$(rbenv init -)"' >> ~/.zshrc
source ~/.zshrc
```

### Ruby

Run the following commands in your terminal to install the correct version of
Ruby and the gems you'll be using in the course:

```shell
rbenv install 3.1.1
rbenv global 3.1.1
rbenv rehash
gem install bundler pry byebug
gem update --system
brew install shared-mime-info
gem install rails -v 7.0.3
rbenv rehash
```

### PostgreSQL

1. Using Google Chrome, navigate to the [Postgres.app Download] page.
2. Download and run the Latest Release installer.
3. Run the following commands in your terminal to access the corresponding CLI
   tools

   ```shell
   sudo mkdir -p /etc/paths.d && echo /Applications/Postgres.app/Contents/Versions/latest/bin | sudo tee /etc/paths.d/postgresapp
   ```

4. Restart your terminal to complete the installation.

[Postgres.app Download]: https://postgresapp.com/downloads.html

### `nvm` & Node.js

Run the following commands in your terminal to install `nvm` and the correct
version of Node.js:

```shell
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
source ~/.zshrc
nvm install 16
nvm use 16
```
