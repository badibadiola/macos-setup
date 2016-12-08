# Setup OSX

## Hostname

sudo scutil --set HostName fandorin

## Make User Directories

mkdir ~/bin
mkdir ~/opt
mkdir ~/workspace

## Brew

### Install Brew

```bash
ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"
```

### Install Cask

```bash
brew install caskroom/cask/brew-cask
```

### Install Tools
```bash
brew install curl
brew install wget
```

### Install Applications via Cask

```bash
brew cask install google-chrome
brew cask install iterm2
brew cask install slack
brew cask install tunnelblick
brew cask install sublime-text
brew cask install java
```

## Dotfiles
```bash
cd ~
git clone git@github.com:stevenhammerton/dotfiles.git
./dotfiles/deploy.py
```

## Preferences

Disable swipe between pages
```
System Preferences -> Trackpad -> More Gestures -> Swipe Between Pages
```

## Legacy Java

### Java 6

```bash
wget -O ~/Downloads/java6.dmg http://support.apple.com/downloads/DL1572/en_US/javaforosx.dmg
hdiutil mount ~/Downloads/java6.dmg
sudo installer -package /Volumes/Java\ for\ OS\ X\ 2015-001/JavaForOSX.pkg -target /Volumes/Macintosh\ HD
sudo ln -s /Library/Java/JavaVirtualMachines/1.6.0.jdk/ /Library/Java/JavaVirtualMachines/jdk6
hdiutil unmount "/Volumes/Java for OS X 2015-001"/
rm ~/Downloads/java6.dmg
```

### Java 7

Download from http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase7-521261.html
```bash
hdiutil mount ~/Downloads/jdk-7u80-macosx-x64.dmg
sudo installer -package /Volumes/JDK\ 7\ Update\ 80/JDK\ 7\ Update\ 80.pkg -target /Volumes/Macintosh\ HD
sudo ln -s /Library/Java/JavaVirtualMachines/jdk1.7.0_80.jdk/ /Library/Java/JavaVirtualMachines/jdk7
hdiutil unmount /Volumes/JDK\ 7\ Update\ 80
rm ~/Downloads/jdk-7u80-macosx-x64.dmg
```

## Maven

### Maven 2

```bash
wget -O ~/Downloads/apache-maven-2.2.1-bin.tar.gz https://archive.apache.org/dist/maven/binaries/apache-maven-2.2.1-bin.tar.gz
tar -xvf ~/Downloads/apache-maven-2.2.1-bin.tar.gz -C ~/opt/
ln -s ~/opt/apache-maven-2.2.1 ~/opt/mvn2
ln -s ~/opt/mvn2/bin/mvn ~/bin/mvn2
rm ~/Downloads/apache-maven-2.2.1-bin.tar.gz
```

### Maven 3

```bash
wget -O ~/Downloads/apache-maven-3.3.9-bin.tar.gz http://apache.mirrors.nublue.co.uk/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.tar.gz
tar -xvf ~/Downloads/apache-maven-3.3.9-bin.tar.gz -C ~/opt/
ln -s ~/opt/apache-maven-3.3.9 ~/opt/mvn3
ln -s ~/opt/mvn3/bin/mvn ~/bin/mvn
rm ~/Downloads/apache-maven-3.3.9-bin.tar.gz
```

## Apps To Install
 - Outlook
 - Docker (https://docs.docker.com/docker-for-mac/)
