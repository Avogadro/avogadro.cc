---
layout: default
title: Tutorials:Making selections
categories: Tutorials
---



Introduction
============

Making selections is an important operation when using Avogadro.

-   Deleting the selection
-   Using Display Types for parts of the molecule
-   Adding hydrogens to only the selected atoms
-   Moving the selected items in space
-   ...

There are several ways to make selections. However, the easiest or quickest way often depends on the task you are trying to accomplish. While the selection methods in this tutorial are organised in 3 sections, you can (and are encouraged) to mix these methods while working with Avogadro.

Before continuing this tutorial, make sure all **necessary plugins** are enabled. If you just installed Avogadro these will be enabled by default. Otherwise you can use the video below to help you enabling the **Selection Tool** and **Selections Extension**. Setting up the project three will be explained later.

<videoflash>Y\_buZIJ2dz8</videoflash>

Selections Extension
====================

![Figure 1: The Select menu.](tut_select_menu.png "fig:Figure 1: The Select menu.") The "Selections" Extension provides many selection methods accessible through the Select menu. Since the first two items are frequently needed, short-cuts are provided.

`Select All  `**`Ctrl+A`**
`Select None  `**`Ctrl+Shift+A`**

At any point, you can **delete** the currently selected items by pressing the **Backspace** key.

Invert Selection
----------------

Inverting the current selection is often useful when making selecting which will be assigned to display types (see next tutorial). For example, if you have selected all ligands in a protein complex and assigned it to a display type (e.g. Stick). Inverting the selection will select the protein which can then be assigned to a different display type (e.g. Simple Wireframe)

Select SMARTS
-------------

