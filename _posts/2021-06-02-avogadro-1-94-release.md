---
title: "Avogadro 1.90.0 Released"
categories: News
author: cryos
date: 2016-12-02
---

We are very proud to announce the availability of Avogadro 1.95.0, the latest Beta
for Avogadro 2.0.

More can be found on the [1.94 release page](https://github.com/OpenChemistry/avogadrolibs/releases/tag/1.94.0) including downloads for Mac and Windows.

As part of the release, we've made it easier to download scripts and data,
including new input generators, molecule fragments, and build and analysis
commands. These scripts make it much easier to integrate Avogadro with many
open source chemistry Python tools, including RDKit, ASE, etc.

Draft developer documentation can be found at <https://two.avogadro.cc>

If you have comments or suggestions, please join us at <https://discuss.avogadro.cc>

We anticipate several more releases over the summer and early fall 2021.

## Features

- Bring back "insert framgent" builder from Avogadro v1 @ghutchis (#591)
- New docs on http://two.avogadro.cc @ghutchis (#568)
- Remove dependency on MoleQueue @cryos (#596)
- Initial Flatpak package @kevinsmia1939
- Improved download widget @ghutchis (#534)
- Reorganize menus - fix #474 @ghutchis (#564)
- Export to SVG @serk12 (#588)
- Symmetry enhancements @ghutchis (#553)
- Added yaehmop with band structure calc @psavery (#339)
- Cp2k input @ghutchis (#383)
- OpenMM script builder plugin @badarsh2 (#343)
- Handle drag-and-drop of files to the window @ghutchis
- Use native message / dialog boxes on Mac @ghutchis
- Download entries from PDB @ghutchis (#575)
- Allow manipulate to rotate selected fragments @ghutchis (#594)
- Add bestFitPlane on Molecule @dvermd (#500)
- Add centerOfGeometry, centerOfMass and radius methods on Molecule @dvermd (#499)
- Reset view (camera) @serk12 (#450)
- Transparent support for ASE "extended XYZ" files @ghutchis (#603)

## 🐛 Bug Fixes

- Switch to using Python 3, fixing #431 @ghutchis (#462)
- Switch Open Babel calls to use CML and non-local numeric format (#471)
- Save background color across sessions and set bg alpha for export @ghutchis
- Add support for cut/copy/clear selected atoms @ghutchis (#510)
- Label toolbar windows for context menu @ghutchis
- Make sure to send Extensions the setActiveWidget call @ghutchis
- Make sure to install Qt image plugins on Mac and Windows @ghutchis
- Fix #483 through stream-specific locale @ghutchis (#549)
- Fix a pile of rendering bugs on high-res by saving viewport @ghutchis (#556)
- Adjust font size for 2D measure labels on hires screens @ghutchis (#548)
- Make sure to check movie sizes for high-dpi screens @ghutchis (#570)
- Fixes silent export on save bug #439 @anubh4v (#517)
- Switch to the navigate tool after pasting coordinates over empty @ghutchis (#593)
- Fix #571 - ensure we read Gaussian files from file, not stream @ghutchis (#592)
- Fix symmetry detection with dummy atoms (e.g, ferrocene example) @ghutchis (#595)

## 🐍 Python Improvements

- Add support for a JSON list of selected atoms @ghutchis (#440)
- Simplify wheel building @psavery (#520)
- Update example Avogadro RPC script @ghutchis

## 🧰 Maintenance

- Switch to using GitHub actions for continual builds @ghutchis (#461)
- Translations update from Weblate @weblate
- Get rid of bits/stdc++ headers - non-portable GCC header @ghutchis (#463)
- Add fedora patches @ghutchis (#460)
- Allow use of HDF5 >= 1.12.0 @berquist (#488)
- Remove exit calls from qtaim code @ghutchis (#475)
- Switch to include spglib.h with no subdir - fixes build issues @ghutchis (#533)
- Update residues from LigandExpo @ghutchis (#572)
- Make VtkPlot more object-oriented @psavery (#379)

## Credits

Thanks to many contributors, including: @Andre870-hub, @ImgBotApp, 
@KovalevArtem, @NathanBnm, @Padanian,
@Pietro026, @SantosSi, @SoftwareByRedline, @VeryTastyTomato, @Z-Fikar,
@Zaryob, @adreasnow, @ahmadubuntu, @akyunus, @amandadumi,
@andhikapangestu29, @anubh4v, @badarsh2, @berquist, @borisfaure,
@comradekingu, @crlambda, @cryos, @dnandz, @dvermd, @ghutchis,
@grsousajunior, @hello-malaysia, @imgbot, @joanavieira8,
@kevinsmia1939, @koffevar, @ludovicobesana, @mirosnik1, @niskala5570,
@psavery, @rezaalmanda, @serk12, @shivupa, @tacostea, @tiagomalho,
@udopton, @weblate, @willow88, @yavgech, Alex, Apostol Penkov, Editor
Do Sonic BR, Irina Puscas, J. Lavoie, Jacque Fresco, Jörg S, Kavin
Teenakul, Liu Tao, Michalis, My Random Thoughts, Oğuz Ersen, RIDHO
NURUL ADILLA, Szabolcs Kalapos, Talking Panda, Thomas Koller, Tymofij
Lytvynenko, fikril Ha, phlostically, rahul bahuguna


If you use Avogadro or Avogadro 2, please consider citing the Avogadro paper: <http://www.jcheminf.com/content/4/1/17>
