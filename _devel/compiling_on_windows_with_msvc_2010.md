---
layout: single
title: Compiling on Windows with MSVC 2010
categories: Developer
---



These instructions are to allow users to build Avogadro from the very latest code. Be aware that Avogadro may fail to build or work properly at any given time when built from the instructions below.

Compiling Avogadro for Windows is a complex task and it is recommended that you download the pre-made installer found on the download page. For the adventurous, here are Windows Visual Studio 2010 instructions that may or may not work. For various steps in the process, there may be downloadable binaries on the web. However, for completeness we build all dependencies.  

There are also [instructions for Linux and Mac OS X](Compiling_on_Linux_and_Mac_OS_X "wikilink") available.

DebugView
=========

[DebugView](http://technet.microsoft.com/en-us/sysinternals/bb896647.aspx) is a small program that allows you to view qDebug() output.

Windows Visual Studio 2010 (Express)
====================================

NOTE April 2011: Python 2.7.x can't be build using version 10, these instructions are for avogadro without python support.  

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



The instructions below are based on [Qt4 with Visual Studio](http://wiki.qtcentre.org/index.php?title=Qt4_with_Visual_Studio). Extract and build Qt4 in the C:\\src\\qt-\<version\> directory (e.g. C:\\src\\qt-4.7.2 for version 4.7.2).

Compiling Qt takes some time and can require +10GB free disk space. Below are some options to run configure.exe that reduce compile time and disk space requirements.

`-release or -debug : default is -debug-and-release which takes more disk spcace.`
`Unused (by Avogadro) Qt components:`
`-no-webkit`
`-no-phonon`
`-no-phonon-backend`
`-no-qt3support`

A full compile & installation could look like (in command prompt):

`cd c:\src\qt-4.7.2`
`configure.exe -opensource -no-webkit -release `
`...`
`Do you accept the terms of the license?`
`y`
`nmake`
`nmake install`

-   Add C:\\src\\qt-4.7.2\\lib to your PATH. (Control Panel-\>System-\>Advanced Tab-\>Environment Variables)
-   Make sure qmake.exe is somewhere in your PATH (needed to build PyQt)



Download [Eigen 2 here](http://eigen.tuxfamily.org). There is no need to build Eigen since it's a template library consisting of headers only. We simply extract the files to C:\\src\\eigen-2.0.15. You should now have the Eigen headers in C:\\src\\eigen-2.0.15\\Eigen





-   Download [zlib-1.2.5.zip here](http://www.winimage.com/zLibDll/)
-   Extract to C:\\src\\zlib-1.2.5
-   In the command prompt:

`cd c:\src\zlib-1.2.5`
`mkdir build`
`cd build`
`del ..\zconf.h`
`cmake -DCMAKE_BUILD_TYPE=Release ..`
`nmake`
`copy zconf.h ..`

The zlib library files are now in C:\\src\\zlib-1.2.5\\build. The zlib.h header file is in C:\\src\\zlib-1.2.5.



-   Download [libxml2-sources-2.7.7.tar.gz here](ftp://xmlsoft.org/libxml2/)
-   Extract to C:\\src\\libxml2-2.7.7
-   In command prompt:

`cd c:\src\libxml2-2.7.7\win32`
`cscript configure.js compiler=msvc prefix=c:\src\libxml2 iconv=no zlib=yes include=c:\src\zlib-1.2.5 lib=c:\src\zlib-1.2.5\build`

-   Edit Makefile.msvc
    -   line 75: remove /OPT:NOWIN98
    -   line 94: change "zdll.lib" to "zlib.lib"
-   In command prompt again:

`nmake /f Makefile.msvc`
`nmake /f Makefile.msvc install`



Although boost is an optional dependency for OpenBabel, it is recommended to compile with boost. OpenBabel only needs headers from the boost libraries and extracting the source package to C:\\src is enough for now. If you intend to build Avogadro with python support you need build boost python later (see below).



Download openbabel 2.3.0 if you haven't already and extract it to C:\\src



Since we are using cmake 2.6, the installed [boost libraries](http://www.boostpro.com/products/free) will be found automatically. If you downloaded the boost source, make sure to also set Boost\_INCLUDE\_DIR. OpenBabel only uses headers from boost, there is no need to compile any boost libraries before building OpenBabel.

First, copy the contents of C:\\openbabel-2.3.0\\windows-vc2008\\include to C:\\openbabel-2.3.0\\include.

`cd c:\openbabel-2.3.0`
`mkdir build`
`cd build`
`cmake -DCMAKE_BUILD_TYPE=Release -DZLIB_INCLUDE_DIR=c:\src\zlib-1.2.5 -DZLIB_LIBRARY=c:\src\zlib-1.2.5\build\zlib.lib`
`    -DLIBXML2_INCLUDE_DIR=c:\src\libxml2\include -DLIBXML2_LIBRARIES=c:\src\libxml2\lib\libxml2.lib `
`    -DXDR_LIBRARY=C:\src\openbabel-2.3.0\windows-vc2008\libs\i386\xdr.lib -DCMAKE_INSTALL_PREFIX=c:\src\openbabel `
`    -G "NMake Makefiles" ..`
`nmake`
`nmake install`

You should now have the library files in C:\\src\\openbabel\\bin. The include path is C:\\src\\openbabel\\include\\openbabel-2.0.

Building Avogadro
-----------------

For a minimal build (no python & GLSL shaders), you can now proceed to build Avogadro. If you want python and/or GLSL shader support, build these dependencies first and come back to this step later.

Download Avogadro [trunk](http://github.com/cryos/avogadro/zipball/master) or [a stable version](http://github.com/cryos/avogadro/doawnloads) and uncompress it to the C:\\src\\avogadro directory.

-   Edit the scripts\\cmake-msvc2010.bat file to make sure all paths are correct.
-   Open the Visual Studio 2010 Command Prompt.

`cd C:\src\avogadro`
`mkdir build`
`cd build`
`..\scripts\cmake-msvc2010.bat`
`nmake`

Running Avogadro & Building the Installer
-----------------------------------------

The easiest way to run avogadro is to build a binary zip file or [NSIS installer](http://nsis.sourceforge.net).

If you have set the CPACK\_BINARY\_ZIP or CPACK\_BINARY\_NSIS variable when running cmake (see scripts/cmake-msvc2008.bat), all you have to do is:

-   In command prompt:

`nmake PACKAGE`

If there are any errors, check the cmake/modules/AvoCPack.cmake file in the avogadro directory and ensure that all paths are correct.

This will generate a zip file or .exe installer in your build dir. Simply extract or install and run avogadro.exe.

GLSL Shader Support (Optional)
------------------------------

-   GLEW-1.5.1: <http://ovh.dl.sourceforge.net/sourceforge/glew/glew-1.5.1-src.zip>
-   Extract to C:\\src
-   Open C:\\src\\glew\\build\\vc6\\glew.sln (**note:** This will convert the VC6.0 solution...)
-   Select **Release** configuration
-   Build the **glew\_shared** target



