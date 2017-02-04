---
title: Avogadro 0.2.0
categories: Releases
date: 2007-10-23
---



Avogadro version 0.2.0 was released on October 23, 2007.

What's New
----------

The following list includes some of the changes since [Avogadro 0.1.0](Avogadro 0.1.0 "wikilink").



-   Support for rendering crystallographic cells and editing unit cell parameters.
-   Flexible rendering, including multiple overlays, and per-atom and per-bond custom rendering.
-   Flexible atom labeling schemes.
-   Support for bond labeling.
-   Axes engine to display x, y, z axes in the corner of the window.
-   Improved transparency, including an adjustable transparent van der Waals sphere rendering option.
-   Configuration options for rendering engines.
-   A new flexible "painter" architecture, now allowing export to POV-Ray. In the future, support for PDF and SVG are planned.
-   Multi-threaded rendering.



-   A full periodic table for drawing and editing.
-   New autorotate tool which will animate rotation of the molecule.
-   New auto-optimize tool, which will continually optimize the geometry of the molecule as you draw or modify it.
-   New "bond-centric" manipulation tool, which facilitates changing the bond length, angle, or dihedral angle of parts of a molecule.
-   More visual feedback when using the mouse tools.



-   Improved force field options, including calculating the energy, and conformational searching.
-   Geometry optimization is threaded with a progress dialog.
-   Improved speed of geometry optimization with Open Babel 2.2 builds. (Used on Mac and Windows binaries for Avogadro 0.2.)
-   Adding/removing hydrogen atoms will now add to selected atoms only.
-   New command to change hydrogen atoms (or only selected H atoms) to methyl groups.
-   When pasting, the new atoms will be automatically selected for movement or manipulation.
    -   We do not (yet) change tools, so you will likely wish to change to the manipulate tool after pasting atoms.
-   Improved support for GAMESS advanced input generation (EFP and QM/MM).
-   Command extensions can now go into any menu or submenu.



-   Initial support for internationalization and translation.
    -   Partial translations for French and German.
-   Improved Mac support, including a unified toolbar look, use of a one-button mouse or trackpad (using the Option and Command keys as modifiers), and more.
-   Many, many more enhancements and bug fixes.

Dependencies
------------

1.  Eigen [<http://eigen.tuxfamily.org/>](http://eigen.tuxfamily.org/) -- for compiling. Not required for running Avogadro.
2.  OpenBabel 2.1.0 [<http://openbabel.sourceforge.net>](http://openbabel.sourceforge.net)
3.  CMake 2.4.5 or later [1](http://www.cmake.org)
4.  Qt 4.3.x or later [<http://www.trolltech.com>](http://www.trolltech.com/)

Building
--------

untar the source `<pre>tar zxvf avogadro-0.1.0.tar.gz</pre>`

make the build directory `<pre>
cd avogadro-0.1.0
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



-   Only one color scheme is currently available, although the code allows different types to be implemented. Suggestions are welcome.
-   No protein ribbon or cartoon render option is available.
-   Surface rendering is not implemented.



-   The fragment library, protein and biomolecule builder features are not implemented yet.
-   The "click measure" tool does not allow measuring 4-atom dihedral angles. All output is graphical, so it is not currently possible to copy the text to another program.
-   The AutoOptimize tool causes crashes when mixing it with the Geometric Optimization extension available from the 'Tools' menu.



-   The atom and bond list on the right side of the window only allows a list. It is not interactive -- for example, selecting an atom in the list will not select it in the view (or vice-versa). Only the atom and bond index are reported, nothing else yet.
-   Views cannot yet be removed into separate windows. In future releases, you will be able to have separate views of the same molecule in separate windows.
-   Export graphics will only save the current resolution in the window in bitmap form. Vector formats (SVG, PS, PDF) and other formats (POV-Ray) are intended to be implemented in the future.
-   No "preferences" are saved (e.g., rendering detail, default colors, etc.).



A select list of commands is currently available, mostly as examples of what can be done using the Avogadro framework.

-   The "Optimize Geometry" command only supports the ghemical force field. Other force fields are intended in future releases.
-   Only the GAMESS input generation is complete (as an example). Other programs are intended for support in future releases.
-   No scripting support (for Python, Perl, Ruby, and shell scripting) is available. Future releases will allow users to add scripts for tasks such as submitting jobs to computational programs, changing molecular structure, or other uses. The entire engine will be scriptable through Avogadro and Open Babel scripting layers.
-   A z-matrix builder command is intended for future releases.
-   A unit cell / crystal builder is intended for future releases.



-   The H2Methyl extension causes crashes always and so it was excluded from this build.

Troubleshooting
---------------

Problem: OpenBabel2 / Eigen libraries are not found.

Solution: Most likely the cause of this problem is due to non-standard install locations. Additionally, the detection system for finding libraries and includes is not flawless. The most likely remedy is manually specify the library location and include directory for the package using the cmake arguments specified above.



