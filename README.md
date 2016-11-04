# Setup OSX

## Hostname

sudo scutil --set HostName [NewHostNameHere]

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

## Java

### Java 6

Download from https://support.apple.com/kb/DL1572?locale=en_GB
```
cd /Library/Java/JavaVirtualMachines
sudo ln -s 1.6.0.jdk/ jdk6
```

### Java 7

Download from http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase7-521261.html
```
cd /Library/Java/JavaVirtualMachines
sudo ln -s jdk1.7.0_80.jdk jdk7
```

### Java 8

Download from http://www.oracle.com/technetwork/java/javase/downloads/java-archive-javase8-2177648.html
```
Installed to /Library/Java/JavaVirtualMachines
sudo ln -s jdk1.8.0_102.jdk jdk8
```

## Maven

### Maven 2

Install to ~/opt
ln -s <version> mvn2
ln -s ~/opt/mvn2 ~/bin/mvn2

### Maven 3

Install to ~/opt
ln -s <version> mvn3
ln -s ~/opt/mvn3 ~/bin/mvn3

## Apps To Install
 - Chrome
 - iTerm2
 - Slack
 - Outlook
 - Tunnelblick
 - Sublime Text
 - Docker (https://docs.docker.com/docker-for-mac/)
