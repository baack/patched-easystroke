# patched_easystroke

A patched version of [Easystroke](https://github.com/thjaeger/easystroke), the currently unmaintained, yet [still awesome](https://www.youtube.com/watch?v=sOWXAyOde18) interface for gesture control. Though the patch was originally suggested in a Arch Linux forum, it was able to make it work on Subgraph Aaron, a Debian Stretch based distro. So, if the OP version isn't able to run on your computer, then I invite you to try this one.

The build instructions below were taken from the OP's wiki for [Easystroke](https://github.com/thjaeger/easystroke/wiki/BuildInstructions), and has some minor modifications for the sake of context. Though I must warn you, I've not tested the installation process any other OS besides Subgraph.

## Build instructions

Easystroke is written in C++ and uses gtkmm for its GUI, but it also depends on the availability of several X11 extensions (Xtst, Xrandr and Xinput) and on the boost::serialization library. Installation of the libraries is distribution-specific. Please feel free to add instructions for your distro of choice.

### Dependencies

**Debian/Ubuntu**
```
sudo apt-get install g++ libboost-serialization-dev libgtkmm-3.0-dev libxtst-dev libdbus-glib-1-dev intltool xserver-xorg-dev
```

**Fedora**
```
yum install gcc-c++ gtkmm24-devel dbus-glib-devel boost-devel libXtst-devel intltool
```
> Note: You might have to install 'xorg-x11-server-devel' for easystroke to compile, probably (I had to).

**OpenSUSE**
```
zypper in make gcc gcc-c++ gtkmm2-devel glib2-devel dbus-1-glib-devel boost-devel intltool
```
> Note: You might have to install 'xorg-x11-server-sdk' to successfully build on 12.X.

**Pardus**
```
pisi it make gcc  gtkmm boost-devel intltool
```
> Note: For Pardus, you also have to add -lXi to the LIBS row in the Makefile in order to get the app to compile.

### Building

Easystroke uses git for revision control. To fetch the development tree for the first time, type
```
git clone git://gitlab.com/hThoreau/patched_easystroke.git
```
which will create a subdirectory 'easystroke' containing the sources. You can update to the latest tree anytime by changing into that directory and typing 'git pull'.

Now we're ready to build the program. Change into the easystroke directory and type 'make -j2'. This will create an executable file that you can either run directly or copy into your $PATH (easystroke does not require additional files to be installed), but of course you can also use 'make install' to install the program to /usr/local/bin. You can also create a small manpage using help2man by typing 'make man'.
