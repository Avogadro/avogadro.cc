---
layout: default
title: Tutorials:Display Types
---

# Tutorials:Display Types

This tutorial will deal with some display types of molecules including : *[Wireframe](Wireframe "wikilink")*, *[Ball and Stick](Ball and Stick "wikilink")*, *[Cartoon](Cartoon "wikilink")*, *[Ribbon](Ribbon "wikilink")*, etc.

Configuration: Avogadro version: 1.0.0

For this purpose we have chosen the [human insulin](http://en.wikipedia.org/wiki/Insulin) model to play with. But this work can be done with any other protein.

Getting started
---------------

-   First, download this `[http://www.biomed.curtin.edu.au/biochem/tutorials/pdb/1hiu.pdb 1hiu.pdb]` file.
-   [Open](Tutorials:Getting started#Opening_a_File "wikilink") the saved `1hiu.pdb` file with the menu **<u>F</u>ile \> <u>O</u>pen** or press **Ctrl+O**.
-   The molecule will appear in the **View 1** panel with a default display type (previously chosen), for example, the *[Ball and Stick](Ball and Stick "wikilink")* mode as shown below:

![*[Ball and Stick](Ball and Stick "wikilink")* display type - Grey: carbon, red: oxygen, blue: nitrogen, yellow: sulfur](Avo balls and sticks.png "Ball and Stick display type - Grey: carbon, red: oxygen, blue: nitrogen, yellow: sulfur")

-   To [navigate](Tutorials:Getting_started#Navigation "wikilink") switch to [Navigate Tool](Navigate Tool "wikilink") ![](Navigate.png "fig:Navigate.png") by choosing it from the toolbar or by pressing **F9**. Using the mouse or the keyboard, you can zoom, rotate and slide the molecule. To recenter the molecule in the field, choose **<u>V</u>iew \> Center** or **(shortcut ?)**.
-   Optionally, hydrogen atoms can be removed using *' <u>B</u>uild*' \> remove hydrogens.
-   In the **display types** menu (the left panel) you can see the available display types listed with checkboxes:

![*[Ball and Stick](Ball and Stick "wikilink")* selected in display types panel](Avo balls and sticks 2.png "Ball and Stick selected in display types panel")

![Atoms with the minimum radius](1hiu.stik.png "fig:Atoms with the minimum radius") ![Atoms with the maximum radius](1hiu.ball.png "fig:Atoms with the maximum radius")

-   By clicking on the **Settings** ![](Properties button.png "fig:Properties button.png") (the small wrench icon beside the display type) you can customize the appearance. For instance, the *[Ball and Stick](Ball and Stick "wikilink")* settings gives you many choices such as:
    -   atoms radius
    -   bonds radius
    -   opacity, very useful if you want to superimpose many display types
    -   display or not display of valence (double bonds)

![*[Ball and Stick](Ball and Stick "wikilink")* settings](Avo balls and sticks 3.png "Ball and Stick settings")

Selecting and displaying residues
---------------------------------

-   Now we will visualize the protein residues or [amino acids](http://en.wikipedia.org/wiki/amino_acid).
    -   select the *Stick* display type and deselect *[Ball and Stick](Ball and Stick "wikilink")* or any other
    -   Open Stick **settings** ![](Properties button.png "fig:Properties button.png")
    -   In **Colors** tab, choose *colorize according to residue* in the upper drop-down list and *amino acids* color pattern in the lower one. The result should be as below:

![*Stick* display type with highlighted amino acids](Avo balls and sticks4.png "Stick display type with highlighted amino acids")

-   In order to recognize residues names, we can easily display the labels. To do so, select *Label* in the **display types** menu and in its **settings**![](Properties button.png "fig:Properties button.png") select *residue name* from *atoms label* drop-down list.

![Labels display.](Avo balls and sticks_5.png "Labels display.")

-   Now, let's try to visualize only one residue and identify its positions in this polypeptide chain. For this purpose, we will make [selection](Tutorials:Making selections "wikilink") of a specific amino acid for example let's take the Leucine abbreviated as LEU. In **<u>S</u>election** menu choose **Select by Residue...**, write LEU in the output box and click **OK**. Then, in the **Objects** tab from the *Stick* **settings** ![](Properties button.png "fig:Properties button.png") choose *display only selected primitives*. As a result, we should obtain the display of 6 Leucine residues:

![Displaying only Leucine residues](Avo balls and sticks6.png "Displaying only Leucine residues")

See also
--------

[Display types documentation](:Category:Display "wikilink")

[Category: Tutorials](Category: Tutorials "wikilink")

