---
title: New to Mac guide
date: 2018-06-01 03:15:00
tags: [MAC, development]
---

Today I start to use MAC for developing on my new job, it is really painful that so many shortcut or convention are different.
So I decided to log it down for me and any new comer for MAC :)

## Must install

* homebrew
* iterm2
* [vscode](https://code.visualstudio.com/Download)

## Shortcut

* Print screen area: command + control + shift + 4 (control is optional for copy to clickboard)
* Open link in new tab: command + click
* Delete file: command + backspace
* Lock screen: ctrl + command + q
* [Evernote shorcut for mac](https://help.evernote.com/hc/en-us/articles/208313358-Keyboard-shortcuts-in-Evernote-for-Mac)
* Close window: command + w
* Quit app: command + q
* Max/Miniimize window: ctrl + command + f

## Settings

* Finder
    `View` > `Show Status Bar`, `Show Path Bar`
* Iterm
    `Menu bar` > `iterm2` > `Make iIerm2 default term`
* VSCode
    * To use `zsh`, edit user settings:
    ```json
    "terminal.integrated.shell.osx": "zsh",
    "terminal.integrated.fontFamily": "Menlo for Powerline"
    ```
    * [Use terminal to open vscode](https://stackoverflow.com/questions/30065227/run-open-vscode-from-mac-terminal):
    `Command + Shift + P` then `Shell Command : Install code in PATH`, then you can type `code <folder path>` to open vscode

## Optional install

* [nvm](https://github.com/creationix/nvm)
* [Alfred](https://www.alfredapp.com/)
* [Oh-My-Zsh](https://github.com/robbyrussell/oh-my-zsh)
    change default shell to zsh with `chsh -s $(which zsh`