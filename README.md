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

You should find yourself in a normal Bash shell.  Oddly, you won't be in your own home directory.
