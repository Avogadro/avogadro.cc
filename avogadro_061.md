---
layout: default
title: Avogadro 0.6.1
---

# Avogadro 0.6.1

Avogadro version 0.6.1 was released on March 8, 2008.

What's New
----------

The following list includes some of the changes since [Avogadro 0.6.0](Avogadro 0.6.0 "wikilink"). This is a bug fix release that includes a few small feature enhancements.

### Rendering

-   Fixed issue with losing the OpenGL context when switching views/virtual desktops.
-   Protein ribbon engine now includes the last two points.
-   Fixed rendering of selected atoms/bonds for the ball and stick engine.
-   Second light source was added to the default OpenGL view enhancing surface rendering.
-   Render cache invalidation more fine grained. Improved rendering performance on bigger molecules.

### Editing Tools

-   Cursor types now changed depending upon actions in the select/rotate tool.
-   Eye candy now solid which improves rendering performance.

### Interface

-   If a window is moved off screen it will be placed in a viewable area on the Mac.

### General

-   Many, many more enhancements and bug fixes.

Dependencies
------------

1.  Eigen [<http://eigen.tuxfamily.org/>](http://eigen.tuxfamily.org/) -- for compiling. Not required for running Avogadro.
2.  OpenBabel 2.2.0b4 or later [<http://openbabel.sourceforge.net>](http://openbabel.sourceforge.net)
    1.  **NOTE** This is available as a [<http://sourceforge.net/project/showfiles.php?group_id=40728>\# snapshot]

3.  CMake 2.4.5 or later [1](http://www.cmake.org)
4.  Qt 4.3.x or later [<http://www.trolltech.com>](http://www.trolltech.com/)

Building
--------

untar the source `<pre>tar xvjf avogadro-0.6.1.tar.bz2</pre>`

make the build directory `<pre>
cd avogadro-0.6.1
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

-   No animations are currently supported (or molecular dynamics trajectories, movies, vibrations, etc.).
-   Editing a multi-molecule file will only edit the first molecule. Saving will overwrite all records except the first.
-   Opening a 2D file will not result in 3D coordinates. Opening a SMILES file will not create 3D coordinates either.
-   Saving to a 2D format will not necessarily produce correct 2D stereochemistry.

### Rendering

-   Only one color scheme is currently available, although the code allows different types to be implemented. Suggestions are welcome.

### Tools / Building

-   The fragment library, protein and biomolecule builder features are not implemented yet.

### Interface

-   The atom and bond list on the right side of the window only allows a list. It is not interactive -- for example, selecting an atom in the list will not select it in the view (or vice-versa). Only the atom and bond index are reported, nothing else yet.
-   Views cannot yet be removed into separate windows. In future releases, you will be able to have separate views of the same molecule in separate windows.
-   Export graphics will only save the current resolution in the window in bitmap form. Vector formats (SVG, PS, PDF) and other formats (POV-Ray) are intended to be implemented in the future.

### Commands

A select list of commands is currently available, mostly as examples of what can be done using the Avogadro framework.

-   Only the GAMESS input generation is complete (as an example). Other programs are intended for support in future releases.
-   No scripting support (for Python, Perl, Ruby, and shell scripting) is available. Future releases will allow users to add scripts for tasks such as submitting jobs to computational programs, changing molecular structure, or other uses. The entire engine will be scriptable through Avogadro and Open Babel scripting layers.
-   A z-matrix builder command is intended for future releases.
-   A unit cell / crystal builder is intended for future releases.

### Windows Build

-   The H2Methyl extension causes crashes always and so it was excluded from this build.

Troubleshooting
---------------

Problem: OpenBabel2 / Eigen libraries are not found.

Solution: Most likely the cause of this problem is due to non-standard install locations. Additionally, the detection system for finding libraries and includes is not flawless. The most likely remedy is manually specify the library location and include directory for the package using the cmake arguments specified above.

<Category:Releases>

