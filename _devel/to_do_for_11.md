---
layout: single
title: To Do for 1.1
categories: Devel
---



The upcoming development series 1.1.x will be a series of unstable/beta releases, leading up to the 1.2.0 release. This process will be similar to the 0.9.x releases which lead up to the stable 1.0.x series.

Specific Plans
--------------

The Avogadro 1.1.x releases and 1.2 will rely on the current Open Babel 2.3.x releases (i.e., the current SVN trunk). Snapshots of Open Babel will be made to coincide with our releases.

General Ideas
-------------

-   New draw tool for templates/fragments (e.g., click to add a benzene ring)



-   Reading multiple geometries and energies from QM codes (e.g., transition state searches, reaction paths, geometry optimizations, relaxed scans).
    -   **(started - Gaussian)**
    -   **(started - Gamess)**
-   Reading orbital energies
-   Support for reading orbital coefficients (both restricted and unrestricted spin orbitals)
-   Enhancements of symmetry code (**spglib**?)
    -   non exact symmetry search
    -   return symmetry axes and planes with deviations
    -   optimization of structure for given point group
    -   symmetry order of pre-defined axis (e.g., rotor axis) - port from OpenThermo



-   Enhancing the "project tree" to highlight multiple molecular fragments independently
-   Automatic structure -\> name (including searching for multiple molecular fragments)
-   Support in Open Babel for orbital energies -- and orbital energy diagrams in Avogadro
-   Integration with new open-source INDO code for simple organic/polymer QM and UV/Vis prediction



-   Engines
    -   Display arbitrary axes **(done)**
    -   Add font and color settings to labels **(done)**
    -   Element settings dialog: setup custom colors/sizes/labels for atoms of different elements **(done)**
    -   Arbitrary planes
    -   Scale of image

<!-- -->

-   Tools
    -   Angle between planes (?)

<!-- -->

-   Extensions
    -   Cartesian Editor
        -   Add sorting **(done)**
        -   Show symmetry unique atoms
    -   QC Input
        -   Custom basis sets for different elements
        -   Fetch basis sets from EMSL
        -   Load QC Input dialogs using run-time interpretation of platform-independent "plugins", probably XML + JavaScript(maybe Python also) + UI(maybe QML when possible); add possibility to easily download needed plugins from UI
    -   Properties
        -   Make properties dialogs more usable **(in progress)**
    -   Spectra
        -   Refactor spectra extension and improve UI **(in progress)**
        -   Add suppport for Raman spectra **(done)**
        -   Show intensities for widened peaks **(done for IR)**
        -   <s>New type of spectra scaling: different scale factors for different intervals</s> (I don't need it anymore, report if somebody needs)
        -   Automatic fit of PlotWidget limits to loaded data **(done)**
    -   Symmetry (as in MacMolPlt) - spglib
        -   Point group search
        -   Choose symmetry group from subgroups of found point group
        -   Symmetry elements visualization
        -   Symmetrization of almost symmetric geometries
    -   Vibrations
        -   Moved vibration list to dock **(done)**
        -   Vibration animation export (?)
-   Add filtering to properties dialogs and vibrations list **(done for vibrations)**
-   New dock for geometry optimization and relaxed scan results
-   <s>Send image to OpenOffice.org via pipe</s> (not for 1.1)



-   Packmol extension
    -   <http://github.com/timvdm/Avogadro-Packmol-Extension>
    -   You always need to specify the number of molecules for a given volume
        -   Estimating this would be nice: calculate Volume + MW + density -\> \
    -   A wizard with some default systems
        -   Protein (or molecule) + solvent + counter ions (make it smart so counter ions are correctly added to make the system charge neutral. Required for Ewald, PME, ...)
        -   (Protein) + Lipid bilayer + solvent
        -   Micelle/double layered/...?
        -   Molecule at interface... (find best fitting plane for molecule -\> determine correct rotation)
    -   Allow user to browse for files that contain the used structures
        -   Use QDesktopServices to obtain temporarily location so it doesn't matter if the files are not in the same dir
        -   Convert the files so they all have the same format (e.g. pdb, required for packmol)
    -   Text editor for experts with syntax highlighting
        -   Simple parser for this text to give \
        -   If there is time left: A simple 3D widget with a preview of all described volumes in wireframe might be nice to identify problems early
-   Gromacs extension
    -   Generate input files
    -   There is a new libdrf to read in trajectories
    -   Some overlap with Packmol: solvation + counter ions...
    -   In progress but code currently not accessible (broken mainboard)
-   Both these extensions would benefit from better performance for large systems (Marcus? ;) )



