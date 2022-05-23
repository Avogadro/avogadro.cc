---
title: "Avogadro 1.95 Released"
categories: News
author: ghutchis
date: 2021-08-16
---

We are very proud to announce the availability of Avogadro 1.95.0, the latest Beta
for Avogadro 2.0.

More can be found on the [1.95 release page](https://github.com/OpenChemistry/avogadrolibs/releases/tag/1.95.0) including downloads for Mac and Windows.

Thanks to many for suggestions, bug reports, and discussions.

This release includes many new features, including new protein ribbon / cartoon renderings and the new "Layer"
system as part of Google Summer of Code by @serk12.

Draft developer documentation can be found at https://two.avogadro.cc

If you have comments or suggestions, please join us at https://discuss.avogadro.cc and as always, help and contributions
in many forms are very welcome, **particularly if you'd like to help with user documentation.**


## ✨ Features

- New "Layer" system, including custom rendering, locking and hiding parts of the molecule @serk12 (#709)
- Atom and residue labels @serk12 (#715)
- New protein cartoon / ribbon display @serk12 (#660 #694 #716)
- Update render options for Wireframe and Ball-and-Sticks @ghutchis (#700 #720)
- Use MMTF downloads - more efficient than PDB format @ghutchis (#699)
- Add back support for importing crystals @ghutchis (#658 #659)
- Add CJSON support for save/load residues and atom colors @ghutchis (#646)
- Refactor of Python command and input generators, including tabs @ghutchis (#667)
- New View => Apply Colors menu @ghutchis (#640 #723)
- Apply color schemes for residues @ghutchis (#638 #688)
- Add more selection commands, including select by residue @ghutchis (#632 #634)
- Render selected atoms in VdW and licorice modes @ghutchis (#702)
- Detect secondary structure from residues / backbones @ghutchis (#685)
- Save enabled / disabled state of scene / rendering plugins on quit @ghutchis
- Should now download and install translations for @ghutchis

## 🐛 Bug Fixes

- Fix Mac builds by turning off COORDGEN library @ghutchis (#606)
- Fix Windows installer to include all needed files @ghutchis
- Save projection type on close #682 @ghutchis
- Add a pass to fix OB plugin library paths on Mac @ghutchis (#627 #628)
- Fix odd behavior on 'Center' command @serk12 (#728)
- Fix several crashes with proteins @ghutchis (#724 #726 #727)
- Fix crash in CJSON reading file without labels @ghutchis (#722)
- Fix bug deleting selected atoms #650 @ghutchis (#672 #677)
- Fix "delete last atom" bug @ghutchis (#691)
- When dragging to create a new atom, use starting coords @ghutchis (#690)
- Fix #679 - incorrect PDB unit cells @ghutchis (#689)
- Fixed problems inserting SMILES without coordinates @ghutchis (#661)
- Fix for transparent widgets @ghutchis (#656)
- Fix #602 - use Molden order for f-orbitals @ghutchis (#649)
- If a chain ID is missing / invalid, skip (to read non-standard PDB) @ghutchis (#647)
- Make sure to reset colors when changing elements @ghutchis (#708)

## 🧰 Maintenance

- Make sure to install crystals directory even when it exists @ghutchis (#613)
- Replace NULL/0 with nullptr @e-kwsm (#617)
- Add support for reading partial charge models from obabel @ghutchis (#626)
- Replace obsolescent `LINK_(PRIVATE|PUBLIC)` with `(PRIVATE|PUBLIC)` @e-kwsm (#629)
- Refactor Molecules class  @serk12 (#648)
- Don't install cclib script - which was removed @ghutchis (#662 #663)

## 📚 Translations

- Fix fuzzy entry for Nihonium (not Zirconium!) @e-kwsm (#618)
- Fix all incorrect fuzzy entries #619 @e-kwsm (#643)
- Remove wrong entries which were fuzzy @e-kwsm (#644)
- Translations update from Weblate @weblate (#625)
- Add a workflow which should update the translation template continuously @ghutchis (#624)

## Credits

Thanks to many contributors, including: @12emin34, @GicoProgram, @LihanzUpenn, @NathanBnm, @San4ito, @acunm, @alexrsoares, @danialk03, @dillonschultz93, @e-kwsm, @ghutchis, @grsousajunior, @psavery, @rezaalmanda, @serk12, @tacitcoast, @weblate, Eisuke Kawashima, Jacque Fresco and phlostically

If you use Avogadro or Avogadro 2, please consider citing the Avogadro paper: <http://www.jcheminf.com/content/4/1/17>
