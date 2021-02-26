## A macOS Minimalist Development Setup

After 15 years of using Windows I migrated to macOS. I started to do some research about how to setup a dev environment mostly for web development: PHP, Javascript & Node. Not super complex, no crazy dev ops, no extensive use of the terminal nor a lot of automation.

I found awesome github repos and tutorials with information, automated install scripts and dozens of tools. 
I started with the setup.

> It took me 2 days.  

---

## I realized I needed something simpler

I meditate on a daily basis and I practice minimalism. Use and keep only what you need at a certain time.

## I created this guide to setup a macOS Zen Development Environment which can grow and shrink as needed
This guide is here to help my future self in case I wipe my computer or buy a new one and to help others with a similar approach. 

## Getting Started
Plug in your brand new mac, select your language, time zone, Apple ID, and so on. The first thing you should do is update macOS to get the latest security updates and patches. Right now I am on Catalina and did not update to Big Sur yet.
## Command Line Tools
```xcode-select --install```

The Command Line Tools are installed at:
```/Library/Developer/CommandLineTools/```

## Homebrew
Install Homebrew package manager: it will allow you to install, uninstall and manage packages/apps from the command line.

``` bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)" ```

## Node.js
Installing Node globally is a *bad practice*. You should install Node using nvm (Node Version Manager) or another version manager. nvm allows you to easily switch between Node versions, which is essential when you work in different projects. 
I will install it using Homebrew.

```brew install nvm```

Create a directory for NVM

`mkdir ~/.nvm`

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
/Users/spaceman/.nvm
```



