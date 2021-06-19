---
title: My MacOSX Development Environment
tags:
  - brew
  - macosx
keywords:
  - brew
  - MacOSX
  - iterm2
  - zsh
  - on-my-zsh
  - multi-screen
description: Here are the steps I setup my macOSX development enviornment.
abbrlink: '20270909'
date: 2021-06-19 00:27:31
categories: 
---



### Mac App Store 

- Microsoft Office 365 - Word, Excel, PowerPoint, Outlook, OneNote, OneDrive
- Microsoft Remote Desktop



### Brew 🍺

```bash
# Install brew
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

# Install Packages
brew install \
    wget \ # For Download
    git-extras \ # Dev
    python \ # Python 3 (latest)
    php \ # PHP (latest)
    colordiff \ # Replace diff
    node \ # Dev
    composer \ # PHP Dev
    expect \ # For boost ssh
    mas # App Store CLI

# Install Apps
brew install --cask \
    firefox \ # broewser
    microsoft-edge \ # browser
    google-chrome \ # browser
    aerial \ # Beauty Screen Saver
    caffeine \ # Don't sleep
    stretchly \ # Rest reminder
    appcleaner \ # Deeply remove App
    cheatsheet \ # long push command to show shortcut
    rectangle \ # Move and resize windows
    vlc \ # Video player
    gimp \ # Painter plus
    the-unarchiver \ # unzip
    iterm2 \ # Replace buildin Terminal
    microsoft-teams \ # For work
    diffmerge \ # Compare code
    visual-studio-code \ # The best IDE
    phpstorm \ # Dev for Magento
    sequel-pro \ # Connect MySQL
    azure-data-studio \ # Connect MSSQL
    visual-studio-code \
    typora \ # Markdown editor
    notion \ # The best note I think !!
    docker \ # Dev
    postman # Web API Dev
    
# FileZilla (brew is not support ...)
open https://filezilla-project.org/download.php?type=client

# Brew Update Command
brew update &&
	brew upgrade &&
	brew upgrade --cask &&
	brew autoremove &&
	brew cleanup &&
	brew doctor
```



### iTerm2

```bash
# Install iTerm2
brew install --cask iterm2

# Term2 Settings
iTerm2 > Make iTerm2 Default Term
Preferences > Profiles > Terminal > Report Terminal Type > xterm-256color
Preferences > Profiles > Colors > Color Presets > Dark Background

# Fonts - Monaco Nerd Font
https://github.com/Karmenzind/monaco-nerd-fonts/raw/master/fonts/Monaco%20Nerd%20Font%20Complete.otf
Preferences > Profiles > Text > Font > Monaco Nerd Font

# Silence bell
Preferences > Profiles > Terminal > Notifications > Silence bell

# Shell Integration
https://www.iterm2.com/documentation-shell-integration.html
iTerm2 > Install Shell Integration
curl -L https://iterm2.com/shell_integration/install_shell_integration_and_utilities.sh | bash

# iTerm2 Shortcut
https://gist.github.com/squarism/ae3613daf5c01a98ba3a
```



### ZSH

```bash
# macOS Catalina (10.15) use zsh by default !!

# Install zsh
brew install zsh

# Switch to zsh by default
echo "/usr/local/bin/zsh" | sudo tee -a /etc/shells 
chsh -s /usr/local/bin/zsh
```

#### oh-my-zsh

```bash
# Install oh-my-zsh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Edit buildin plugins in ~/.zshrc
plugins=(
  aws
  brew
  composer
  colored-man-pages
  colorize
  git
  gitfast
  git-prompt
  docker
  docker-compose
  extract
  pip
  python
  osx
  vscode
  z
)

# Install zsh plugin by brew
brew install \
    zsh-syntax-highlighting \
    zsh-autosuggestions \
    zsh-completions
    
# Add other plugins in ~/.zshrc
source /usr/local/share/zsh-autosuggestions/zsh-autosuggestions.zsh
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
if type brew &>/dev/null; then
  FPATH=$(brew --prefix)/share/zsh-completions:$FPATH
  autoload -Uz compinit
  compinit
fi
```



### [My Shell Config](https://github.com/rangerz/config)

```bash
cd ~
git clone https://github.com/rangerz/config.git
~/config/install.sh
exec $SHELL
```



### Git + GPG

```bash
git config --global user.name "Your Name"
git config --global user.email "Your Email"

# Git GPG
# https://github.com/muwenzi/Program-Blog/issues/133
brew install gpg
gpg --gen-key
gpg --list-secret-keys --keyid-format LONG
gpg --armor --output public-key.txt --export E68AFE14FC29E92414C2E6AF731D0E574165A8D
gpg --armor --output private-key.txt --export-secret-keys

git config --global user.signingkey E68AFE14FC29E92414C2E6AF731D0E574165A8C0
git config --global commit.gpgsign true
```



### SSH with password (exssh)

```bash
# Install required package
brew install expect

curl -O https://gist.githubusercontent.com/rangerz/9e83514acf32ec4b094d0f16ce618ff8/raw/99c98d2d719b119d6eb8fc171762fd2f73d1fd5b/exssh
chmod +x exssh
sudo mv exssh /usr/local/bin/exssh

# Usage
exssh user@localhost password
```



### MacOS Config

#### Screenshots Folder

```bash
defaults write com.apple.screencapture location ~/Desktop/Screenshots
killall SystemUIServer
```



#### Mouse Setting

```markdown
# Point & Click
- [x] Look up & data detectors
- [o] Secondary click - Click or tap with two fingers
- [o] Tap to click

# Scroll & Zoom
- [x] Scroll direction: Natural
- [o] Zoon in or out
- [x] Smart zoom
- [x] Rotate

# More Gestures
- [o] All

# Three finger drag
- Accessibility -> Pointer Control -> Trackpad Options -> Enable dragging -> three finger drag
- https://support.apple.com/en-us/HT204609
```



#### Keyboard Setting

```markdown
# 輸入法 (Typing)
- Keyboard -> Input Source -> Select the previous input source -> Zhuyin
- Use the Caps Lock key to switch to and from U.S.

# Disable Capital Char and Smart Quotes
- Keyboard -> Text
- [x] Capitalize words outomatically
- Use smart quotes and dashes
"abc"
'abc'

# Shift + Insent (Paste Text)
- https://superuser.com/questions/703162/shift-insert-to-paste-in-mac-os-x
- https://apple.stackexchange.com/questions/32297/how-can-i-reassign-the-copy-paste-keyboard-shortcuts

# Home & End keys like Windows
- https://damieng.com/blog/2015/04/24/make-home-end-keys-behave-like-windows-on-mac-os-x
```



#### ulimit

https://medium.com/mindful-technology/too-many-open-files-limit-ulimit-on-mac-os-x-add0f1bfddde



#### Double Screens

https://medium.com/thevelops-tech-blog/how-to-switch-focus-between-screens-in-macos-21c6f02883a6

```bash
# CatchMouse + Karabiner Elements
# Install CatchMouse in Apple Store
brew install --cask karabiner-elements
```











