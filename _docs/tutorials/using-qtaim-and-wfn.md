---
title: Using Atoms-In-Molecules (Bader) Analysis - QTAIM and WFN
---

Avogadro now includes support for the QTAIM analysis developed by Prof. Richard Bader and his group. This technique allows Avogadro to determine bond connections and bond orders directly from the quantum mechanical electron density.

## Start with a WFN File

![Start with a WFN File][1]

[1]: ../images/1-using-qtaim-and-wfn/start-with-a-wfn-file.png

Most quantum chemistry software allows creating a WFN format file from the output of a calculation. We can read this file in through the QTAIM Extension for visualization and analysis. In the future, other formats will also be supported, including deriving the data directly from checkpoint files.

![][2]

[2]: ../images/1-using-qtaim-and-wfn/media_1340250901000.png

Here we've picked a WFN file of interest (HCO2) using the Molecular Graph + Lone Pairs command.

![][3]

[3]: ../images/1-using-qtaim-and-wfn/media_1340250954094.png

Avogadro's QTAIM support will read in the atoms, determine bonds and bond orders using AIM analysis and then continue with further analysis.

![][4]

[4]: ../images/1-using-qtaim-and-wfn/media_1340251076292.png

Initially, you may not see anything different. QTAIM includes a separate Display Type for viewing the results of the AIM analysis.

![][5]

[5]: ../images/1-using-qtaim-and-wfn/media_1340251126011.png

Here, we've enabled the QTAIM display, which will show lone pairs, bond critical points, etc. You may also want to turn off the Ball and Stick model to see all AIM annotations.

![][6]

[6]: ../images/1-using-qtaim-and-wfn/media_1340251283231.png

Here, we've also turned off the classical ball and stick display type to leave only the QTAIM view of HCO2.
