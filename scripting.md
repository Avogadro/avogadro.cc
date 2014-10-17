---
layout: default
title: Scripting
---

# Scripting

There are many to use Python in Avogadro. This page gives an overview.

Introduction
============

The Avogadro python API resembles the [http://avogadro.cc/api/dev C++ API](http://avogadro.cc/api/dev C++ API "wikilink") as much as possible. This means that the C++ documentation also applies to python. However, there are some differences which are defined by the following rules.

-   Avogadro adopted the Qt libraries naming conventions for get/set methods. All methods start with a lowercase letter and new words start with a capital letter. Some examples are atomicNumber(), partialCharge(), numAtoms() and so on. These examples are in fact all get methods, they take no parameters and return something. Note that the "get" part is omitted from their names. Set functions on the other hand, all start with "set" followed by one or more words each starting with a capital letter. Again, some examples to illustrate this are setAtomicNumber(int), setPartialCharge(double).

<!-- -->

-   In python, get/set methods are replaced by class properties named after the get method.

`>>> print atom.atomicNumber`
`6`
`>>> atom.atomicNumber = 1`
`>>> print atom.atomicNumber`
`1`

-   Not all get/set methods can be replaced by properties, for these methods the python names remain unchanged.
    -   Set methods which return something
    -   Get & set methods which take more than 0 or 1 argument respectively.
    -   Set methods which have no get counterpart.

`>>> print molecule.atomPos(0) # print position of atom with id 0`
`[1.  2.  3.]`
`>>> molecule.setAtomPos(0, array([0.0, 0.0, 0.0])) `

-   The previous example already shows the use of array to specify an atom's position. If we look at the C++ API we'll see that the setAtomPos method accepts an Eigen::Vector3d object as second parameter. Eigen is the the library we use in C++ to do all math related stuff but python users can just replace this with an array from the numpy package. The array will be automatically converted by the Avogadro python module to and from python. There are four Eigen classes used in the API:
    -   Eigen::Transform3d: a 4x4 transformation matrix, used to manipulate the camera.
    -   Eigen::Vector3d: x,y,z vector, double precision. In python [numpy.]array([1.0, 2.0, 3.0])
    -   Eigen::Vector3f: same as Vector3d but float precision. For python users there is no difference between Vector3d and Vector3f.
    -   Eigen::Vector3i: x,y,z vector, integers. In python [numpy.]array([1, 2, 3])

`>>> import Avogadro`
`>>> import numpy`
`>>> molecule = Avogadro.Molecule()`
`>>> atom = molecule.newAtom()`
`>>> a.pos = numpy.array([1, 2, 3]) # Vector3d != Vector3i !`
`Traceback (most recent call last):`
`  File "`<stdin>`", line 1, in `<module>
`Boost.Python.ArgumentError: Python argument types in`
`    None.None(Atom, numpy.ndarray)`
`did not match C++ signature:`
`    None(Avogadro::Atom {lvalue}, Eigen::Matrix`<double, 3, 1, 0, 3, 1>`)`
`>>> a.pos = numpy.array([1., 2., 3.]) # valid (note the "." after each number to indicate float/double)`

Getting started
===============

-   Read the introduction above.
-   [Python Terminal](Tutorials:Console "wikilink"): How to use the python terminal. If you are a beginner, start here.
-   [Molecule class](Python_Molecule "wikilink"): How to create molecules, iterate over atoms, ids & indexes, ...

Intermediate
============

-   [PyQt4 integration](Python_PyQt4 "wikilink"): Explains how Avogadro integrates with PyQt4. While it is rather technical, it is highly recommended to read this page. It also explains how to work with signals and slots.

Advanced
========

These topics assume you know how to work with Molecules, Atoms, the GLWidget and other classes previously introduced.

Writing Plugins
---------------

-   [Python Extensions](Python_Extensions "wikilink"): Writing Python Extensions.
-   [Python Engines](Python_Engines "wikilink"): Writing Python Engines (also known as **Display Types**).
-   [Python Tools](Python_Tools "wikilink"): Writing Python Tools

Standalone
----------

<Category:Developer>

