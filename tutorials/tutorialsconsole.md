---
layout: default
title: Tutorials:Console
---

# Tutorials:Console

Getting Started
===============

In case the python terminal is not visible, it can be made visible by checking the 'Settings \> Toolbars \> Python Terminal' checkbox.

![](Tut_console_1.png "Tut_console_1.png")

Once the python terminal is visible, the Avogadro module can be imported:

`>>> import Avogadro`

What to do next depends on what you are trying to achieve. However, we will go over some examples to cover the basics.

The Avogadro module
===================

python's help(...)
------------------

The python terminal resembles a real python terminal as much as possible. This means that you can always use help(...) to list classes, methods, data etc.

`>>> help(Avogadro)`
`Help on module Avogadro:`
`...`
`DATA`
`    molecule = `<Avogadro.Molecule object at 0x2128130>
`    molecules = `<Avogadro.MoleculeList object at 0x20a33d0>
`>>> help (Avogadro.Molecule)`
`...`

Avogadro.molecule and Avogadro.molecules
----------------------------------------

As can be seen in the output of help(Avogadro) above, the Avogadro python module has 2 DATA members. The first, Avogadro.molecule is the current molecule (i.e. the visible molecule). In many situations, you can directly use this to perform your task. For example, to clear the molecule:

`>>> Avogadro.molecule.clear()`

The molecule will automatically be updated when return is pressed (i.e. molecule.update() is called automatically).

If you need to create a new molecule, you can't directly construct one from python. Instead Avogadro.molecules should be used:

`>>> newMol = Avogadro.Molecule()     `**`#` `error`**
`Traceback (most recent call last):`
`  File "`<string>`", line 1, in `<module>
`RuntimeError: This class cannot be instantiated from Python`
`>>> newMol = Avogadro.molecules.addMolecule()   `**`#` `works`**

The Avogadro.molecules object is an instance of the MoleculeList class. This is a python specific class to make sure the molecules are not destroyed by python's garbage collection.

Iterating over atoms, bonds, ...
--------------------------------

Iterating over atoms, bonds and so on is easy as can be seen below. When a ':' character is found at the end of a line, the python terminal automatically indents the next line(s) and displays '...' instead of '\>\>\>'. To exit the loop, press return, leaving one row '...'.

`>>> for atom in Avogadro.molecule.atoms:`
`...   print atom.atomicNumber`
`...   `
`6`
`6`
`6`
`1`
`1`
`1`
`1`
`1`
`1`
`1`
`1`
`>>>`

Examples
========

