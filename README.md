Set up your Stackato Development Environment
============================================

This document will help you install your development environment for working with Stackato.

# Install Ubuntu

First, install Ubuntu 12.04 LTS (64 bit if you can, otherwise 32 bit):

      http://www.ubuntu.com/download/desktop

Documentation on dual-booting linux + Windows:

    https://help.ubuntu.com/community/WindowsDualBoot

If you want Mac + linux, I'd highly recommend using something called rEFIt:

    http://refit.sourceforge.net/

# Prepare your development environment

There's a script I made to help get my development started for this. It's
hosted on Github Gists, which is a way for creating and sharing snippets
of code:

    https://gist.github.com/bacongobbler/5747364

Feel free to take out any packages you won't need. This is for my environment.
If you don't need [golang](http://golang.org/) because you're not making an
application in Go, then go nuts, copy and paste the script, and remove 'golang'
from the packages list.

Some packages that are mandatory are:

    virtualbox virtualbox-dkms virtualbox-qt curl

This sets up Virtualbox on Ubuntu. Curl is just a really handy tool for doing
cool stuff like this:

    curl "http://cowsay.morecode.org/say?format=text&message=hello"

or, if someone has a script online, like say on a github gist...

    # run the install.sh script hosted on github!
    curl https://gist.github.com/bacongobbler/5747364/raw/63593b170f4cafda09db676e960deae4f72750b1/install.sh | sudo bash

Be sure to restart your computer afterwards, as virtualbox-dkms compiles a couple modules for Virtualbox to run properly.

## Text Editor

You're free to use any text editor you wish. However, I have fallen in love with Sublime Text.
It's free, and it can be found [here](http://www.sublimetext.com/). Or, you can just run the
script listed above and it will install it for you =)

# Install Stackato

Get the Stackato client and the server from [ActiveState's downloads page](http://downloads.activestate.com/).
I recommend this link so you won't get any pesky marketing emails from us, as compared to if you try to
download from [here](http://www.activestate.com/stackato/download_vm).

## Server

Once you're done that, follow through these steps:

 * open up virtualbox
 * press CTRL + I to "Import Appliance"
 * Go through the steps, click ok
 * Open the imported box's settings (CTRL + S)
 * Set the network type to Bridged on eth0 (or wlan0 if you're on a wireless network)
 * Fire up the VM

## Client

It's pretty simple, really... no dependencies required to install!

    # Download the Stackato Client from our downloads page
    wget http://downloads.activestate.com/stackato/client/v1.7.4/stackato-1.7.4-linux-glibc2.3-x86_64.zip
    # unzip the file, then delete it
    unzip stackato-1.7.4-linux-glibc2.3-x86_64.zip && rm stackato-1.7.4-linux-glibc2.3-x86_64.zip
    # move the Stackato client somewhere reasonable, like /usr/bin
    sudo mv stackato-1.7.4-linux-glibc2.3-x86_64/stackato /usr/bin
    # create a symbolic link to the Stackato client for ease of use
    sudo ln -s /usr/bin/stackato /usr/bin/st
    # remove the folder we no longer need
    rm -rf stackato-1.7.4-linux-glibc2.3-x86_64

After it's been installed, test if it's working...

    stackato help

You're good to go!
