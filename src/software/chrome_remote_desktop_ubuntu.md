# Setting up Chrome Remote Desktop on Ubuntu

## Updates

I have been informed of two other solutions. Most recently,
[this comment](https://aur.archlinux.org/packages/chrome-remote-desktop/#comment-719586) appears to describe a better
process more directly supported by Google. In the past I was also pointed to
[this askubuntu question](https://askubuntu.com/questions/795703) which appears to have a better (shorter, headless)
solution than what I describe here. I have not personally tested either of these, but I recommend starting there.

This was written in September of 2015. Not sure whether it still applies.

## Sources

The upstream documentation is a little bit scattered, not always entirely complete, and the Ubuntu package provided
needs some poking to work. Hence this summary.

The two main sources of information I found are:

- An old product forum post: <https://productforums.google.com/forum/#!topic/chrome/8PMxG69VJ6o>
- This documentation (under \"Enable remote access to your computer\"):
  <https://support.google.com/chrome/answer/1649523?hl=en>

## Overview of how remote-desktop works

The Linux version of chrome remote desktop (henceforth, CRD) doesn\'t allow clients to connect and control an existing X
session; rather, there is a dedicated X session specific to CRD. This is similar to the classic vncserver mechanic. When
you connect, a session is started if one is not already running. If it is running, you are connected to the in-progress
session.

Initial setup still requires a non-headless environment: A running Chrome (until someone or Google makes a tool that
generates the necessary on-disk state in your home directory for authorizing remote access).

Once set up however, CRD is completely headless and is controlled using an init script. For example:

    sudo /etc/init.d/chrome-remote-desktop restart

It determines which users should have CRD running based on which users are part of the `chrome-remote-desktop` Unix
group.

## Why Chrome Remote Desktop instead of `$OTHER_OPTION`?

Mostly:

- It works natively on ChromeOS, and works well. It handles hi-dpi displays correctly, and passes through keyboard
  combinations correctly (e.g., it stops CTRL-N from opening a new local window).
- It seems faster than any other remote desktop option I have tried. I don\'t know technical details, but likely their
  use of some kind of modified VP9 codec has to do with this. When originally writing this I thought it was lossy and
  pixel perfect nonetheless, but I\'ve been informed it\'s not. At least it was good enough to fool me :)

## Setup instructions

### Install the package

Download the package linked from <https://support.google.com/chrome/answer/1649523?hl=en> and install it:

    sudo dpkg -i chrome-remote-desktop_current_amd64.deb
    sudo apt-get -f install

### Prepare the chrome-remote-desktop group

At the time of this writing, the package installer seems to fail to create the `chrome-remote-desktop` group, so add it:

    sudo groupadd chrome-remote-desktop

You may need to add yourself to the group (unclear if this happens correctly automatically):

    sudo usermod -a -G chrome-remote-desktop $USER

### Set up the desktop session

If `~/.chrome-remote-desktop-session` is missing or contains bad information, the attempt to connect to the remote
desktop will fail without a clear cause. Example:

    #!/bin/bash

    xterm &
    exec i3

Unconfirmed whether `chmod +x` is needed.

### Set up your desired resolution in your shell profile

Wherever your shell profile is, add an appropriate resolution selection:

    export CHROME_REMOTE_DESKTOP_DEFAULT_DESKTOP_SIZES=1024x768

### Bootstrap through SSH+VNC

On the server:

    sudo apt-get install vnc4server
    vncpasswd
    vncserver

    # log in remotely and bootstrap chrome (see later)

    vncserver -kill :1

On the client, log into the server using a VNC client over SSH forwarding. I.e:

    ssh -L 5901:localhost:5901 username@remotehost

And run your preferred VNC client to connect to `localhost:5901`.

### Enable remote connections in Chrome

Start Chrome, install the \"Chrome Remote Desktop\" app, run it. Under \"My Computers\", hit \"Enable remote
connections\".

Hopefully it should succeed. After this, the session will automatically start on boot thanks to the init script, and
chrome will have directly launched a session for you just now - so you should now be able to connect through a CRD
client.
