---
layout: default
title: Compiling on Windows with MSVC 2008
categories: Developer
---



These instructions are to allow users to build Avogadro from the very latest code. Be aware that Avogadro may fail to build or work properly at any given time when built from the instructions below.

Compiling Avogadro for Windows is a complex task and it is recommended that you download the pre-made installer found on the download page. For the adventurous, here are Windows Visual Studio 2008 instructions that may or may not work. For various steps in the process, there may be downloadable binaries on the web. However, for completeness we build all dependencies.  

There are also [instructions for Linux and Mac OS X](Compiling_on_Linux_and_Mac_OS_X "wikilink") available.

DebugView
=========

[DebugView](http://technet.microsoft.com/en-us/sysinternals/bb896647.aspx) is a small program that allows you to view qDebug() output.

Windows Visual Studio 2008 (Express)
====================================

NOTE: The redistributable manifest and the version Avogadro compile against do not match. This means that the redistributable's manifest must be altered in order to successfully use the redistributable DLLs. Go to "C:\\Program Files\\Microsoft Visual Studio 9.0\\VC\\redist\\x86\\Microsoft.VC90.CRT" and edit the file called "Microsoft.VC90.CRT.manifest". I used the version string,

    version="9.0.21022.8"

After I changed that then the DLLs were successfully loaded and the mysterious error message stopped popping up. This was with the standard "free" version downloaded in January 2009.

Dependencies
------------

Required:

[CMake](http://www.cmake.org) (\>=2.6.0)
[Qt4](
[Eigen](
[OpenBabel](

For optional OpenGL shader support:

[GLEW](http://glew.sourceforge.net/)  

For the optional Python console/bindings:

[PyQt4](http://www.riverbankcomputing.co.uk/software/pyqt/download)
[SIP](http://www.riverbankcomputing.co.uk/software/sip/download)
[Boost libraries](http://www.boostpro.com/products/free) (tested with \>=1.36.0, older versions likely work fine)
[Boost](http://www.boost.org/users/download/)  



The instructions below are based on [Qt4 with Visual Studio](http://wiki.qtcentre.org/index.php?title=Qt4_with_Visual_Studio). Extract and build Qt4 in the C:\\src\\qt-\<version\> directory (e.g. C:\\src\\qt-4.5.1 for version 4.5.1).

Compiling Qt takes some time and can require +10GB free disk space. Below are some options to run configure.exe that reduce compile time and disk space requirements.

`-release or -debug : default is -debug-and-release which takes more disk spcace.`
`Unused (by Avogadro) Qt components:`
`-no-webkit`
`-no-phonon`
`-no-phonon-backend`
`-no-qt3support`

A full compile & installation could look like (in command prompt):

`cd c:\src\qt-4.5.1`
`configure.exe -opensource -no-webkit -release `
`...`
`Do you accept the terms of the license?`
`y`
`nmake`
`nmake install`

-   Add C:\\src\\qt-4.5.1\\lib to your PATH. (Control Panel-\>System-\>Advanced Tab-\>Environment Variables)
-   Make sure qmake.exe is somewhere in your PATH (needed to build PyQt)



Download [Eigen 2 here](http://eigen.tuxfamily.org). There is no need to build Eigen since it's a template library consisting of headers only. We simply extract the files to C:\\src\\eigen-2.0.1. You should now have the Eigen headers in C:\\src\\eigen-2.0.1\\Eigen





-   Download [zetlib123.zip here](http://www.winimage.com/zLibDll/)
-   Extract to C:\\src\\zlib-1.2.3
-   Open C:\\src\\zlib-1.2.3\\projects\\visualc6\\zlib.sln (**note:** This will convert the VC6.0 solution...)
-   Select the **DLL Release** configuration
-   Build (F7)

The zlib library files are now in C:\\src\\zlib-1.2.3\\projects\\visualc6\\Win32\_DLL\_Release. The zlib.h header file is in C:\\src\\zlib-1.2.3.



-   Download [libxml2-sources-2.7.3.tar.gz here](ftp://xmlsoft.org/libxml2/)
-   Extract to C:\\src\\libxml2-2.7.3
-   In command prompt:
      
    cd c:\\src\\libxml2-2.7.3\\win32

    cscript configure.js compiler=msvc prefix=c:\\local\\libxml2 iconv=no zlib=yes include=c:\\src\\zlib-1.2.3 lib=c:\\src\\zlib-1.2.3\\projects\\visualc6\\Win32\_DLL\_Release

-   Edit Makefile.msvc: change "zdll.lib" to "zlib1.lib"
-   In command prompt again:
      
    nmake /f Makefile.msvc

    nmake /f Makefile.msvc install



Although boost is an optional dependency for OpenBabel, it is recommended to compile with boost. OpenBabel only needs headers from the boost libraries and extracting the source package to C:\\src is enough for now. If you intend to build Avogadro with python support you need build boost python later (see below).



Download openbabel 2.2.1 if you haven't already and extract it to C:\\src



Since we are using cmake 2.6, the installed [boost libraries](http://www.boostpro.com/products/free) will be found automatically. If you downloaded the boost source, make sure to also set Boost\_INCLUDE\_DIR. OpenBabel only uses headers from boost, there is no need to compile any boost libraries before building OpenBabel.

`cd c:\openbabel`
`mkdir build`
`cd build`
`cmake -DCMAKE_BUILD_TYPE="Release" -DZLIB_INCLUDE_DIR=c:\openbabel\include -DZLIB_LIBRARY=c:\openbabel\windows-vc2005\zlib1.lib`
`-DLIBXML2_INCLUDE_DIR=c:\openbabel\include -DLIBXML2_LIBRARIES=c:\openbabel\windows-vc2005\libxml2.lib `
`-DLIBRARY_OUPUT_PATH=c:\openbabel\output -DEXECUTABLE_OUPUT_PATH=c:\openbabel\output -G "Visual Studio 9 2008" ..`



![openbabel CMake 2.6 setting for windows](Cmake.jpg "openbabel CMake 2.6 setting for windows")

1.  Open the CMake GUI: Start \> All programs \> CMake 2.6 \> cmake-gui(beta)
2.  Set the "Where is the source code" field to C:/openbabel
3.  Set the "Where to build the binaries" field to C:/openbabel/build
4.  Press the "Configure" button
5.  A new dialog will appear where you can select the build environment: Visual Studio 9 2008
6.  Set the combo box (on the right of the search field) to "Grouped View"
7.  Edit the ZLIB and LIBXML2 fields so they resemble the screenshot



1.  Open the C:\\openbabel\\build\\openbabel.sln solution
2.  Select the **Release** solution configuration.
3.  Build the Solution (F7)

You should now have all files files in C:\\openbabel\\output\\Release.

Building Avogadro
-----------------

For a minimal build (no python & GLSL shaders), you can now proceed to build Avogadro. If you want python and/or GLSL shader support, build these dependencies first and come back to this step later.

Download Avogadro [trunk](http://github.com/cryos/avogadro/zipball/master) or [a stable version](http://github.com/cryos/avogadro/doawnloads) and uncompress it to the C:\\src\\avogadro directory.

-   Edit the scripts\\cmake-msvc2008.bat file to make sure all paths are correct.
-   Open the Visual Studio 2008 Command Prompt.

`cd C:\src\avogadro`
`mkdir build`
`cd build`
`..\scripts\cmake-msvc2008.bat`
`nmake`

Running Avogadro & Building the Installer
-----------------------------------------

The easiest way to run avogadro is to build a binary zip file or [NSIS installer](http://nsis.sourceforge.net).

If you have set the CPACK\_BINARY\_ZIP or CPACK\_BINARY\_NSIS variable when running cmake (see scripts/cmake-msvc2008.bat), all you have to do is:

-   In command prompt:

`nmake PACKAGE`

This will generate a zip file or .exe installer in your build dir. Simply extract or install and run avogadro.exe.

GLSL Shader Support (Optional)
------------------------------

-   GLEW-1.5.1: <http://ovh.dl.sourceforge.net/sourceforge/glew/glew-1.5.1-src.zip>
-   Extract to C:\\src
-   Open C:\\src\\glew\\build\\vc6\\glew.sln (**note:** This will convert the VC6.0 solution...)
-   Select **Release** configuration
-   Build the **glew\_shared** target

Python Support (Optional)
-------------------------



-   Python 2.6.2: <http://www.python.org/ftp/python/2.6.2/Python-2.6.2.tar.bz2>
    -   Extract to C:\\src
    -   Open c:\\src\\Python-2.6.2\\PCbuild\\pcbuild.sln (**note:** when using VC++ 2008 express, you'll get an error message saying "solution folders" aren't supported. You can safely ignore this.)
    -   Select **Release**
    -   Build (F7)
    -   You now have the files in the PCBuild directory
    -   Copy the exe, lib, dll & pyd files to c:\\src\\Python-2.6.2\\libs
    -   Copy C:\\src\\Python-2.6.2\\PC\\pyconfig.h to C:\\src\\Python-2.6.2\\Include

Some targets (7 for 2.6.2) fail because they need additional libraries (encryption, sqlite3, ...). This is not a problem since we don't use these parts.



-   bjam precompiled: <http://sourceforge.net/project/showfiles.php?group_id=7586&package_id=72941>
    -   place bjam.exe in a directory in your PATH (e.g. C:\\Windows) (**note:** typing PATH at the MSVC command prompt show your current PATH values)
-   boost libraries (1.38): <http://sourceforge.net/project/showfiles.php?group_id=7586&package_id=8041>
    -   Extract to C:\\src
    -   Edit C:\\src\\boost\_1\_38\_0\\tools\\build\\v2\\user-config.jam
    -   Add (at the end for example):

`using python`
`  : 2.6`
`  : C:/src/Python-2.6.2/libs/python 
`  : C:/src/Python-2.6.2/Include     
`  : C:/src/Python-2.6.2/libs ;      

In command promt:

`cd C:\src\boost_1_38_0`
`mkdir build`
`bjam --build-dir="build" --toolset=msvc --with-python stage`

You now have the following files in **$BOOST\_ROOT/stage/lib**:

`boost_python-vc90-mt.lib               185kB`
`boost_python-vc90-mt-1_38.dll          210kB`
`boost_python-vc90-mt-1_38.lib          185kB  
`libboost_python-vc90-mt.lib            5173kB `
`libboost_python-vc90-mt-1_38.lib       5173kB 

Copy the files above to **$BOOST\_ROOT/lib**, the CPack script expects to find them there



-   <http://www.riverbankcomputing.co.uk/static/Downloads/sip4/sip-4.7.9.zip>
    -   Extract to C:\\src

In command prompt:

`cd c:\src\sip-4.7.9`
`C:\src\Python-2.6.2\libs\python.exe configure.py`
`nmake`

You now have these files:

`C:\src\sip-4.7.9\sipconfig.py`
`C:\src\sip-4.7.9\siplib\sip.h`
`C:\src\sip-4.7.9\siplib\sip.pyd`
`C:\src\sip-4.7.9\siplib\sip.pyd.manifest`
`C:\src\sip-4.7.9\sipgen\sip.exe`
`C:\src\sip-4.7.9\sipgen\sip.exe.manifest`

-   Copy **sipconfig.py**, **sip.pyd** and **sip.pyd.manifest** to C:\\src\\Python-2.6.2\\lib\\site-packages\\
-   Copy file **sip.h** to C:\\src\\Python-2.6.2\\Include
-   Copy files **sip.exe** and **sip.exe.manifest** to C:\\src\\Python-2.6.2

Notes:

-   sip.exe[.manifest] is only needed to build PyQt4, no need to include it in the installer
-   sip.h is also needed to build Avogadro



Assumes Qt is in C:\\Qt\\4.4.3, change this if needed...

-   PyQt4 4.4.4: <http://www.riverbankcomputing.co.uk/static/Downloads/PyQt4/PyQt-win-gpl-4.4.4.zip>
    -   Extract to C:\\src

In command prompt:

`cd C:\src\PyQt-win-gpl-4.4.4`
`mkdir release`
`copy C:\Qt\4.4.3\lib\QtCore4.dll release\QtCore4.dll`
`C:\src\Python-2.6.2\libs\python.exe configure.py`
`nmake`

You now have the .pyd files and their manifests in the Qt\* dirs:

`C:\src\PyQt-win-gpl-4.4.4\Qt\Qt.pyd(.manifest)`
`C:\src\PyQt-win-gpl-4.4.4\QtCore\QtCore.pyd(.manifest)`
`C:\src\PyQt-win-gpl-4.4.4\QtGui\QtGui.pyd(.manifest)`
`C:\src\PyQt-win-gpl-4.4.4\QtOpenGL\QtOpenGL.pyd(.manifest)`
`...`

You can leave the files there, the CPack script will include them in the package.



-   Numpy 1.3.0: <http://kent.dl.sourceforge.net/sourceforge/numpy/numpy-1.3.0.tar.gz>
    -   Extract to C:\\src

In command prompt:

`cd c:\src\numpy-1.3.0`
`c:\src\Python-2.6.2\libs\python.exe setup.py install`

This will install numpy to the **C:/src/Python-2.6.2/lib/site-packages** directory

numpy/arrayobject.h is in **C:/src/Python-2.6.2/lib/site-packages/numpy/core/include** (You'll need this to build Avogadro)



