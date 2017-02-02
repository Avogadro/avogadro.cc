---
layout: default
title: Building:Development Version
---

# Building:Development Version

Deprecated - please see updated instructions
============================================

The updated instructions are [here](Compiling_on_Linux_and_Mac_OS_X "wikilink"), the instructions on this page are out of date.

Building Source Code
====================

The following instructions are intended for users who wish to develop Avogadro. If you simply wish to build a copy of Avogadro for yourself, please see separate instructions for:

-   [Compiling on Windows](Compiling on Windows "wikilink")
-   [Compiling on Linux and Mac OS X](Compiling on Linux and Mac OS X "wikilink")

Linux
=====

These steps are designed to allow you build Avogadro without having to install ('make install') the dependencies. For the purposes of this example we check out all entries to $HOME/src.

Optional Development Tools
--------------------------

There are a few development tools you might like to use in order to make development a little easier and quicker. The first is [colorgcc](http://schlueters.de/colorgcc.html), which is a nice Perl script that adds some color to GCC output when compiling Avogadro. The second program you should really consider is [ccache](http://ccache.samba.org/), as developers we often recompile the same objects again and again. The ccache program can greatly increase the speed of recompilation by caching these object files.

Many Linux distributions will package these useful utilities and they can make both spotting the GCC errors, and recompilation, much faster. Assuming colorgcc has its symlinks in /usr/lib/colorgcc/bin/ and ccache has its in /usr/lib64/ccache/bin/ adding the following to your .bashrc will ensure they are both used. You must run CMake after these environment variables have been set to ensure they are used.

`<pre>export PATH="/usr/lib/colorgcc/bin/:/usr/lib64/ccache/bin/:${PATH}"</pre>`

Setting up the Environment
--------------------------

Avogadro searches relative to the binary location, and you can also set the environment variable AVOGADRO\_PLUGINS if you want to hard code the plugin directory location. By setting these environment variables OpenBabel will use special directories for runtime plugin loading. Avogadro will search the subdirectories colors, engines, extensions and tools for suitable plugins. The environment variables can point to multiple directories separated by colons, i.e. "$HOME/.avogadro/plugins:/usr/local/lib/avogadro".

Openbabel Formats `<pre>export BABEL_LIBDIR=$HOME/src/openbabel-2.2/src/formats/.libs:$HOME/src/openbabel-2.2/src/formats/xml/.libs</pre>`

Openbabel Data Files `<pre>export BABEL_DATADIR=$HOME/src/openbabel/data</pre>`

Dependencies
------------

[Git](http://git.or.cz/)
[CMake](http://www.cmake.org) (\>=2.6.2)
[Qt4](http://trolltech.com/products/qt) (\>=4.4.2)
[Eigen2](http://eigen.tuxfamily.org/) (\>=2.0.0)
[OpenBabel](http://www.openbabel.org/) (\>=2.2.1)  

### Building Eigen2 (Optional)

`<pre>
cd $HOME/src
svn co svn://anonsvn.kde.org/home/kde/trunk/kdesupport/eigen2 eigen2
</pre>`

### Building Openbabel (Optional)

This will build the TRUNK version of OpenBabel and allow you to use OpenBabel from the build directory rather than having to install it. `<pre>
cd $HOME/src
svn co https://openbabel.svn.sourceforge.net/svnroot/openbabel/openbabel/branches/openbabel-2-2-x openbabel-2.2
cd openbabel-2.2
./configure 
make -j3
</pre>`

Building Avogadro
-----------------

For more details on working with Git, GitHub and contibuting patches please see [Working\_With\_Git](Working_With_Git "wikilink").

`<pre>
cd $HOME/src
git clone git://github.com/cryos/avogadro.git
mkdir $HOME/build/avogadro
cd $HOME/build/avogadro
cmake \
  -DOPENBABEL2_INCLUDE_DIR=$HOME/src/openbabel-2.2/include \
  -DOPENBABEL2_LIBRARIES=$HOME/src/openbabel-2.2/src/.libs/libopenbabel.so \
  -DOPENBABEL2_VERSION_MET=true \
  -DEIGEN2_INCLUDE_DIR=$HOME/src/eigen2 \
  $HOME/src/avogadro
make -j3
</pre>`

Running
-------

`<pre>$HOME/build/avogadro/bin/avogadro</pre>`

