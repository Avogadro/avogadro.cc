---
layout: default
title: Avogadro 0.8.0
categories: Releases
---



Avogadro version 0.8.0 was released on May 19, 2008.

What's New
----------

The following list includes some of the changes since [Avogadro 0.6.1](Avogadro 0.6.1 "wikilink").



-   Axis rendering from the origin, to indicate the exact frame of reference.
-   Improved surface and orbital rendering.
-   Clipping planes for van der Waals surfaces.
-   Improved performance of "quick rendering" during user interaction.
-   Improved POV-Ray export.



-   New "alignment" tool, which currently allows picking two atoms to align to the X, Y or Z axes for a constant frame of reference.
-   New fragment library, to draw in arbitrary fragments. Includes a base library, as well as an unlimited number of user directories.
-   Improved selection tool to be more intuitive.



-   Added initial support for basic Gaussian calculations.
-   Added support for generating molecular orbitals from a Gaussian formatted checkpoint (\*.fchk files).
-   Support for multiple Gaussian cubes in one file (e.g., multiple molecular orbitals).
-   Fixed bugs for weighted-rotor searching and other molecular mechanics in combination with Open Babel.
-   Improved molecular mechanics speed via Open Babel.



-   Removed tabs for rendering configuration and primitives
-   Allows drag-and-drop of files to the viewer window to open.
-   Added file format filters for open and save dialogs.
-   Improved save dialogs on Linux.
-   Improved look of "property" editors, including Cartesian coordinates.
-   A variety of additional interface cleanups and improvements.



-   Embedded Python interpreter.
-   Initial support for animations and GROMACS trajectories (\*.xtc files).
-   Prevents possible over-writing of files if errors occur during saving.
-   Fixed several possible crashes and added additional "defensive programming."
-   Many, many bug fixes and small enhancements.

Dependencies
------------

1.  Eigen [<http://eigen.tuxfamily.org/>](http://eigen.tuxfamily.org/) -- for compiling. Not required for running Avogadro.
2.  OpenBabel 2.2.0b5 or later [<http://openbabel.sourceforge.net>](http://openbabel.sourceforge.net)
    1.  **NOTE** This is available as a [<http://sourceforge.net/project/showfiles.php?group_id=40728>\

3.  CMake 2.4.8 or later [1](http://www.cmake.org)
4.  Qt 4.3.x or later [<http://www.trolltech.com>](http://www.trolltech.com/)

Building
--------

untar the source `<pre>tar xvjf avogadro-0.8.0.tar.bz2</pre>`

make the build directory `<pre>
cd avogadro-0.8.0
mkdir build
</pre>`

configure `<pre>
cd build
cmake ..
</pre>`

> CMake takes a few optional parameters:
>
> -   -DCMAKE\_INSTALL\_PREFIX= : specify the installation prefix (default /usr)
> -   -DOPENBABEL2\_LIBRARIES= : specify the OpenBabel2 libraries
> -   -DOPENBABEL2\_INCLUDE\_DIR : specify the OpenBabel2 include directory
> -   -DEIGEN\_INCLUDE\_DIR : specify the Eigen include directory
>
> For more information see the CMake website; [<http://www.cmake.org/>](http://www.cmake.org/)

build `<pre>make</pre>`

install `<pre>make install</pre>`

Known Issues & Limitations
--------------------------

This release is an early beta release and is intended to gain feedback and interest in the project.

The code currently expects to be editing one 3D molecule per file with one coordinate set. This means:

-   Editing a multi-molecule file will only edit the first molecule. Saving will overwrite all records except the first.
-   Opening a 2D file will not result in 3D coordinates. Opening a SMILES file will not create 3D coordinates either.
-   Saving to a 2D format will not necessarily produce correct 2D stereochemistry.



-   Only one color scheme is currently available, although the code allows different types to be implemented. Suggestions are welcome.



-   Several builder features are not implemented, including:
    -   Protein and biomolecule builders
    -   Crystal structure builder
    -   Carbon Nanotube builder
    -   Z-matrix editor



-   Views cannot yet be removed into separate windows. In future releases, you will be able to have separate views of the same molecule in separate windows.
-   Export graphics will only save the current resolution in the window in bitmap form. Vector formats (SVG, PS, PDF) and other formats are intended to be implemented in the future.



A select list of commands is currently available, mostly as examples of what can be done using the Avogadro framework.

-   Only the GAMESS and Gaussian input generation is complete (as an example). Other programs are intended for support in future releases.



-   The H2Methyl extension causes crashes and was excluded from this build.

Troubleshooting
---------------

Problem: OpenBabel2 / Eigen libraries are not found.

Solution: Most likely the cause of this problem is due to non-standard install locations. Additionally, the detection system for finding libraries and includes is not flawless. The most likely remedy is manually specify the library location and include directory for the package using the cmake arguments specified above.



