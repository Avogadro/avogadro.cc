---
title: Avogadro 0.9.6
categories: Releases
date: 2009-06-05
---



Avogadro 0.9.6 was released on 5 June 2009. This is the seventh of our final beta series before Avogadro 1.0.0 is released. Please help us by providing feedback. New beta releases are expected roughly once per month until the 1.0.0 release. You can [download this release here](http://sourceforge.net/project/showfiles.php?group_id=165310&package_id=187449).

What's New
----------

The following list includes some of the changes since [Avogadro 0.9.5](Avogadro 0.9.5 "wikilink"). This is a bug fix release, primarily to address a change in behavior of the Qt library. [Avogadro 0.9.5](Avogadro 0.9.5 "wikilink") suffered from a bug that caused data loss on all platforms using Qt 4.5.0 or earlier. This bug did not affect Avogadro users linking to Qt 4.5.1, and so the Mac binary package was not affected.



-   Fixed bug causing data loss on file saves when using Qt 4.5.0 or earlier.
-   Windows release now handles chemical files with Unix and Windows line endings.
-   More bugs found and fixed.

Dependencies
------------

1.  Eigen 2.0.2 [<http://eigen.tuxfamily.org/>](http://eigen.tuxfamily.org/) -- for compiling only.
2.  OpenBabel 2.2.1 or later [<http://openbabel.org>](http://openbabel.org/)
3.  CMake 2.6.0 or later [<http://www.cmake.org>](http://www.cmake.org/)
4.  Qt 4.4.0 or later [<http://www.trolltech.com>](http://www.trolltech.com/)
5.  Boost 1.35 or later [<http://www.boost.org/>](http://www.boost.org/) -- for Python support (optional).
6.  GLEW 1.5.0 or later [<http://glew.sourceforge.net/>](http://glew.sourceforge.net/) -- for GLSL support (optional)

Building
--------

untar the source `<pre>tar xvjf avogadro-0.9.6.tar.bz2</pre>`

make the build directory `<pre>
cd avogadro-0.9.6
mkdir build
</pre>`

configure `<pre>
cd build
cmake -DCMAKE_BUILD_TYPE=Release -DENABLE_GLSL=ON -DENABLE_PYTHON=ON ..
</pre>`

> CMake takes a few optional parameters:
>
> -   -DCMAKE\_INSTALL\_PREFIX= : specify the installation prefix (default /usr/local)
> -   -DOPENBABEL2\_LIBRARIES= : specify the OpenBabel2 libraries
> -   -DOPENBABEL2\_INCLUDE\_DIR : specify the OpenBabel2 include directory
> -   -DEIGEN\_INCLUDE\_DIR : specify the Eigen include directory
> -   -DCMAKE\_BUILD\_TYPE : specify the build type (Debug, Release etc)
> -   -DENABLE\_GLSL : set to ON to enable, or OFF to disable GLSL support.
> -   -DENABLE\_PYTHON : set to ON to enable, or OFF to disable Python support.
> -   -DENABLE\_RPATH: set to ON to install binaries with relative RPaths (no need to set LD\_LIBRARY\_PATH).
> -   -DENABLE\_UPDATE\_CHECKER: set to ON to enable checks for updated versions over the network - Linux distributions might want to disable this to avoid user confusion.
>
> For more information see the CMake website; [<http://www.cmake.org/>](http://www.cmake.org/)

build `<pre>make</pre>`

install `<pre>make install</pre>`

Known Issues & Limitations
--------------------------

This release is a beta release and is intended to gain feedback and interest in the project.

The code currently expects to be editing one 3D molecule per file with one coordinate set. This means:

-   Editing a multi-molecule file will only edit the first molecule. Saving will overwrite all records except the first.
-   Saving to a 2D format will not necessarily produce correct 2D stereochemistry.



-   Several builder features are not implemented, including:
    -   Crystal structure builder
    -   Carbon Nanotube builder
    -   Z-matrix editor (early version committed - needs more work)



-   Views cannot yet be removed into separate windows. In future releases, you will be able to have separate views of the same molecule in separate windows. Early support is in but disabled.
-   Export graphics will only save the current resolution in the window in bitmap form.

Troubleshooting
---------------

Problem: OpenBabel2 / Eigen libraries are not found.

Solution: The most likely the cause of this problem is non-standard install locations. Additionally, the detection system for finding libraries and includes is not flawless. The most likely remedy is to manually specify the library location and include directory for the package using the cmake arguments specified above.



