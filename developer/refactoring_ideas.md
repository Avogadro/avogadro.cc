---
layout: default
title: Refactoring Ideas
---

# Refactoring Ideas

This page contains some ideas about future refactorization of libavogadro. They may seriously break ABI (and possibly API), and should be discussed

Rendering Widget
----------------

-   Make libavogadro use abstract RenderWidget instead of GLWidget
-   Inherit GLWidget from RenderWidget and QGLWidget, move GL-independent functionality (e.g., plugin access) up to RenderWidget

**Fix**: multiple inheritance for QWidgets is tricky. Another variant of design:

    Renderer - ADT, doesn't inherit anything from Qt.
          Contains generic functionality like access methods, PainterDevice access, no signals/slots.
    GLWidget : public Renderer, public QGLWidget
    GL2Widget etc. ananlogically
    SimpleRenderWidget : public Renderer, public QGraphicsView
    AvogadroWidget - inherits QWidget, is directly used in UI of external client. 
          Contains pointer RenderWidget* to one chosen renderer, can switch them, can load RenderWidget* from plugin

-   Remove most of OpenGL calls from engines, replace them by new methods of PainterDevice

**Note**: Of course, GL only engines can exist for some specific purposes (maybe Cartoon, Ring), but such GL tasks as setting fg color, drawing eyecandy, GL\_RESCALE\_NORMAL, GL\_NORMALIZE should be encapsulated into renderer.

-   Remove all GL calls from Avogadro application - GUI client must work without any knowledge of backend. Call GL2PS from libavogadro if needed. Move glgraphicsview to libAvogadroWidget, don't use it in Avogadro application directly but through generic backend-independent view.
-   Add minimalistic SimpleRenderWidget without OpenGL (to create images for publication, b/w images, for use on old/heavy loaded PCs, etc). Also, some rendering imitation could be added - would be sufficient for reliable production of PDF and SVG without polygons.
-   Create separate GLWidgets for OpenGL2, 3, 4, etc (?)
-   "On-line" POV-Ray rendering for aesthetes (???)

PlotWidget
----------

-   Make it stronger and used by 3rd party developers - I think there are some projects interested in easy Qt way to do it without linking to KDE
-   Rename it to QPlotWidget and publish as independent library - may be some contributors will appear
-   Qt Designer plugin for QPlotWidget (?)
-   KPlotWidget is LGPL, so we can change its license to LGPL
-   Try to merge KPlotWidget with QPlotWIdget
    -   KPlotWidget didn't evolve a lot from time it was forked for Avogadro
    -   so it could be simple KDE wrapper for QPlotWidget library and some KDE-specific features
    -   [crazy idea] We can try to push QPlotWidget in QtGui, and KDE folks will do all work theirselves :)

Modularization of libavogadro
-----------------------------

Libavogadro contains a lot of APIs for different purposes and tends to grow. I propose to divide it into several modules (as Qt did when moving to Qt4)

For compatibility with previous versions, monolithic libavogadro library is provided

### **AvogadroCore** (done)

Generic classes which could be used even by terminal applications to simplify access to OB and make some advanced operations with molecules. <big>

    Atom
    Bond
    Cube
    Fragment
    IDList
    Mesh
    MeshGenerator
    Molecule
    MoleculeFile
    NeighborList (?)
    Primitive
    PrimitiveList
    Protein (?)
    Residue
    ZMatrix 

</big>

### **AvogadroWidget**

(partially done - didn't separate it from Python yet)

Rendering of molecules in external apps (including Avogadro). Static ("core") engine/tools also go here.

Since it's intended to be easy-to-use Qt widget, Designer plugin will be desired. <big>

    Animation
    Camera
    Color3f
    ColorButton (?)
    Cylinder_p
    GLHit
    GLPainter_p
    GLWidget
    Navigate
    Painter
    PainterDevice
    UndoSequence

    Color
    Engine
    Extension
    DockExtension
    Tool
    ToolGroup

</big>

Also, it's needed to create class AvogadroWidget which will allow to choose what subclass of RenderWidget is used

### **AvogadroPython**

Everything Python-related <big>

    pythonengine
    pythonerror
    pythonextension_p
    pythoninterpreter
    pythonscript
    pythonthread_p
    pythontool_p

</big>

-   **AvogadroPython** should be made a plugin - if AvogadroWidget is compiled with Python support, it must work when AvogadroPython library is missing, and load it if it's present. It will provide additional flexibility for bundle packages (Windows and Mac - user will be able to choose install it or not), and for traditional unix packages (one component - one package). Also, other scripting languages maybe added as plugins

<!-- -->

-   Add PythonPluginManager, inherited from PluginManager - AvogadroWidget should not be linked with Python or Boost to be lightweight.

### **QPeriodicTable** (done)

<big>

    ElementDetail
    ElementItem
    ElementTranslator
    PeriodicTableScene
    PeriodicTableView

</big>

### **QPlotWidget** (done)

<big>

    plotaxis
    plotobject
    plotpoint
    plotwidget

</big>

-   Also, new module with basis set related files from extensions/ directory could be introduced

<big>

    basisset
    molpro 
    mopacaux
    gaussianfchk

</big>

If you think 3 latter modules are too small, they could be merged in one, e.g. AvogadroExtra. However, see my proposition about plotwidget before. Also, there are a lot of types of basis sets. Periodic table could run as standalone application (there's gelemental though)

Source Tree
-----------

Current source tree is very complicated and "overpopulated". Extensions directory looks like a dump.

-   Divide libavogadro and avogadro repositories, create a superpackage instead. It isn't actual now, but if ABI is stable, application and library releases may be done separately, especially bugfix ones. What about Windows and Mac users? They may receive such bugfixes as incremental updates (e.g., download only avogadro.exe through update manager instead of full installation procedure for new release)

<!-- -->

-   Separate sources of modules: AvogadroCore, AvogadroWidget, AvogadroPython

<!-- -->

-   Divide extensions into:
    -   Main - live in Git of (lib)avogadro (e.g., animationextension,cartesianextension, fileimportextension, networkfetchextension, propextension, selectextension)
    -   Extras:
        -   Quantum - input generators, MO surfaces, basis set code
        -   Crystal - unitcell, supercell (?)
        -   Spectra

Of course, everything could be built together as superpackage

<Category:Developer>

