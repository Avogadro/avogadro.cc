---
layout: post
title: "Avogadro 1.2 Released"
modified:
categories: News
excerpt:
tags: []
image:
  feature:
date: 2016-06-15
---

We are very proud to announce the availability of Avogadro 1.2.0

Avogadro is a free, open source, cross-platform molecular editor
designed for flexible use in computational chemistry, molecular
modeling, bioinformatics, materials science, and related
areas.

This release marks a new stable release of Avogadro. It fixes countless bugs and adds important new features as we work on Avogadro v2.

Download: <https://sourceforge.net/projects/avogadro/files/latest/download>

Key Updates with 1.2.0:
- Support for the ORCA quantum chemistry package, thanks to Dagmar Lenk, including input generation and output parsing
- Improved support for MO calculations, including orbitals with F, G, H, and I angular momentum, thanks to Dagmar Lenk and Albert DeFusco
- Support for exporting VRML models of atoms, bonds, surfaces, and orbitals (e.g. for 3D printing), thanks to Ethan Pavolik
- Support for perceiving molecular symmetry on Mac and Linux using the libmsym library (i.e., Properties -> Symmetry), thanks to Marcus Johansson
- Updated links to the new Avogadro website <http://avogadro.cc/>, manual <http://manual.avogadro.cc/>, and discussion forum <http://discuss.avogadro.cc/>
- Fixed support for compiling with the Eigen3 library up to version 3.2.8
- Improved support for space groups through spglib
- Updated translations, now including over 25 languages in addition to English
- Fixed a bug downloading from the Protein Data Bank
- Fixed a bug fetching molecules from the network, including the "chemical by name"
- Fixed a bug when naming molecules from the NIH chemical resolver website

We anticipate several more new releases of Avogadro v1 before we finish Avogadro 2.0 by the end of 2016.

This is a community project and we couldn't have made this release without you. Many thanks to all the contributors to Avogadro including those of you who submitted feedback, bug reports, and code. Particular thanks go to all the translators.

For more information: <http://avogadro.cc/>

If you use Avogadro please consider citing the Avogadro paper: <http://www.jcheminf.com/content/4/1/17>
