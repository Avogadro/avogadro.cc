---
layout: default
title: Avogadro 0.9.2
---

# Avogadro 0.9.2

Avogadro 0.9.2 was released on 1 March 2009. This is the third of our final beta series before Avogadro 1.0.0 is released. Please help us by providing feedback. New beta releases are expected roughly once per month until the 1.0.0 release. You can [download this release here](https://sourceforge.net/project/showfiles.php?group_id=165310&package_id=187449).

What's New
----------

The following list includes some of the changes since [Avogadro 0.9.1](Avogadro 0.9.1 "wikilink"). This is mainly a bug fix release with a few new features implemented over the last few weeks of development.

### General

-   Tool and extension parenting issues fixed, application shutdown is now much smoother.
-   Forcefields on Windows should now work with any shortcut/run directory.
-   Work to make Avogadro find plugins relative to the binary - relocatable install directory.
-   Versioned configuration, old configurations will be discarded.
-   Bump in the plugin version due to API changes in our plugins.
-   Desktop file and icon in Linux with association of various file types we support.
-   More bugs found and fixed.

### Interface

-   Combined configuration / preferences dialog added.

### Rendering

-   New cartoon rendering engine with some inital support for ribbons.
-   Unit cell rendering can be turned off.
-   Quick rendering setting now correctly reported.
-   POV-Ray colored mesh rendering bug fixed.

### Extensions

-   New super cell builder that supports building super cells with improved bonding.
-   Surfaces extension bug fix for electron density calculations.
-   New MOPAC plugin that supports direct execution of MOPAC.
-   New vibrations extension for molecular vibration visualization.

Dependencies
------------

1.  Eigen 2.0.0 [<http://eigen.tuxfamily.org/>](http://eigen.tuxfamily.org/) -- for compiling only.
2.  OpenBabel 2.2.0 or later [<http://openbabel.org>](http://openbabel.org/)
3.  CMake 2.6.0 or later [<http://www.cmake.org>](http://www.cmake.org/)
4.  Qt 4.4.0 or later [<http://www.trolltech.com>](http://www.trolltech.com/)
5.  Boost 1.35 or later [<http://www.boost.org/>](http://www.boost.org/) -- for Python support (optional).
6.  GLEW 1.5.0 or later [<http://glew.sourceforge.net/>](http://glew.sourceforge.net/) -- for GLSL support (optional)

Building
--------

untar the source `<pre>tar xvjf avogadro-0.9.2.tar.bz2</pre>`

make the build directory `<pre>
cd avogadro-0.9.2
mkdir build
</pre>`

configure `<pre>
cd build
cmake -DCMAKE_BUILD_TYPE=Release -DENABLE_GLSL=ON -DENABLE_PYTHON=ON ..
</pre>`

> CMake takes a few optional parameters:
>
> -   -DCMAKE\_INSTALL\_PREFIX= : specify the installation prefix (default /usr)
> -   -DOPENBABEL2\_LIBRARIES= : specify the OpenBabel2 libraries
> -   -DOPENBABEL2\_INCLUDE\_DIR : specify the OpenBabel2 include directory
> -   -DEIGEN\_INCLUDE\_DIR : specify the Eigen include directory
> -   -DCMAKE\_BUILD\_TYPE : specify the build type (Debug, Release etc)
> -   -DENABLE\_GLSL : set to ON to enable, or OFF to disable GLSL support.
> -   -DENABLE\_PYTHON : set to ON to enable, or OFF to disable Python support.
>
> For more information see the CMake website; [<http://www.cmake.org/>](http://www.cmake.org/)

build `<pre>make</pre>`

install `<pre>make install</pre>`

Known Issues & Limitations
--------------------------

This release is a beta release and is intended to gain feedback and interest in the project.

The code currently expects to be editing one 3D molecule per file with one coordinate set. This means:

-   Editing a multi-molecule file will only edit the first molecule. Saving will overwrite all records except the first.
-   Opening a SMILES file will not create 3D coordinates either (although you can insert SMILES as fragments into an Avogadro window)
-   Saving to a 2D format will not necessarily produce correct 2D stereochemistry.

### Tools / Building

-   Several builder features are not implemented, including:
    -   Protein and biomolecule builders
    -   Crystal structure builder
    -   Carbon Nanotube builder
    -   Z-matrix editor

### Interface

-   Views cannot yet be removed into separate windows. In future releases, you will be able to have separate views of the same molecule in separate windows. Early support is in but disabled.
-   Export graphics will only save the current resolution in the window in bitmap form.

Troubleshooting
---------------

Problem: OpenBabel2 / Eigen libraries are not found.

Solution: The most likely the cause of this problem is non-standard install locations. Additionally, the detection system for finding libraries and includes is not flawless. The most likely remedy is to manually specify the library location and include directory for the package using the cmake arguments specified above.

<Category:Releases>

