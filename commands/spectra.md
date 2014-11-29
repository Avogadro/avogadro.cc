---
layout: default
title: Spectra
categories: commands
---



![](Spectra.png "Spectra.png")

Spectra Extension
-----------------

The Spectra Extension displays spectra and other plotted data. Currently IR and NMR spectra are supported, and DOS, CD, and UV plots are on the way (pending a new release of OB).

Supported formats
-----------------

The output from the following codes are currently supported:



-   cml
-   qchem
-   nwchem
-   molpro
-   mopac
-   gaussian
-   gamess
-   molden
-   PWSCF/Quantum Espresso (Must be loaded with "Load Data" in the spectra window)
-   Turbomol control files (Must be loaded with "Load Data" in the spectra window)



Requires OB trunk

-   gamess



-   qchem
-   gaussian



Requires OB trunk and [dlonie's DOS branch](http://github.com/dlonie/avogadro/tree/DOS) of avogadro from github to work.

-   VASP



Requires OB trunk and [dlonie's DOS branch](http://github.com/dlonie/avogadro/tree/DOS) of avogadro from github to work.

-   Gaussian
-   Turbomol spectrum files (Must be loaded with "Load Data" in the spectra window)



Requires OB trunk and [dlonie's DOS branch](http://github.com/dlonie/avogadro/tree/DOS) of avogadro from github to work.

-   Gaussian
-   Turbomol cdspectrum files (Must be loaded with "Load Data" in the spectra window)

Usage
-----

The interface for the spectra dialog is easy to use, and advanced options can be hidden when not needed. The following options are shown at all times:



The actual plot. It is possible to manipulate the plot with the following commands:

-   double left click: Restore default plot limits
-   scroll: Zoom in/out
-   middle click: Zoom to region
-   left click: drag plot



The pulldown box in the bottom left corner is used to switch between different types of plot that may be present in the loaded molecule. If there are no spectra loaded, it simply says "No Data". If there is spectra data found in the molecule or loaded separately, it will list each by type. Selecting an entry updates the plot with the selected type.



Use this button to load spectra from external files. There does not need to be a molecule loaded in avogadro to use this feature. Supported types are:

-   PWscf (Quantum Espresso) IR data
-   Turbomol IR data



Shows/hides more advance options:



The options in this tab can be used to change the color, font, and shown spectra types (calculated and/or imported). It is also in this tab where users can import external plot data or export data in the following formats:

Import:

-   .tsv Tab Separated Values
-   .csv Comma Separated Values
-   .jdx JCAMP-DX files

Export:

-   .tsv Tab Separated Values

There is also a powerful color scheming engine here, allowing the user to save preset color and font themes for the plot window.



This tab allows the user to save the image on the plot to a file.



Each spectra type will load a new tab with options unique to the spectra (such as gaussian widening, shift factors, peak labels, etc). The options here are self explanitory.



