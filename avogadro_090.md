---
layout: default
title: Avogadro 0.9.0
---

# Avogadro 0.9.0

Avogadro 0.9.0 was released on 12 January 2009. This is the first of our final beta series before Avogadro 1.0.0 is released. Please help us by providing feedback.

What's New
----------

The following list includes some of the changes since [Avogadro 0.8.1](Avogadro 0.8.1 "wikilink")

### General

-   The core API of Avogadro was rewritten -- improved thread safety, Qt-like API.
-   Rewritten core allows independence from the underlying libraries -- OpenBabel API not exposed.
-   Initial unit testing added for Molecule class.

### Interface

-   POV-Ray export dialog added -- POV-Ray can be called directly.
-   Export graphics improvements -- should work on more systems.
-   The navigate tool is now called if tools do not accept the mouse events.
-   Keyboard events sent to the tools -- arrow keys manipulate the view.

### Rendering

-   Mesh generation speeds massively improved.
-   Mesh rendering improved -- managed by the molecule now.
-   Primitives / colors only shown for display types that support them.
-   Meshes can now be rendered using POV-Ray.
-   POV-Ray rendering improved for transparent surfaces.
-   Wireframe engine shows aromatic bonds, double bonds etc.
-   Initial GLSL support added for improved rendering on graphics cards that support it.
-   Depth cues using fog have been added.
-   Quick draw optimizations when moving the view can be turned off.

### Commands / Extensions

-   QtConcurrent used to multithread cube calculations.
-   MO and electron density cubes can be calculated from MOPAC AUX files.
-   Q-Chem input generation support.
-   Van der Waals surfaces at any distance can be made.
-   Initial animation support added.

### Scripting

-   New Boost Python bindings.
-   Integration with PyQt4.
-   Improved Python terminal (save commands between sessions and syntax highlighting).
-   PythonEngine: You can now use Python scripts to add new display types (wireframe.py example included).
-   Python extensions behave more like real extensions (choose menu path, provide multiple actions, ...)
-   First release to have windows installer with Python support.

Dependencies
------------

1.  Eigen 2.0.0\_beta6 [<http://eigen.tuxfamily.org/>](http://eigen.tuxfamily.org/) -- for compiling only.
2.  OpenBabel 2.2.0 or later [<http://openbabel.org>](http://openbabel.org/)
3.  CMake 2.6.0 or later [<http://www.cmake.org>](http://www.cmake.org/)
4.  Qt 4.4.0 or later [<http://www.trolltech.com>](http://www.trolltech.com/)
5.  Boost 1.35 or later [<http://www.boost.org/>](http://www.boost.org/) -- for Python support (optional).
6.  GLEW 1.5.0 or later [<http://glew.sourceforge.net/>](http://glew.sourceforge.net/) -- for GLSL support (optional)

Building
--------

untar the source `<pre>tar xvjf avogadro-0.9.0.tar.bz2</pre>`

make the build directory `<pre>
cd avogadro-0.9.0
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

-   Views cannot yet be removed into separate windows. In future releases, you will be able to have separate views of the same molecule in separate windows. Early support is in but disabled -- this should make it into the next release.
-   Export graphics will only save the current resolution in the window in bitmap form.

Troubleshooting
---------------

Problem: OpenBabel2 / Eigen libraries are not found.

Solution: The most likely the cause of this problem is non-standard install locations. Additionally, the detection system for finding libraries and includes is not flawless. The most likely remedy is to manually specify the library location and include directory for the package using the cmake arguments specified above.

<Category:Releases>

