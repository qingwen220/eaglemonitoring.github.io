---
layout: doc
title:  "How to Setup Apache Eagle (incubating) Development Environment on Mac OSX"
permalink: /docs/development-in-macosx.html
---

How to Setup Apache Eagle (incubating) Development Environment on Mac OSX
-----------------------------------------------------

*Apache Eagle (incubating) will be called Eagle in the following.*  
This tutorial is based `Mac OS X`. It can be used as a reference guide for other OS like Linux or Windows as well.  To save your time of jumping back and forth between different web pages, all necessary references will be pointed out. 

### Prerequisite

* __HomeBrew__
  
Make sure you have HomeBrew installed on your mac. If not, please run:

    $ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

  you can find more information about HomeBrew at http://brew.sh/ .

* __Scala & SBT__

Some core eagle modules are written with scala. To install Scala and SBT, just run:

     $ brew install scala
     $ brew install sbt

* __NPM__

Eagle-webservice module uses npm. To install it, run:

     $ brew install npm

* __Apache Maven__

Eagle is built with maven:
 
     $ brew install maven

* HomeBrew Cask 

    - Install HomeBrew Cask:
      
          $ brew install caskroom/cask/brew-cask
          
    - Next, install JDK via HomeBrew:

        $ brew cask search java


you will see all available JDK versions and you can install multiple JDK versions in this way. For eagle please choose java7 to install:

     $ brew cask install java7


**Note:**
- During this writing SBT has issue with JDK 8. This issue has been tested confirmed by using: 
- Java 1.8.0_66
- Maven 3.3.9
- Scala 2.11.7
- Sbt 0.13.9

you can find more information about HomeBrew Cask at [http://caskroom.io](http://caskroom.io)

* Jenv 

you can use Jenv to manage installed multiple Java versions. To install it:

    $ brew install https://raw.githubusercontent.com/entrypass/jenv/homebrew/homebrew/jenv.rb

and make sure activate it automatically:

    $ echo 'eval "$(jenv init -)"' >> ~/.bash_profile


**Note:**
- There is a known issue at this writing: https://github.com/gcuisinier/jenv/wiki/Trouble-Shooting
- Please make sure JENV_ROOT has been set before jenv init:
- $ export JENV_ROOT=/usr/local/opt/jenv

Now let Jenv manage JDK versions (remember In OSX all JVMs are located at /Library/Java/JavaVirtualMachines):

    $ jenv add /Library/Java/JavaVirtualMachines/jdk1.8.0_66.jdk/Contents/Home/
    $ jenv add /Library/Java/JavaVirtualMachines/jdk1.7.0_80.jdk/Contents/Home/

and

    $ jenv rehash

You can see all managed JDK versions:

    $ jenv versions

set global java version:

    $ jenv global oracle64-1.8.0.66

switch to your eagle home directory and set the local JDK version for eagle:

    $ jenv local oracle64-1.7.0.80

you can find more information about Jenv at https://github.com/rbenv/rbenv and http://hanxue-it.blogspot.com/2014/05/installing-java-8-managing-multiple.html.

### How to Build Eagle


Go to Eagle home directory and run:

    mvn -DskipTests clean package

That's all. Now you have runnable eagle on your Mac. Have fun. :-)
