---
title: New to Macbook guide for developer
date: 2018-09-19 03:15:00
tags: [MAC, development, install-list, OSX, macOS]
---

Recently I start to use Macbook Pro for software development. It is really painful that so many shortcut and software are different from Windows. I hope log it down could help some MAC new comers :)

## Recommended install list

* homebrew
  * You could almost install everything through `brew install <program name>` or `brew cask install <program with GUI>`
* [iterm2](https://www.iterm2.com/)
  * Better terminal in MAC
* [Oh-My-Zsh](https://github.com/robbyrussell/oh-my-zsh)
  * Change default shell to zsh with `chsh -s $(which zsh)`
* [vscode](https://code.visualstudio.com/Download)
* [Karabiner-Elements](https://github.com/tekezo/Karabiner-Elements)
  * `brew cask install Karabiner-Elements`
  * Keyboard mapper, if you use your own keyboard you should install it!
* [nvm](https://github.com/creationix/nvm)
  * Handle Nodejs environment
* [超注音](https://applealmond.com/posts/27387)
  * Enable the ability to switch language by `shift`
* [spectacle](https://www.spectacleapp.com/)
  * Shortcut for docking windows
* [awesome-vim-configuration](https://github.com/amix/vimrc)
* [manico](https://itunes.apple.com/cn/app/manico/id724472954?mt=12)
  * Best tool for launching app with custom shortcut
* [Scroll Reverser](http://pilotmoon.com/scrollreverser/)
  * `brew cask install scroll-reverser`
  * Seperate mouse / touchpad scroll direction setting
* [diff-so-fancy](https://github.com/so-fancy/diff-so-fancy)
  * Make your git diff so fancy
  * `brew install diff-so-fancy`
  * `git config --global core.pager "diff-so-fancy | less --tabs=4 -RFX"`

## Shortcut

* [Mac shortcuts](https://support.apple.com/en-us/ht201236)
* [Spotify](https://support.spotify.com/us/using_spotify/system_settings/keyboard-shortcuts/)
* [Chrome](https://support.google.com/chrome/answer/157179?hl=zh-Hant)
* [Zsh Git Alias](https://github.com/robbyrussell/oh-my-zsh/blob/master/plugins/git/git.plugin.zsh)
* Print screen area: `command + control + shift + 4` (`control` is optional for copy to clipboard)
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
* Show desktop `(fn) + F11`

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
* Disable firefox and other apps notification sound
  * `System Preferences > Notifications` Choose Firefox and uncheck `Play sound for notifications` to get rid of the sound.

## Things you need to know

* If you command + tab switch window and nothings come up, it is because there is no window for this application, to quit application just simply command + q, or you could open window for this application by top menu bar
* `Spotlight` is search engine inside your Mac
* `Finder` is File Manager
* `Preview` has functionality of `painter`

## Read more

* [Mac輸入法教學](http://letsoffice.tw/2016mackeyin/)