[http://www.daylight.com/dayhtml/doc/theory/theory.smarts.html SMARTS](http://www.daylight.com/dayhtml/doc/theory/theory.smarts.html SMARTS "wikilink") are usually used for subgraph searching. The select SMARTS function in Avogadro selects all matched atoms in the molecule. All [http://www.daylight.com/dayhtml/doc/theory/theory.smiles.html SMILES](http://www.daylight.com/dayhtml/doc/theory/theory.smiles.html SMILES "wikilink") are valid [http://www.daylight.com/dayhtml/doc/theory/theory.smarts.html SMARTS](http://www.daylight.com/dayhtml/doc/theory/theory.smarts.html SMARTS "wikilink"):

`SMILES      Description`
`C(=O)O      select all carboxylic acids, esters, ...`
`N           select all aliphatic nitrogen atoms`
`n           select all aromatic nitrogen atoms`
`n1ccccc1    select all atoms in pyridine rings`

[http://www.daylight.com/dayhtml/doc/theory/theory.smarts.html SMARTS](http://www.daylight.com/dayhtml/doc/theory/theory.smarts.html SMARTS "wikilink") are much more powerful though. Here are some examples using SMARTS that cannot be expressed as a single SMILES:

`SMARTS      Description`
`a1aaaa1     select all aromatic atoms in 6 membered rings`
`A           select all aliphatic atoms`
`[O,N][

More information on how to write SMILES and SMARTS strings can be found here:

[http://www.daylight.com/dayhtml/doc/theory/theory.smiles.html SMILES - A Simplified Chemical Language](http://www.daylight.com/dayhtml/doc/theory/theory.smiles.html SMILES - A Simplified Chemical Language "wikilink") [http://www.daylight.com/dayhtml/doc/theory/theory.smarts.html SMARTS - A Language for Describing Molecular Patterns](http://www.daylight.com/dayhtml/doc/theory/theory.smarts.html SMARTS - A Language for Describing Molecular Patterns "wikilink")

Select by Element
-----------------

![Figure 2: Select by Element.](tut_select_element.png "fig:Figure 2: Select by Element.") Clicking the "Select by Element..." action will show a periodic table. Clicking any of the elements in the table will select all atoms for which the atomic number matches the clicked element.

Select by Residue
-----------------

![Figure 3: Select by Residue.](tut_select_residue.png "fig:Figure 3: Select by Residue.") This option allows you to select all residues with a specified residue name (e.g. **"VAL"**, **"TYR"**, ...). While the VAL and TYR example might not be of great value, this option can often be useful for selecting ligands with a known name. For example, the 1DRF.pdb protein contains a folate molecule with residue name FOL.

1DRF.pdb:

`...`
`HET    `**`FOL`**`  A 187      32                                                       `
`...`
`HETNAM     `**`FOL`**` FOLIC ACID                                                       `
`...`
`FORMUL   4  FOL    C19 H19 N7 O6                                                `
`...`
`ATOM   1508  N1  `**`FOL`**` A 187      26.779  12.325  -3.996  1.00  0.00           N  `
`ATOM   1509  C2  `**`FOL`**` A 187      27.684  12.453  -5.033  1.00  0.00           C  `
`ATOM   1510  NA2 `**`FOL`**` A 187      27.113  12.270  -6.218  1.00  0.00           N  `
`...`

Uisng the select by residue option, it is easy to select the ligand. Once selected, a display type can be assigned to the ligand. When using the cartoon display type for proteins, selections are rendered as wireframe in the selection color (Figure 3).

Select Solvent
--------------

Currently, only residues with the name **HOH** are selected.

Selection Tool
==============

While all previous select methods didn't involve the 3D widget directly, clicking on atoms and bonds to make selections is possible using the Selection Tool. The selection tool has **3 modes**:

-   **Atom/Bond**: Select the clicked atom/bond
-   **Residue**: Select the residue to which to clicked atom/bond belongs. This only works for molecules with residues like proteins for example. Both the atoms and the bonds of the residue will be selected.
-   **Molecule**: Select all atoms and bonds connected to the clicked atom/bond.

The **Atom/Bond** mode is exclusive without using modifier keys. This means when you click various atoms consecutively, only the last will be selected. This behaviour can be changed by holding the **Shift** (or **Ctrl**) modifier key while clicking the atom/bond.

-   **Shift** (Add modifier): Select additional atom/bond without deselecting any previous selection. When clicking on an already selected atom, this has no effect.
-   **Ctrl** (Toggle modifier): Same as **Shift** but deselects a selected atom/bond when clicking on it.

Both **Residue** and **Molecule** mode work in a toggle like way. Clicking a previously unselected residue/molecule will select it, clicking it again will deselect it. (note: these modes don't use modifier keys)

There is one more option for making selections using this tool. Left clicking on an empty space in the 3D widget and moving the mouse cursor will draw a **selection box**. When the mouse button is released, all atoms and bonds inside the box will be selected. The modifier keys can also be used with selection boxes:

-   **Shift** (Add modifier): Select additional atom/bond without deselecting any previous selection.
-   **Ctrl** (Exclusive modifier): Select only the atoms and bonds within the box. Previous selections will be deselected.

Right click on empty space clears the selection.

Named Selections
================

![Figure 4: Named selections in the project tree.](tut_select_projecttree2.png "fig:Figure 4: Named selections in the project tree.") Once a selection has been made, it can often be useful to make it a named selection using **Select \> Add Named Selection...**. This allows for quick reselection later using the Project Tree.

Selecting and the Project Tree
==============================

![Figure 5: Configuring the project tree.](tut_select_projecttree1.png "fig:Figure 5: Configuring the project tree.") ![Figure 6: Named selections in the project tree.](tut_select_projecttree3.png "fig:Figure 6: Named selections in the project tree.") If the project tree is not visible, it can always be made visible again using **Settings \> Toolbars \> Project Tree**. If the project tree is empty, items can be added using **Settings \> Configure Avogadro...** (Figure 5). This only needs to be done once, the settings will be stored for later sessions. Some of the items you can add are '''User Selections, **Molecule**, **Atoms**. In the real project tree, these items will expand and contain the actual selections, residues, items and so on. Double clicking an item will select the matching atoms, bonds, ... (Figure 6).

