# Dev Environment@macOS

## Homebrew

```shell
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## Terminal

### iTerm2

https://iterm2.com/downloads/stable/latest

### Zsh

```shell
$ brew install zsh zsh-completions
```

### Oh-my-zsh

Official homepage pls refer-> [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)

Install instruments

```shell
$ sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

#### Set theme

Refer->[iterm2-solarized.md](https://gist.github.com/kevin-smets/8568070)

![Powerlevel9k Font](https://gist.githubusercontent.com/kevin-smets/9722391f8b3e4fa436b1c1dcf05ecd88/raw/29389beaa891f939e274b8e20622647357e793d4/powerlevel9k.png)

1. Clone *Powerlevel9k* 

   ```shell
   $ git clone https://github.com/bhilburn/powerlevel9k.git ~/.oh-my-zsh/custom/themes/powerlevel9k
   ```

2. Set Theme in ~/.zhsrc

   ```shell
   ZSH_THEME="powerlevel9k/powerlevel9k"
   ```

3. Install patched fonts

   - [Meslo](https://github.com/powerline/fonts/blob/master/Meslo%20Slashed/Meslo%20LG%20M%20Regular%20for%20Powerline.ttf) (the one in the screenshot). Click "view raw" to download the font. 
   - [Source Code Pro](https://github.com/powerline/fonts/blob/master/SourceCodePro/Sauce%20Code%20Powerline%20Regular.otf) has better alignment for the glyphs @14px.
   - [Others @ powerline fonts](https://github.com/powerline/fonts)

   Open the downloaded font and press "Install Font".

   Set this font in iTerm2 (Meslo is my personal preference) (iTerm → Preferences → Profiles → Text → Change Font).

   Restart iTerm2 for all changes to take effect.

#### Plugins

1. autojump

   - install 

     ```shell
     $ brew install autojump
     ```

   - add below code to ~/.zshrc

     ```shell
     [ -f /usr/local/etc/profile.d/autojump.sh ] && . /usr/local/etc/profile.d/autojump.sh
     ```

2. zsh-syntax-highlighting

   - install

     ```shell
     $ git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
     ```

   - Activate the plugin in `~/.zshrc`:

     ```shell
      plugins=( [plugins...] zsh-syntax-highlighting)
     ```

   - Source `~/.zshrc` to take changes into account:

     ```shell
     $ source ~/.zshrc
     ```

### Solarized Color

1. Download solarized color repository

   ```Shell
   $ git clone git://github.com/altercation/solarized.git
   ```

2. Go to iterm2-colors-solarized directory and double click the **.itermcolors* files

   - Solarized Dark.itermcolors
   - Solarized Light.itermcolors

3. Set colors in iterm2

   1. iTerm2->Preferences->Profiles->Colors->Color Presets
   2. Select the solarized color

4. Directory color of **ls** command

   Since *ls* of macOS is not the *gnu ls*, consequently it does not display colors, we'd use dircolors to make it colorful.

   1. Download dircolors-solarized

      ```shell
      $ git clone https://github.com/seebi/dircolors-solarized.git
      ```

   2. Install *coreutils*

      ```shell
      $ brew install coreutils
      ```

   3. Create directory ~/.dir_colors to store theme file to use

      ```shell
      $ cd ~ & mkdir .dir_colors
      $ cp dircolors-solarized/dircolors.ansi-dark .dir_colors/
      ```

   4. Add below code to .zshrc file

      ```shell
      eval $(gdircolors ~/.dir_colors/dircolors.ansi-dark)

      #Aliases
      alias ls='gls --color=auto'
      alias ll='ls -al'
      ```



## Editor

### VIM

macOS has builtin vim, the configuration is inherited from https://github.com/ma6174/vim

```shell
$ brew install wget
$ wget -qO- https://raw.github.com/ma6174/vim/master/setup.sh | sh -x
```

After downloaded, edit ~/.vimrc to change the markdown and html open command with following codes:

```shell
...
elseif &filetype == 'html'
		exec "!open -a Safari %.html &"
elseif &filetype == 'mkd'
        exec "!~/.vim/markdown.pl % > %.html &"
        exec "!open -a Safari %.html &"
```

And add java file type support by adding below codes:

```shell
FileType java setlocal dict+=~/.vim/dict/java.dict
```



## Markdown Editor

### Typora

```shell
$ brew cask install typora
```

## UML

### StarUML

```shell
$ brew cask install staruml
```



## CVS

### git

macOS has builtin git, we can upgrade it with brew install

```shell
$ brew install git
```

### tig

*tig* is a text-mode interface for git https://github.com/jonas/tig

```shell
$ brew install tig
```

### gitup

```shell
$ brew cask install gitup
```

### gitfinder

```shell
$ brew cask install gitfinder
```



## Java

1. Install

```shell
$ brew cask install java
```

2. Check Info 

```shell
$ brew cask info java
```

###Dependency Mgt

#### Gradle

```shell
$ brew install gradle
```

#### Maven

1. install

   ```shell
   $ brew install maven
   ```

## 

## Python

### iPython

```shell
$ brew install ipython
```

### pip

https://pip.readthedocs.io/en/stable/installing/

### virtualenv

```shell
$ pip install virtualenv
```

## Go

1. install

   ```shell
   $ brew install golang
   ```

2. Go versions management 

   https://github.com/moovweb/gvm

   ```shell
   $ bash < <(curl -s -S -L https://raw.githubusercontent.com/moovweb/gvm/master/binscripts/gvm-installer)
   ```

   zsh will replace bash if you're using zshell.

3. Dependencies managment

   - [godep](https://github.com/tools/godep)

     ```shell
     $ go get github.com/tools/godep
     ```

   - [glide](https://glide.sh)

     ```shell
     $ brew install glide
     ```

   - Others

## APP Sever

### Tomcat

1. Install

```shell
$ brew install tomcat
```

2. Startup

To have launchd start tomcat now and restart at login:

```shell
$ brew services start tomcat
```

Or, if you don't want/need a background service you can just run:

  ```shell
$ catalina run
  ```



### Jetty

1. install 

   ```shell
   $ brew install jety
   ```

## Database

### MySQL

1. MySQL server

   ```shell
   $ brew install mysql
   ```

2. MySQL command line

   ```shell
   $ brew install mycli
   ```

3. Sequel Pro

   ```shell
   $ brew cask install sequel-pro
   ```

4. MySQL Workbench

   ```shell
   $ brew cask install mysqlworkbench
   ```

#### Flyway

```shell
$ brew install flyway
```

### Redis

1. redis server

   ```shell
   $ brew install redis
   ```



## IDE(Jetbrain family)

### Intellij IDEA

IDEA ultimate edition needs license!

1. Install

```shell
$ brew cask install intellij-idea
```

2. plugins

   - Lombok


   - plantuml
   - Color-ide (Seems not provided in plugin manager, can [download](https://plugins.jetbrains.com/plugin/download?updateId=11436) it manually)

3. Solarized color

   1. download solarized color from [intellij-colors-solarized](https://github.com/jkaving/intellij-colors-solarized) rather than the main repository of solarized color. Since the main repository *settings.jar* in intellij-colors-solarized directory does not work well on Intellij IDEA.
   2. import it from disk, select `File > Import Settings`
   3. Set Scheme, select `Preferences > Editor > Color Scheme > General > Solarized Dark`
   4. Install Color-ide plugin as former description

4. Configuration

   - Import Gradle Project

     After opening Idea, user needs to setup gradle firstly as below steps:

     1. On the bottom right, select `Configure > Project Defaults > Project Structure`: 

        ![idea-setup](https://i.stack.imgur.com/xijoa.png)

   2. Picking the `Project` tab on the left will show that you have no SDK selected. Just click the `New...` button on the right hand side of the dropdown and point it to your JDK. After that, you can go back to the import screen and it should just show up.

      ![gradle-vm-option](https://i.stack.imgur.com/g2XZf.png)

### Pycharm

brew cask could install pycharm-community edition. The professional edition needs licence!

```shell
$ brew cask install pycharm-ce
```

### CLION

!!!Clion needs licence.

```shell
$ brew cask install clion
```



## Debug Tools

### Postman

```shell
$ brew cask install postman
```

### Charles

```shell
$ brew cask install charles
```

### Wireshark

```shell
$ brew cask install wireshark
```



## Others

### Xcode

Mac App Store

### Dash

```shell
$ brew cask install dash
```

### Xmind

```shell
$ brew cask install xmind
```

### CLI admin tool

https://github.com/rgcr/m-cli

```shell
$ brew install m-cli
```

### Chrome

```shell
$ brew cask install google-chrome
```

### Firefox

```shell
$ brew cask install firefox
```

### Slack

```shell
$ brew cask install slack
```

### Skype

```shell
$ brew cask install skype
```



### Quicklook plugins

[Quicklook plugins](https://github.com/sindresorhus/quick-look-plugins) provide user with many convenient functionalities.

#### install all 

```shell
$ brew cask install qlcolorcode qlstephen qlmarkdown quicklook-json qlprettypatch quicklook-csv betterzipql qlimagesize webpquicklook suspicious-package quicklookase qlvideo
```

