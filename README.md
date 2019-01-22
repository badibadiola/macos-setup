# Setup OSX

## macOS Settings

```bash
sudo scutil --set ComputerName tailstrike
sudo scutil --set HostName tailstrike
sudo scutil --set LocalHostName tailstrike
sudo defaults write /Library/Preferences/SystemConfiguration/com.apple.smb.server NetBIOSName -string tailstrike

sudo networksetup -setsearchdomains Wi-Fi h7n.uk openmarket.com lon.openmarket.com mxtelecom.com
sudo networksetup -setsearchdomains "Thunderbolt Bridge" h7n.uk openmarket.com lon.openmarket.com mxtelecom.com

# Disable automatic keyboard backlight
# sudo defaults write /Library/Preferences/com.apple.iokit.AmbientLightSensor "Automatic Keyboard Enabled" -bool false

# Speed up mouse tracking
defaults write -g com.apple.mouse.scaling  2.0

# Set blazingly fast key repeat rate
defaults write NSGlobalDomain KeyRepeat -int 1
defaults write NSGlobalDomain ApplePressAndHoldEnabled -bool false

# Show battery percentage
defaults write com.apple.menuextra.battery ShowPercent -string "YES"

# Disable the Time Machine new disk requests dialog
defaults write com.apple.TimeMachine DoNotOfferNewDisksForBackup -bool true

# Require password 15 minutes after sleep or screen saver begins
defaults write com.apple.screensaver askForPasswordDelay -int 0

# Dock Size
defaults write com.apple.dock tilesize -int 48

# Show open indicators in Dock
defaults write com.apple.dock show-process-indicators -bool true

# Don’t automatically rearrange Spaces based on most recent use
defaults write com.apple.dock mru-spaces -bool false

# Auto hide the Dock
defaults write com.apple.dock autohide -bool true

# Finder: New window points to home
defaults write com.apple.finder NewWindowTarget -string "PfHm"

# Finder: show all filename extensions
# defaults write NSGlobalDomain AppleShowAllExtensions -bool true

# Finder: allow quitting via ⌘ + Q; doing so will also hide desktop icons
defaults write com.apple.finder QuitMenuItem -bool true

# Finder: disable window animations and Get Info animations
defaults write com.apple.finder DisableAllAnimations -bool true

# Finder: show path bar
defaults write com.apple.finder ShowPathbar -bool true

# When performing a search, search the current folder by default
defaults write com.apple.finder FXDefaultSearchScope -string "SCcf"

# Disable the warning when changing a file extension
defaults write com.apple.finder FXEnableExtensionChangeWarning -bool false

# Avoid creating .DS_Store files on network or USB volumes
defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool true
defaults write com.apple.desktopservices DSDontWriteUSBStores -bool true

# Enable snap-to-grid for icons on the desktop and in other icon views
/usr/libexec/PlistBuddy -c "Set :DesktopViewSettings:IconViewSettings:arrangeBy grid" ~/Library/Preferences/com.apple.finder.plist
/usr/libexec/PlistBuddy -c "Set :FK_StandardViewSettings:IconViewSettings:arrangeBy grid" ~/Library/Preferences/com.apple.finder.plist
/usr/libexec/PlistBuddy -c "Set :StandardViewSettings:IconViewSettings:arrangeBy grid" ~/Library/Preferences/com.apple.finder.plist

# Set grid spacing for icons on the desktop and in other icon views
/usr/libexec/PlistBuddy -c "Set :DesktopViewSettings:IconViewSettings:gridSpacing 100" ~/Library/Preferences/com.apple.finder.plist
/usr/libexec/PlistBuddy -c "Set :FK_StandardViewSettings:IconViewSettings:gridSpacing 100" ~/Library/Preferences/com.apple.finder.plist
/usr/libexec/PlistBuddy -c "Set :StandardViewSettings:IconViewSettings:gridSpacing 100" ~/Library/Preferences/com.apple.finder.plist

# Set the size of icons on the desktop and in other icon views
/usr/libexec/PlistBuddy -c "Set :DesktopViewSettings:IconViewSettings:iconSize 60" ~/Library/Preferences/com.apple.finder.plist
/usr/libexec/PlistBuddy -c "Set :FK_StandardViewSettings:IconViewSettings:iconSize 60" ~/Library/Preferences/com.apple.finder.plist
/usr/libexec/PlistBuddy -c "Set :StandardViewSettings:IconViewSettings:iconSize 60" ~/Library/Preferences/com.apple.finder.plist

# Use list view in all Finder windows by default
# Four-letter codes for the other view modes: `icnv`, `clmv`, `Flwv`
defaults write com.apple.finder FXPreferredViewStyle -string "Nlsv"

# Show the ~/Library folder
chflags nohidden ~/Library

# Show the /Volumes folder
sudo chflags nohidden /Volumes
```

## Make User Directories

```bash
mkdir ~/bin
mkdir ~/opt
mkdir ~/workspace
```

## Brew

### Install Brew

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
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
brew cask install iterm2
brew cask install sublime-text
brew cask install keepingyouawake
brew cask install java
brew cask install tunnelblick
```

### Python
```bash
brew install python
sudo easy_install pip
sudo pip install --upgrade pip
sudo pip install pyyaml
sudo pip install requests
sudo pip install ansible
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

### i2cssh

From https://github.com/wouterdebie/i2cssh

```bash
sudo gem install i2cssh
```

### Manual Install Apps
 - IntelliJ
 - MS Office (https://portal.office.com/)
 - iStats (https://bjango.com/mac/istatmenus/)
