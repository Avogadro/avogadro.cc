---
title: Avogadro 0.6.0
categories: Releases
date: 2008-02-29
---



Avogadro version 0.6.0 was released on February 29, 2008.

What's New
----------

The following list includes some of the changes since [Avogadro 0.2.0](Avogadro 0.2.0 "wikilink"). The jump in version number indicates that Avogadro is rapidly reaching a stable 1.0 release series.



-   Cloning render engines allowing parts of the molecule to be displayed using different styles etc.
-   Protein ribbon engine to display secondary structure.
-   Ring engine to highlight ring structures in molecules.
-   Polyhedron engine highlighting metallic centers in molecules for example.
-   Configurable color maps such as user specified colors.
-   Added an isosurface generator using the marching cubes algorithm.
-   New molecular orbitals engine that can display molecular orbitals and other surfaces from cube files.
-   New Van der Waals surface engine generates a VdW surface with optional ESP coloring.



-   An improved periodic table for drawing and editing.



-   Selection menu
    -   Add, remove, clear, invert selection.
    -   Select by residue, chain, molecule (i.e., click on one atom, select a whole group or molecule).
    -   Select by element, residue name, solvent.
    -   Selections using SMARTS.



-   Menu reorganization.
-   Persistent window/tool settings.
-   stacked widgets giving more space to the OpenGL window displaying the molecule.



-   Improved force field options, including calculating the energy, and conformational searching.
-   Geometry optimization is threaded with a progress dialog.
-   Improved speed of geometry optimization with Open Babel 2.2 builds.



-   Initial support for internationalization and translation.
    -   Partial translations for French, German and British English.
-   Many, many more enhancements and bug fixes.

Dependencies
------------

1.  Eigen [<http://eigen.tuxfamily.org/>](http://eigen.tuxfamily.org/) -- for compiling. Not required for running Avogadro.
2.  OpenBabel 2.2.0b4 or later [<http://openbabel.sourceforge.net>](http://openbabel.sourceforge.net)
    1.  **NOTE** This is available as a [<http://sourceforge.net/project/showfiles.php?group_id=40728>\

3.  CMake 2.4.5 or later [1](http://www.cmake.org)
4.  Qt 4.3.x or later [<http://www.trolltech.com>](http://www.trolltech.com/)

Building
--------

untar the source `<pre>tar xvjf avogadro-0.6.0.tar.bz2</pre>`

make the build directory `<pre>
cd avogadro-0.6.0
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



-   The fragment library, protein and biomolecule builder features are not implemented yet.



-   The atom and bond list on the right side of the window only allows a list. It is not interactive -- for example, selecting an atom in the list will not select it in the view (or vice-versa). Only the atom and bond index are reported, nothing else yet.
-   Views cannot yet be removed into separate windows. In future releases, you will be able to have separate views of the same molecule in separate windows.
-   Export graphics will only save the current resolution in the window in bitmap form. Vector formats (SVG, PS, PDF) and other formats (POV-Ray) are intended to be implemented in the future.



A select list of commands is currently available, mostly as examples of what can be done using the Avogadro framework.

-   Only the GAMESS input generation is complete (as an example). Other programs are intended for support in future releases.
-   No scripting support (for Python, Perl, Ruby, and shell scripting) is available. Future releases will allow users to add scripts for tasks such as submitting jobs to computational programs, changing molecular structure, or other uses. The entire engine will be scriptable through Avogadro and Open Babel scripting layers.
-   A z-matrix builder command is intended for future releases.
-   A unit cell / crystal builder is intended for future releases.



-   The H2Methyl extension causes crashes always and so it was excluded from this build.

Troubleshooting
---------------

Problem: OpenBabel2 / Eigen libraries are not found.

Solution: Most likely the cause of this problem is due to non-standard install locations. Additionally, the detection system for finding libraries and includes is not flawless. The most likely remedy is manually specify the library location and include directory for the package using the cmake arguments specified above.



