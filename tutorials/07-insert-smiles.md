---
layout: default
title: Tutorials:Insert SMILES
categories: Tutorials
---



Building with SMILES
====================

--screen capture showing menus--

[SMILES](http://en.wikipedia.org/wiki/SMILES), or simplified molecular input line entry specification, is a system for specifying a chemical structure on a single line. It looks a lot like a conventional condensed structure without the hydrogens. The official [SMILES manual](http://www.daylight.com/dayhtml/doc/theory/theory.smiles.html) is available at Daylight.

SMILES can be a convenient way to enter a structure. If the molecule is small, typing the SMILES may be easier than using the graphical interface. If the molecule is highly complex, e.g. morphine, building it from scratch may be difficult. If the SMILES string is available it makes an easy way to import the structure. The SMILES strings for many compounds are available on line at sites like [Wikipedia](http://en.wikipedia.org/wiki/Main_Page), [PubChem](http://pubchem.ncbi.nlm.nih.gov/) and [ChemSpider](http://www.chemspider.com/SimpleSearch.aspx).

The standard organic subset for SMILES includes B, C, N, O, P, S, F, Cl, Br, and I. Other elements, atoms with non-standard bond orders, or ions have their symbols given in square brackets, e.g. [Se], [NH4+]

straight chains
---------------

For simple chains with no branching, list the atomic symbols for the atoms. Hydrogens are not normally included, instead it is assumed that each atom has its normal number of bonds and Hydrogens are included accordingly. There can be more than one correct SMILES string for a given compound.

methane C

ethane CC

propane CCC

ethanol CCO or OCC

branching
---------

Any atom not part of the main chain is a branching group. Every branching group - even a single atom like Br - is enclosed in parentheses following the main chain atom to which it is attached. In SMILES with branching, the atoms without parentheses are the main chain.

`   isopropanol CC(O)C     or CC(C)O      or OCC(C)C`

`   2,2-dibromo propane CC(Br)(Br)C    or  BrC(C)(Br)C`

multiple bonds
--------------

double bonds between two atoms are shown with an equals sign, =

`   ethylene    C=C`

`   1-butene    C=CCC`

Cis and Trans double bonds can be indicated by putting a slash before and after the double-bonded atoms. If both slashes lean the same way, cis is indicated. If they lean opposite directions then trans is indicated.

cis 2-butene C/C=C/C

trans 2-butene C/C=C\\C

Triple bonds are indicated with a pound sign, \

`   acetylene   C

`   propyne     C

`   HCN     C

rings
-----

aromatic
--------

use lower case letters, or alternate single/double bonds

stereochem, isotopes, charges

Canonical and Isomeric SMILES

SMARTS for selecting substructures - same general idea

