---
layout: default
title: Display Types
categories: Tutorials
---



This tutorial will deal with some display types of molecules including : *[Wireframe](/rendering/wireframe.html)*, *[Ball and Stick](/rendering/ball_and_stick.html)*, *[Cartoon](/rendering/cartoon.html)*, *[Ribbon](/rendering/ribbon.html)*, etc.

For this purpose we have chosen the [human insulin](http://en.wikipedia.org/wiki/Insulin) model to play with. But this work can be done with any other protein.

Getting started
---------------

-  Choose `File`&rarr;`Import`&rarr;`Fetch from PDB...` and enter "1hiu" to download the **1HIU** entry (insulin) from the Protein Data Bank (PDB).
-   The molecule will appear in the main panel with a default display type (previously chosen), for example, the [Ball and Stick](/rendering/ball_and_stick.html) mode as shown below:

![Ball and Stick display type - Grey: carbon, red: oxygen, blue: nitrogen, yellow: sulfur](/images/Avo_balls_and_sticks.png)

-   Optionally, hydrogen atoms can be removed using `Build`&rarr;`Remove Hydrogens` menu item.
-   In the **display types** menu (the left panel) you can see the available display types listed with checkboxes:

![Ball and Stick selected in display types panel](/images/Avo_balls_and_sticks_2.png)

![Atoms with the minimum radius](/images/1hiu.stik.png){:.some-css-class style="height:200px"} ![Atoms with the maximum radius](/images/1hiu.ball.png){:.some-css-class style="height:200px"}

-   By clicking on the **Settings** ![](/images/Properties_button.png) icon, you will have many choices such as:
    -   atom radius
    -   bond radius
    -   opacity (very useful if you want to superimpose many display types)
    -   display or not display of valence (double bonds)

![Ball and Stick settings](/images/Avo_balls_and_sticks_3.png)

Selecting and displaying residues
---------------------------------

-   Now we will visualize the protein residues or [amino acids](http://en.wikipedia.org/wiki/amino_acid).
    -   Select the **Stick** display type and deselect **Ball and Stick** or any others.
    -   Open Stick **settings** ![](/images/Properties_button.png)
    -   In **Colors** tab, choose *colorize according to residue* in the upper drop-down list and *amino acids* color pattern in the lower one. The result should be as below:

![*Stick* display type with highlighted amino acids](/images/Avo_balls_and_sticks4.png "Stick display type with highlighted amino acids")

-   In order to recognize residue names, we can add labels. To do so, select *Label* in the **display types** menu and in its **settings**![](/images/Properties_button.png) select *residue name* from *atoms label* drop-down list.

![Labels display.](/images/Avo_balls_and_sticks_5.png "Labels display.")

-   Now, let's try to visualize only one residue and identify its positions in this polypeptide chain. For this purpose, we will [select](03-making-selections.html) of a specific amino acid for example let's take the Leucine abbreviated as LEU. In **<u>S</u>election** menu choose **Select by Residue...**, write LEU in the output box and click **OK**. Then, in the **Objects** tab from the *Stick* **settings**![](/images/Properties_button.png) choose *display only selected primitives*. As a result, we should obtain the display of 6 Leucine residues:

![Displaying only Leucine residues](/images/Avo_balls_and_sticks6.png)

See also
--------

[Display Types documentation](/rendering/)
