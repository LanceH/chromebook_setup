# chromebook_setup
Setting up Chromebook for Golang development

# Overview
This should cover the steps necessary to get any Chromebook ready for development using the Golang programming language.  This should also include other commonly used programs (git, editor, etc...).

# Platform
Toshiba Chromebook 2 (CB35-C3300) - it should work this way for most Chromebooks.

# Developer Mode
**This will reset the entire Chromebook.**  This shouldn't be a problem as it is all designed to save to cloud storage.  If you have anything in the Downloads directory, you should probably back that up first.

To put it into developer mode, simply hold `Power+Esc+Refresh` then let go of `Power`.  Refresh should be the the third button to the right of Esc and looks like a circular arrow.

You'll see a screen with a warning that "Chrome OS is missing or damaged."  This is normal.  Press `Ctrl-D`.

This brings up a new screen asking you "To turn OS verification OFF, press ENTER".  Press `ENTER` now to go into developer mode or `Esc` if you're having second thoughts.

The next screen will tell you that "OS verification is OFF".  It will beep with a warning and you have another opportunity to back out by pressing `SPACE`.  Wait it out and it will transition to developer mode.  This will take a while as local data will be cleared and everything gets reset.

When it finally comes back up, you'll be prompted for language, keyboard and network settings, just like when you first opened it.  It's still a Chromebook, so you'll need to log into Google like normal.

# Shell
To pull up a bash shell:
* Press `Ctrl-D` to pull up the Chrome OS
* Type `shell` at the command line and press enter

You should find yourself in a normal Bash shell.  

Oddly, you won't be in your own home directory.

```
chronos@localhost / $ cd ~
chromos@localhost ~ $ pwd
/home/chronos/user
```
It doesn't matter what user you're logging in as, you'll always see your home directory as `/home/chronos/user`.  Different users will both see their home directories by the same name, but they are different and don't share files.

# Installing Golang
Referencing: https://github.com/golang/go/wiki/ChromeOS

Synopsis for golang 1.5.3:
* Download `go1.5.3.linux-amd64.tar.gz` from https://golang.org/dl/
* ```sudo tar -C /usr/local -xzf ~/Downloads/go1.5.3.linux-amd64.tar.gz```

Test it:
```bash
chronos@localhost ~ $ /usr/local/go/bin/go version
go version go1.5.3 linux/amd64
```

Create a file in your Downloads directory named `gocode`.
```
mkdir ~/Downloads/gocode
```

Create a `tmp` directory which will be used when executing `go run`:
```
mkdir ~/tmp
```

Then add the following to your .bashrc file:
```
export PATH=$PATH:/usr/local/go/bin
export GOPATH=~/Downloads/gocode
export PATH=$PATH:$GOPATH/bin
export TMPDIR=~/tmp
sudo mount -i -o remount,exec /home/chronos/user/
```
The first three lines set up the normal paths required for GO to find executables and packages.  The TMPDIR variable is necessary when doing `go run` becaus the normal /tmp is mounted such that files can't be executed from there.  The fifth line remounts your home dir so that any files you build and store in your home directory can be executed.  Finally, we cd into the home directory for convenience sake.

Close your shell and open it again and everything should be in place.

# Installing Git (and Ruby)
Referencing: https://skycocker.github.io/chromebrew/

Using chromebrew:
```
wget -q -O - https://raw.github.com/skycocker/chromebrew/master/install.sh | bash
```
This will take a while as things are built and moved into place.  When is complete you should be able to use git and ruby.
```
chromos@localhost ~ $ git version
git version 1.8.4
chromos@localhost ~ $ ruby --version
ruby 2.0.0p247 (2013-06-27 revision 41674) [xo86_64-linux]
```

See what other packages are available with crew using `crew search`.

# Editors

For now, simply install [Caret](https://chrome.google.com/webstore/detail/caret/fljalecfjciodhpcledpamjachpmelml?hl=en) from the Google app store.  It is an online editor.  You will only be able to work with files in Google's cloud, or in your Downoad directory.  It will not be able to view your home directory or follow symlinks from the Downloads directory.

# Next Steps
At this point you should be ready to edit and run files in your `~/Downloads` directory.  This is a somewhat limited setup, but completely functional for golang development.

The next step would be installing [Crouton](https://github.com/dnschneid/crouton) which will make much more of linux available, including graphical applications.  In particular I'll want a more full editor for extended use.

Alternately, some people choose to dual boot linux, but that is something I can't explore simultaneously with my install of Crouton and will be left as an exercise for the reader.
