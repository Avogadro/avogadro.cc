---
layout: single
title: Creating a Third Party Plugin
categories: Devel
---



Choose plugin type
------------------

Avogadro 1.0.0 allows you to develop plugins of several types:

-   **Painter**: alternative way of graphics export (e.g., POVRay)
-   **Engine**: new rendering style for molecules or other graphic elements
-   **Tool**: new mouse tool for interaction with molecule
-   **Color**: new color scheme for bonds, atoms, etc.
-   **Extension**: new menu action or dock widget

In addition, Avogadro 1.1.x branch will provide

-   **DockExtension**: special type of extension, providing additional options for dock

All you need is to choose proper interface and inherit your plugin class from it. For more information look through [API Documentation](http://avogadro.cc/api/dev/)

Prepare a repository
--------------------

Modify the files
----------------

Building and installation
-------------------------

In this section building of plugin **outside** Avogadro source tree is described. Alternatively, you can contribute to Avogadro and add your code directly into Git repository of Avogadro (but in this case your code must be under GPL or compatible license).

In theory, you may use any build system you like (e.g., hand-written Makefile). For successful build, Avogadro and Eigen2 headers must be in include path, and libavogadro must be linked with your library (if you use OpenBabel explicitly, take care of its headers and library too).

In practice, the simplest way to build plugin is to do it using CMake -- you don't need to worry about placement of Avogadro, OpenBabel and Eigen2 dependencies.







