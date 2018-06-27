---
title: New to Mac guide
date: 2018-06-01 03:15:00
tags: [MAC, development]
---

Today I start to use MAC for developing on my new job, it is really painful that so many shortcut or convention are different.
So I decided to log it down for me and any new comer for MAC :)

## Must install

* homebrew
    * You could almost install everything through `brew install <program name>` or `brew cask install <program with GUI>`
* iterm2
* [vscode](https://code.visualstudio.com/Download)
* [Oh-My-Zsh](https://github.com/robbyrussell/oh-my-zsh)
    * Change default shell to zsh with `chsh -s $(which zsh`

## Shortcut

* [Mac shortcuts](https://support.apple.com/en-us/ht201236)
* [Spotify](https://support.spotify.com/us/using_spotify/system_settings/keyboard-shortcuts/)
* [Evernote shorcut for mac](https://help.evernote.com/hc/en-us/articles/208313358-Keyboard-shortcuts-in-Evernote-for-Mac)
* [Chrome](https://support.google.com/chrome/answer/157179?hl=zh-Hant)
* Print screen area: `command + control + shift + 4` (control is optional for copy to clickboard)
* Open link in new tab: `command + click`
* Delete file: `command + backspace`
* Lock screen: `ctrl + command + q`
* Close window: `command + w`
* Quit app: `command + q`
* Fullscreen/Normalscreen: `ctrl + command + f`
* Hide window: `command + m`
* Show window: Hold `command + tab` to the app, then hold `option` then release command
* Open application preference: `command + ,`
* Switch different window in same application: `` command + ` ``

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
* zsh
    * [osx](https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins/osx)
    * [zsh-completions](https://github.com/zsh-users/zsh-completions)

## Optional install

* [nvm](https://github.com/creationix/nvm)
   * Handle Nodejs environment
* [Alfred](https://www.alfredapp.com/)
   * Replacement for `Spotlight`
* [超注音](https://applealmond.com/posts/27387)
* [spectacle](https://www.spectacleapp.com/)
   * Shortcut for docking windows
* [awesome-vim-configuration](https://github.com/amix/vimrc)
* [manico](https://itunes.apple.com/cn/app/manico/id724472954?mt=12)
   * Best tool for launching app with custom shortcut
* [insomniaX](http://semaja2.net/ye-ol-projects/insomniaxinfo/)
   * Prevent mac sleep behavior
* Beyond compare 
   * `brew cask install beyond-compare`
   * Best diff tool ever
* [Scroll Reverser](http://pilotmoon.com/scrollreverser/) 
   * `brew cask install scroll-reverser`
   * Seperate mouse / touchpad scroll direction setting

## Things you need to know

* If you command + tab switch window and nothings come up, it is because there is no window for this application, to quit application just simply command + q, or you could open window for this application by top menu bar
* `Spotlight` is search engine inside your Mac
* `Finder` is File Manager
* `Preview` has functionality of `painter`
