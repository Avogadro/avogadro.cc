---
title: Avogadro 0.8.1
categories: Releases
date: 2008-06-07
---



Avogadro version 0.8.1 was released on 7 June 2008.

What's New
----------

The following list includes some of the changes since [Avogadro 0.8.0](Avogadro 0.8.0 "wikilink").



-   Orbitals are cleared with the rest of the molecule.
-   Orbitals engine can now display the size of the cube being rendered.
-   AutoOpt tool now displays the energy as it optimizes.
-   Quick render functions added to sphere engine and surface display types.
-   Large speed improvement to the surface rendering.



-   The manipulate tool now works much faster than before.
-   Several bug fixes for the "Insert Fragment..." dialog. Insert smiles available again.
-   More robust adjust hydrogens feature, still not perfect.



-   Improved unit cell dialog.
-   Conformer energies are now displayed.
-   Python extension now searches for system wide scripts too.
-   Gaussian input deck generator now uses extender for preview.
-   Gaussian input deck generator now supports z-matrix output.
-   GAMESS input deck dialog reduced in vertical size to accommodate smaller resolutions.



-   Export of graphics dialog improved.
-   Add engines now adds the engine selected (previous bug caused random engine to be added with name selected).



-   Improved installer (thanks to Uwe Stöhr).
-   Many windows specific bug fixes.



-   Plugin version bumped to 1.1, will prevent stale plugin files from being loaded.
-   Fixed several possible crashes and added additional checks to improve stability.
-   Many, many bug fixes and small enhancements.

Dependencies
------------

1.  Eigen [<http://eigen.tuxfamily.org/>](http://eigen.tuxfamily.org/) -- for compiling. Not required for running Avogadro.
2.  OpenBabel 2.2.0b5 or later [<http://openbabel.org>](http://openbabel.org/)
    1.  **NOTE** This is available as a [<http://sourceforge.net/project/showfiles.php?group_id=40728>\

3.  CMake 2.4.7 or later [<http://www.cmake.org>](http://www.cmake.org/)
4.  Qt 4.3.x or later [<http://www.trolltech.com>](http://www.trolltech.com/)

Building
--------

untar the source `<pre>tar xvjf avogadro-0.8.1.tar.bz2</pre>`

make the build directory `<pre>
cd avogadro-0.8.1
mkdir build
</pre>`

configure `<pre>
cd build
cmake -DCMAKE_BUILD_TYPE=Release ..
</pre>`

> CMake takes a few optional parameters:
>
> -   -DCMAKE\_INSTALL\_PREFIX= : specify the installation prefix (default /usr)
> -   -DOPENBABEL2\_LIBRARIES= : specify the OpenBabel2 libraries
> -   -DOPENBABEL2\_INCLUDE\_DIR : specify the OpenBabel2 include directory
> -   -DEIGEN\_INCLUDE\_DIR : specify the Eigen include directory
> -   -DCMAKE\_BUILD\_TYPE : specify the build type (Debug, Release etc)
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
    -   Protein and biomolecule builders (Geoff?)
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



