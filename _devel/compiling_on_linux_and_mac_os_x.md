---
layout: single
title: Compiling on Linux and Mac OS X
categories: Developer
---



These instructions are intended to help users and contributors build Avogadro from the latest code. Be aware that Avogadro may fail to build or work properly at any given time when built using the instructions below. For the adventurous, there are also [Windows Visual Studio 2008](Compiling_on_Windows "wikilink") instructions, although building on Windows is much more problematic.

Generally, if you do not need the latest Avogadro features and are not interested in developing Avogadro, you should first try the binary installers or packages available on the [download](:Get_Avogadro "wikilink") page. These are built using a released version of Avogadro which has received more testing than the current head of Git at any given moment.

Dependencies
------------

You should be able to find most of these dependencies in your distribution's repositories, or as binary downloads for Mac from the homepages linked below. Be careful to satisfy the version requirements.

[Git](http://git-scm.com) (optional, but recommended)
[CMake](http://www.cmake.org) (\>=2.6.0)
[Qt4](http://qt.nokia.com/products/) (\>=4.6.x)
[Eigen2](http://eigen.tuxfamily.org/) (\>=2.0) (more instructions [below](
[OpenBabel](http://openbabel.org/) (\>=2.3.0) (more instructions [below](

For the optional Python console/bindings:

[PyQt4](http://www.riverbankcomputing.co.uk/software/pyqt/download)
[SIP](http://www.riverbankcomputing.co.uk/software/sip/download)
[Boost](http://www.boost.org/users/download/)  

For optional OpenGL shader support:

[GLEW](http://glew.sourceforge.net/)  

Avogadro Squared
----------------

If you have [Git](http://git-scm.com) and [CMake](http://www.cmake.org/) installed, you can use the new "Avogadro Squared" build to fetch and build any needed dependencies.

` git clone --recursive `[`git://github.com/cryos/avogadro-squared.git`](git://github.com/cryos/avogadro-squared.git)
` mkdir avogadro-build`
` cd avogadro-build`
` cmake ../avogadro-squared`

Installing Eigen2
-----------------

You can obtain the [Eigen2 source here](http://bitbucket.org/eigen/eigen/get/2.0.15.tar.bz2).

Assuming you have the sources, it can be build and installed as follows:

`<pre>
cd eigen2
mkdir $HOME/build/eigen2
cd $HOME/build/eigen2
cmake $HOME/src/eigen2
make
sudo make install
</pre>`

**Note:** If you are either unable or do not want to install Eigen globally you can skip the final make install step.

Building OpenBabel
------------------

Avogadro makes heavy use of code and features from the [OpenBabel](http://openbabel.org) chemistry toolbox. Avogadro needs OpenBabel 2.2.3 or more recent (preferably 2.3.0). If your distribution does not have a sufficiently recent version you may obtain it using:

`<pre>
cd $HOME/src
svn co https://openbabel.svn.sourceforge.net/svnroot/openbabel/openbabel/branches/openbabel-2-3-x openbabel-2.3
</pre>`

Once you have the source code you can build it using: `<pre>
cd openbabel-2.3
./configure 
make -j2
sudo make install
</pre>`

**Note:** If you are either unable or do not want to install OpenBabel globally you can skip the final make install step.

Building Avogadro
-----------------

Avogadro uses Git for version control, with hosting provided by GitHub. If you would rather not install Git it is possible to download a tar or zip file containing the latest sources from [here](http://github.com/cryos/avogadro/). Click on the download link, unpack the file and adjust the instructions as necessary. It is generally a good idea to clone the repository if you intend to contribute or regularly build the latest sources. For more details about Git and Avogadro please see [Working\_With\_Git](Working_With_Git "wikilink").

`<pre>
cd $HOME/src
git clone git://github.com/cryos/avogadro.git
mkdir -p $HOME/build/avogadro
cd $HOME/build/avogadro
cmake $HOME/src/avogadro
make -j2
sudo make install
</pre>`

**Note:** If you are either unable or do not want to install Avogadro globally you can run in from your home directory using the following instructions. The instructions assume you have built Eigen and OpenBabel in your home directory too.

**Setting up the environment**

If you set these environment variables Avogadro and OpenBabel will use special directories for runtime plugin loading. Avogadro will search the subdirectories colors, engines, extensions and tools for suitable plugins. The environment variables can point to multiple directories separated by colons, i.e. "$HOME/.avogadro/plugins:/usr/local/lib/avogadro". All of them are optional, if they are installed then there is no need to set any environment variables.

`<pre>export AVOGADRO_TRANSLATIONS=$HOME/build/avogadro/avogadro/src                                       
export BABEL_LIBDIR=$HOME/src/openbabel/src/formats/.libs:$HOME/src/openbabel/src/formats/xml/.libs  
export BABEL_DATADIR=$HOME/src/openbabel/data                                                        

**Mac Specific Build Instructions**

If you would like to create binaries that will work on both Tiger and Leopard with both x86 and ppc Macs then the CMakeCache.txt in the build directory must contain,

    CMAKE_OSX_ARCHITECTURES:STRING=i386;ppc
    CMAKE_OSX_SYSROOT:PATH=/Developer/SDKs/MacOSX10.4u.sdk

You also need to export the environment variable to build for Tiger,

    export MACOSX_DEPLOYMENT_TARGET=10.4

**Building Avogadro**

These instructions assume that the OpenBabel sources are compiled in your home directory but not installed.

`<pre>
cd $HOME/src
git clone git://github.com/cryos/avogadro.git
mkdir -p $HOME/build/avogadro
cd $HOME/build/avogadro
cmake \
  -DOPENBABEL2_INCLUDE_DIR=$HOME/src/openbabel-2.2/include \
  -DOPENBABEL2_LIBRARIES=$HOME/src/openbabel-2.2/src/.libs/libopenbabel.so \
  -DOPENBABEL2_VERSION_MET=true $HOME/src/avogadro
make -j2
</pre>`

**Note:** Since compilation of translation files for all languages takes noticeable time, you may speed up build by choosing only one localization. To do it, append `-DI18N_LANGUAGE=your_language_code` to cmake command, e.g., `-DI18N_LANGUAGE=ru`

**Building Avogadro with Python Support**

To be able to access the python terminal within Avogadro, you will need to have boost python, python libraries, python interpreter, the numpy module, and the SIP module already installed on your computer. If you have all the required dependencies, the output when running cmake should be like:

`<pre>
...
-- [1/5] Boost Python
-- Boost Python found...
-- [2/5] Python Libraries
-- Found PythonLibs: /usr/lib/libpython2.6.so
-- [3/5] Python Interpreter
-- Found PythonInterp: /usr/bin/python2.6
-- [4/5] Numpy Module
-- Numpy headers found
-- [5/5] SIP Module
-- Found sip.h header...
-- using sip version 4.8 or above...
-- All python dependencies found - Python support enabled
...
</pre>`

To make sure that all the Python dependencies are fulfilled on Ubuntu you can use apt-get. Similar packages should be available from the repositories of other Linux flavors.

`<pre>
sudo apt-get install libboost-python-dev python-numpy-dev sip4
</pre>`

now all that is required is to run "make" and then "make install" according to the install instructions supplied with the source code. "make install" moves the Avogadro python module to the correct location. If you want to find the directory containing the python modules, you can always use this python script:

`<pre>
>>> from sys import stdout
>>> from distutils import sysconfig
>>> stdout.write(sysconfig.get_python_lib())
</pre>`

Running
-------

`<pre>avogadro</pre>` On Linux, if you installed Avogadro globally and you had Avogadro previously installed from repositories, you may need to execute `<pre>/usr/local/bin/avogadro</pre>` to run new version. However, it's recommended to uninstall `avogadro` package before installation from sources to prevent collisions. On Mac OS X Avogadro will be in your Applications folder, or you can run it from the build directory inside the bin folder.

**Note:** If you have built Avogadro using the directions in the previous section then run Avogadro using: `<pre>$HOME/build/avogadro/bin/avogadro</pre>`



