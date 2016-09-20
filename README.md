# Setup OSX

## Hostname

sudo scutil --set HostName [NewHostNameHere]

## Java

### Java 6

Download from http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase6-419409.html
Installed to /Library/Java/JavaVirtualMachines
ln -s <version> jdk6

To use:
export $JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk6/Contents/Home

### Java 7

Download from http://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase7-521261.html
Installed to /Library/Java/JavaVirtualMachines
ln -s <version> jdk7

To use:
export $JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk6/Contents/Home

### Java 8

Download from http://www.oracle.com/technetwork/java/javase/downloads/java-archive-javase8-2177648.html
Installed to /Library/Java/JavaVirtualMachines
ln -s <version> jdk8

To use:
export $JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk6/Contents/Home

## Maven

### Maven 2

Install to ~/opt
ln -s <version> mvn2
ln -s ~/opt/mvn2 ~/bin/mvn2

### Maven 3

Install to ~/opt
ln -s <version> mvn3
ln -s ~/opt/mvn3 ~/bin/mvn3

## Python
