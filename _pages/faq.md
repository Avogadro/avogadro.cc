---
layout: single
title: Frequently Asked Questions
permalink: /faq/
---

{% include toc %}

# General

1.  Does Avogadro work on platform X?

    Avogadro can be downloaded for Windows, Mac OS X & Linux and should work on most other Unix systems which support the Qt package. At the moment, we do not support tablets, smartphones, etc. (i.e., iOS, Android, or Windows phone) but these are being considered for future releases.

2.  What about PyMol or VMD or [insert your favorite program here]?

    Many of these programs are our favorites too. We use them. But PyMol and VMD are largely limited to being viewers. If you view biomolecules, use PyMol. If you do molecular dynamics, use VMD. If you need to build a molecule, protein, or crystal, please consider Avogadro.

# Scripting

1.  Does Avogadro support scripting?

    Yes, Avogadro 1.0 has support for Python. Other languages may be considered for future versions.

2.  Can I use libavogadro from a Python standalone script?

    Yes, but this currently only works on Linux. On Windows, the Python interpreter used is not the same as the python installed (if any). Compiling Avogadro on Windows and running the Python interpreter from the Avogadro directory should make this work too. If requested, we can see wether we can ship python.exe in future versions for this purpose.

3.  Why doesn't the Mac version support Python?

    We're currently working on how to package Python support for the Mac, since Apple changes versions of Python with every OS release.

# Known Issues

1.  Avogadro crashes when clicking inside draw area in Linux

    If you are using NVidia graphics card with Nouveau driver, uninstall it and switch to proprietary NVidia driver or open source nv driver

2.  Avogadro freezes when trying to draw molecule in Linux

    Try to change your Qt widget style, for example, to Oxygen. Some styles are known to be buggy, maybe you are using one of them.

3.  What is an "engine?"

    In older versions (before 0.8), Avogadro had "rendering engines" or just "engines" which dictated the objects which appeared on the screen. In more recent versions, these are called "display types" or "[displays](/rendering/)."

4.  Why does insert smiles give the wrong stereoisomer?

    This is a bug in OpenBabel. You should make sure you have a recent version.
