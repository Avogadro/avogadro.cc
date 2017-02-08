---
layout: single
title: Python Molecule
---

# Python Molecule

Creating Molecules
==================

In short:

`mol = Avogadro.molecules.addMolecule()`

MoleculeList class
------------------

The MoleculeList class doesn't exist outside the python module. It is there to make it easier to write python scripts for Avogadro without having to worry about ownership. The class contains only a few methods and properties.

In the Avogadro python molecule there is an instance of this class defined as Avogadro.molecules.

`tim@ubuntu:~/avogadro-timvdm$ python`
`Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49) `
`[GCC 4.3.2] on linux2`
`Type "help", "copyright", "credits" or "license" for more information.`
`>>> import Avogadro`
`>>> help(Avogadro)`
`...`
`DATA`
`    molecules = `<Avogadro.MoleculeList object at 0x8997064>

To create a new molecule:

`mol = Avogadro.molecules.addMolecule()`

id vs. index
============

In Avogadro, all primitives (Atom, Bond, Residue, Cube, Mesh, ...) have both an id and an index. The **id is a unique value** for a given primitive. This means that ids are not reused and they can not be used to access a list by index. **Indexes** on the other hand can be used to access lists by index, they always go from **0** to **numAtoms-1**.

`>>> import Avogadro`
`>>> mol = Avogadro.molecules.addMolecule()`
`>>> for atom in mol.atoms:`
`...   print "atom"`
`...   print "  id =", atom.id`
`...   print "  index =", atom.index`
`... `
`atom`
`  id = 0`
`  index = 0`
`atom`
`  id = 1`
`  index = 1`
`atom`
`  id = 2`
`  index = 2`
`atom`
`  id = 3`
`  index = 3`

Iterating
=========

Methods which return QLists are converted to python lists automatically.

`...`
`for atom in molecule.atoms:`
`  print "atom id(", atom.id, ")"`
`for bond in molecule.bonds:`
`  print "bond ", bond.beginAtomId, "-", bond.endAtomId`
`...`

A few tips
----------

-   Always make sure your spelling is correct. There are situations where the python interpretor doesn't give you an error although the program doesn't behave as expected.

`>>> atom.atomicNumer = 6 # legal, just defining an extra attribute`
`>>> print atom.atomicNumer`
`6`
`>>> print atom.atomicNumber`
`0`

Deleting Molecules
==================

It is possible to delete molecules using the QObject.deleteLaster() function. However, unless you know what you are doing, this is not recommended.

`mol =`

<Category:Scripting>

