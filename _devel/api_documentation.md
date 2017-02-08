---
layout: single
title: API Documentation
categories: Developer
---



The *trunk* version of the Avogadro documentation is available at <http://avogadro.openmolecules.net/api/dev/>.

![](/images/Architecture.png)

There are four current interfaces for extending Avogadro

-   Engines -- These are responsible for the overall style of a rendered molecule: balls and sticks, van der Waals spheres, protein ribbons, etc.
-   Painters -- These are responsible for "painting" graphics and text from engines and tools, either to the screen (the default OpenGL view) or to a file (e.g., POV-Ray output)
-   Tools -- These allow user interaction with the mouse, for rotating and translating the view, editing, etc.
-   Extensions -- These are user-level commands, like selecting atoms, running a force field, or interfacing with an external program.



As indicated in the diagram, a scripting interface in Python exists, offering

-   A command-line terminal for interactive manipulation
-   API exposure for engines, painters, tools, and extensions from scripting languages
-   Embedding libavogadro into Python programs
-   Running script files, for example to send a molecule to a cluster

Of course in many cases, the engine, painter, and tool interfaces are performance-sensitive. Users want a fast, responsive user interface. Consequently, most of this code will likely be written in C++. However, access will be provided in scripting languages for easy prototyping and for general use.



The current painter interface is intended to be expanded to allow saving to SVG or other vector graphics formats (PS, PDF) and the use of GLSL shaders on supported systems.



