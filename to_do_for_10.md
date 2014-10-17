---
layout: default
title: To Do For 1.0
---

# To Do For 1.0

Some items to complete from the long-term [To Do](To Do "wikilink") list for the 1.0 release:

-   Help System
    -   Integrated help
    -   Handbook for users
    -   Web tutorials and screencasts
    -   Tutorials for developers

<!-- -->

-   Translations
    -   Set a "string" freeze **(June 4th)**
    -   Integrate new translations from [Launchpad](https://translations.launchpad.net/avogadro/trunk/+pots/avogadro)
    -   Add a "translation credits" section to wiki.

<!-- -->

-   User Interface Changes
    -   Tools into separate toolbar **(done)**
    -   Tool settings in separate dock window **(done)**
    -   Separate "insert fragment" into extension **(done)**

<!-- -->

-   Scripting
    -   Python bindings using SIP and boost **(done)**
    -   Need to expose PythonEngine and PythonTool **(done)**
    -   Need PluginManager to create multiple engines and tools for each Python script **(done)**
        -   TODO: PythonExtension **(done)**

<!-- -->

-   Animation / vibrations
    -   Animations **(done)**
    -   Vibrations **(done)**
        -   Need some bug fixing

<!-- -->

-   More compute interfaces from the [To Do](To Do "wikilink") list **(in progress)**
    -   Insure all input builders also have support for reading output & orbitals.
        -   In particular, NWChem and GAMESS?

<!-- -->

-   Web / Searching interfaces
    -   Open URL extension **(done)**
    -   Open PDB id extension **(done)**

<!-- -->

-   Save settings to CML
    -   Core functionality integrated **(done)**
    -   Need to update interface with new settings
    -   Need to segregate per-file settings from application defaults

<!-- -->

-   A "plugin manager" is needed to enable/disable plugins **(done)**
    -   Optionally, this should be able to download and/or build plugins from an online directory
    -   This obviously works best when the plugins are based in Python -- no compiles!

Projects
--------

These are specific projects that people are working on for 1.0.

### Geoff

-   Animations
    -   Merge animation extension into general libavogadro class **(done)**
    -   Document **(done)**
    -   Update animation extension **(done)**

<!-- -->

-   Color enhancements
    -   New types:
        -   Custom color **(done)**
        -   Custom gradients
        -   Custom indexed color (e.g., rings, chains/ribbons)
        -   Color by atom position (i.e., distance from atom 1) **(done)**
        -   Color by atom charge **(done)**
        -   Color by hydrophobic/hydrophilic residues **(done)**
        -   Color by residue sidechain pKa **(done)**
    -   Allow color settings **(done)**
        -   Read/write settings (to file)

<!-- -->

-   Builders
    -   Amino acid peptide builder **(done)**
    -   Crystal surface builder
    -   Nanotube builder ?

<!-- -->

-   Unit Cells
    -   Crystal/Surface builder
    -   Signal to enable/disable "display unit cell" menu item
    -   "Display Unit Cell" action in View menu **(done)**
    -   Finish fillUnitCell code **(done)**
    -   Add simple supercell extension **(done)**
    -   Add back "view along Miller Plane" extension ??

<!-- -->

-   Plugins
    -   Revise configuration with "identifier" (non-translated string) **(done)**
    -   Revise to minimize duplicate translated strings **(done)**

<!-- -->

-   Extensions
    -   Text reader (i.e. see text of output file)
    -   Molecule properties

<!-- -->

-   Open Babel 2.2.2
    -   Weighted conformer search integration in Avogadro
        -   Threaded, and return multiple conformers to list

<!-- -->

-   Metadata
    -   NMR metadata from Open Babel **(done)**
    -   Atom forces (for vibrations and Force engine) **(done)**
    -   General Primitive metadata to integrate with OBPairData **(done)**

<!-- -->

-   Vibrations
    -   Force arrows **(done)**
    -   Animations **(done)**

<!-- -->

-   General UI polish **(done)**

### Tim

-   Remove BoxControl for now **(done)**
-   Check Protein API + docs **(done)**
-   Add constructor for NeighborList with QList<Atom*> **(done)**
-   Python
    -   Add a Avogadro.py wrapper around \_Avogadro.[so/pyd] with at least the dl stuff from openbabel.py (needed for formats to load when running standalone apps) **(done)**
    -   Ensure all unit tests pass
    -   Add more examples scripts **(in progress)**
    -   Add reload python script(s) button
    -   Some specific issues:
        -   Make sure Camera::modelview/setModelview works on WIN32
        -   provide toPyQt(...) for all relevant classes **(done)**
    -   Use a single QTextEdit for the PythonTerminal (like ParaView) **(done)**
-   Finish Cartoon engine: **(done)**
-   Engines
    -   HydrogenBond: Use NbrList class for faster H-Bond detection **(done)**
    -   Make sure there are good (quality/performance) settings for large molecules in general **(Marcus added a simple wireframe..)**
-   Ensure all plugins can be reloaded automatically **(done & removed the restart Avogadro message box)**
-   NeighborList class **(done + unit tests)**

### Dave

-   Spectra
    -   Move vibrationplot.\* to its own Spectra extension **(done)**
    -   Create persistent color schemes for plots **(done)**
        -   Several attractive defaults **(Light / Dark -- done)**
        -   User customization **(done)**
    -   Add tab bar with options **(done)**
    -   tsv export of plotted points **(done)**
    -   Adjustable DPI for exported images **(done)**
    -   Adjustable image size of exports **(done)**
    -   Reorganize spectra types to allow easier addition of types.
-   Add left click events for points in PlotWidget.\* **(done)**
-   Add a 'select(QPoint\*)' slot to PlotWidget.\* that will add a marker at a given location. **(done)**
-   Add a followMouse property to highlight the nearest point to the mouse on mouseover. **(done)**

### Marcus

-   Rework the MO / Surface calculation extension interface -- simplify.
-   Update extension -- using QtNetwork to check for updated versions, offer to download
-   Z-matrix editor **(in progress)**
-   Improve plugin loading, load user plugins, allow programs to add extra search paths
-   Fix the engine loading/naming -- often gets confused, does not add new engines, old ones incorrectly named.
-   Remove unnecessary d-pointers from private classes
-   GLSL Painter inherited from GLPainter to use OpenGL 1.5 and GLSL features
-   Painter API stubs for future expansion **(done)**
-   UTF8 aware file loading and saving as an interface **(in progress)**
-   Packaging for Mac .app bundle **(done)**
-   Example extensions built outside of Avogadro distribution **(done)**
-   Move private classes to classname\_p.h style headers **(done)**

