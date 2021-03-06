# bookshop Installer

bookshop development environment installer for Windows

## Overview

The goal of this project is to generate an installer that when run installs all
of the most common components for a bookshop development environment with no
required prerequisites on a Windows system.

## How to Contribute

bookshop Installer project code repository is located on GitHub and is bootstrapped,
built and packaged via rake tasks.

1. Download and install the latest
   [bookshop Installer](http://blueheadpublishing.github.com/bookshop/installer/)

1. Download and install latest
   [Inno Setup Quick Start Pack](http://www.jrsoftware.org/isdl.php#qsp),
   ensure iscc.exe is in your PATH

1. [Fork](http://help.github.com/fork-a-repo/)
   the [bookshop Installer project on github](https://github.com/blueheadpublishing/bookshopinstaller-windows.git)
   into your own github account

1. Open the bookshop Installer Command prompt from the start menu bookshop Installer
   group and change directories to where you like to keep your projects.

1. Clone your fork of the project

    > git clone git@github.com:{{your github user name}}/bookshopinstaller-windows

    > cd bookshopinstaller-windows

1. Update from origin master branch and checkout a new topic branch for
   your feature/bugfix.

    > git checkout master

    > git pull origin master

    > git checkout -b mybranchname

1. Bootstrap the project, from the project root run

    > rake bootstrap

1. Implement your new feature / fix your bug in the bookshopinstaller project code.
   Configuration of the packages are to be included are found in the
   config/bookshopinstaller.yml file. Building of the installer into the stage path
   for packaging happens from the Ruby code in the lib/ directory, starting from
   the file lib/bookshopinstaller/actions.rb. Methods called from actions
   file are implemented in lib/bookshopinstaller/methods.rb. In order to kick off a
   build into the stage/ directory run the following rake command.

1. Next build all components on the stage

    > rake build

1. We are now ready to package the installer for testing/distribution.
   Packaging of the installer from the stage path into an executable can be done
   via the following rake command. This creates the executable (.exe)
   package file in the pkg/ directory from the files staged during the
   build process in the stage/ directory.

     > rake package

1. Use Inno Setup to package bookshop Installer (NOTE that You can run the package
   task with --trace for debugging output if the package fails to build or if
   you simply want to see what is being done as it is done).

    > rake package

1. Once you have verified your Push your feature branch up to GitHub

    > git commit -a -m "Implemented featureX/bugfixX which <description>..."

    > git push origin mybranchname

1. Now issue a [pull request](http://help.github.com/pull-requests/) on GitHub

# bookshop Installer Components

The next few sections detail the core components that make up bookshop Installer.

### Ruby 1.8.7/1.9.2 on Windows

RubyInstaller is a self contained package installer which installs Ruby and
RubyGems on a windows system, head over to http://rubyinstaller.org/ for more
information.

### Development Kit (DevKit)

A MSYS/MinGW based toolkit that enables bookshop Installer to build native C/C++
packages, both for Ruby and gems. DevKit is built and maintained by the
wonderful folks over at the RubyInstaller (http://rubyinstaller.org/) project.

### Git

The git version that is bundled into bookshop Installer is
[msysgit](http://code.google.com/p/msysgit/)

### Packaging/Installer

We are using [Inno Setup](http://www.jrsoftware.org/isinfo.php "Inno Setup"),
a free installer for Windows programs.

