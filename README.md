# macOS minimalist Development Setup

<img src="./assets/macos.png" width="80" alt="macOS">

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

After 15 years of using Windows I migrated to macOS. I started to do some research about how to setup a dev environment mostly for web development: PHP, Javascript & Node. Not super complex, no crazy dev ops, no extensive use of the terminal nor a lot of automation.

I found awesome github repos and tutorials with information, automated install scripts and dozens of tools.
I started with the setup.

> It took me 2 days.

---

## I realized I needed something simpler
I meditate on a daily basis and I practice minimalism. Use and keep only what you need at a certain time.

## I created this guide to setup a macOS Zen Development Environment which can grow and shrink as needed
Goal: This guide is here to help my future self in case I wipe my computer or buy a new one and to help others with a similar approach.

Primitives:
- Having a maintainable guide to install a mac development environment in a new or wiped machine without thinking nor searching in Google for solutions
- Being able to install / uninstall anything without globals nor affecting Projects
- Avoiding to install any app that can be used in the browser: slack, spotify, gmail, google drive, etc ***unless***:
- Helping to create sustainable productivity: notion

## Getting Started
Plug in your new or wiped computer. Follow the installation process. The first thing you should do is update macOS to get the latest security updates and patches. Right now I am on Catalina and did not update to Big Sur yet.
## Command Line Tools
```bash
xcode-select --install
```

The Command Line Tools are installed at:
```bash
/Library/Developer/CommandLineTools/
```

## Homebrew
<img src="./assets/homebrew.png" width="80" alt="Homebrew">

Install Homebrew package manager: it will allow you to install, uninstall and manage packages/apps from the command line.

```bash
bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

## Tools
I will install git, github cli yarn and make with homebrew.

```bash
brew install \
  git \
  gh \
  yarn \
  make
```

## Apps
Must use apps for my development workflow.
```bash
brew install alfred
brew install firefox
brew install google-chrome
brew install rectangle
brew install phpstorm
brew install local
brew install notion
brew install postgres
brew install postico
brew install visual-studio-code
```

- Alfred is kind a replacement for Spotlight
- Firefox for Browsing
- Chrome for Development
- Rectangle for window management using keyboard shortcuts
- Phpstorm for PHP/Wordpress development
- Local by Flywheel for Wordpress development
- Notion
- Postgres
- Postico is a GUI to manage postgres DB
- Visual Studio Code for JAMPP development

## Git & SSH
<img src="./assets/macos.png" width="80" alt="git">
This config will help to have a global setup for git.

1. Create a git config file
2. Create a SSH config file
3. Generate SSH key
4. Set it up in github (or another provider)

1. Create a git config file

```
$ touch ~/.gitconfig # Creates the config file
$ open ~/.gitconfig  # Opens the config file
```

Add this to the git config file to set up some shortcuts and defaults.
I have set my email address in github to be private so in the email field it should be set the noreply github email alias. More info [here](https://github.com/dwyl/dev-setup/issues/22)
```text
[alias]
  # Show verbose output about tags, branches or remotes
  tags = tag -l
  branches = branch -a
  remotes = remote -v
  # Pretty log output
  hist = log --graph --pretty=format:'%Cred%h%Creset %s%C(orange)%d%Creset %Cgreen(%cr)%Creset [%an]' --abbrev-commit --date=relative

[color]
  ui = auto
[user]
	name = My Name
	email = email@my.me
[github]
  user   = username
[alias]
  a      = add
  cm     = commit -m
  s      = status
[core]
	excludesfile = /Users/user/.gitignore
[filter "lfs"]
	required = true
	clean = git-lfs clean -- %f
	smudge = git-lfs smudge -- %f
	process = git-lfs filter-process
[pull]
	ff = only
```

2. Create a SSH config file
```bash
$ mkdir ~/.ssh
$ touch ~/.ssh/config # Creates the config file
$ open  ~/.ssh/config  # Opens the config file
```

Add this to the config file. Save and close.
```
 Host *
    AddKeysToAgent yes
    UseKeychain no
    IdentityFile ~/.ssh/id_rsa
```

Generate a SSH key. If you are not sharing the key set the passphrase to none. Leave the key with default name (id_rsa)
```bash
$ ssh-keygen -t rsa -b 4096 -C "email@example.com"
```

Add the SSH key
```bash
$ ssh-add -K ~/.ssh/id_rsa
```

4. I use Github so future me, follow the github steps to add the SSH key [here](https://docs.github.com/en/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent):

## Node.js
Installing Node globally is a *bad practice*. You should install Node using nvm (Node Version Manager) or another version manager. nvm allows you to easily switch between Node versions, which is essential when you work in different projects.
I will install it using Homebrew.

```
brew install nvm
```

Create a directory for NVM

```
mkdir ~/.nvm
```

Open zsh config file

```bash
open ~/.zshrc
```

Add nvm config
```bash
export NVM_DIR=~/.nvm
source $(brew --prefix nvm)/nvm.sh
```

***Close the terminal and reopen it to reload config***

Echoing $NVM_DIR should now return your NVM directory

```bash
$ echo $NVM_DIR
/Users/username/.nvm
```

Install latest node stable version
```
nvm install node
```

Verify node installation

```
node -v && npm -v
```

## macOS Settings
Personal preferences on how to set up masOS. It is up to you.
## Default Commands
    # Show path bar
    defaults write com.apple.finder ShowPathbar -bool true

    # Show status bar
    defaults write com.apple.finder ShowStatusBar -bool true
### Dock
    Hide dock automatically.
### Sharing
    Change compauter name > Use something that cannot be matched to tour computed visually
### Security
    Security & Privacy > General > Require password immediately after sleep or screen saver begins.
    Security & Privacy > FileVault > Set it to enabled.
    iCloud > I do not use iCloud.
    Users & Groups > Setup a password if you did not setup one during installation.
### System
    Dock > Automatically hide and show the Dock
    Keyboard > Key Repeat > Fast (all the way to the right)
    Keyboard > Delay Until Repeat > Short (all the way to the right)
    Keyboard > Text > Disable "Correct spelling automatically"
    Keyboard > Text > Disable "Capitalize words automatically"
    Keyboard > Text > Disable "Add period with double-space"
    Trackpad > Enable "Tap to click"

## App Settings
### Visual Studio Code
    # Path
    Press CMD + SHIFT + P and click "Install code command in PATH"

    # Preferences
    "editor.tabSize": 2
    "editor.rulers": [80]

    # Extensions
    ESlint
    Gitlens
    Highlight Matching Tag
    Prettier

    # Theme
    Visual Studio Dark Theme

## Contributing
Found mistakes? Improvements? Caveats? Outdated commands? Let me know with a pull request.
## License
MIT ot Public Domain. Whatever.
