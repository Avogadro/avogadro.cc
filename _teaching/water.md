---
layout: single
title: Water
categories: Teaching
---

Task
====

Create one molecule of water, run energy minimization. Check bonds
length and angle between them.

Add another molecule. Run force field energy minimization. Check bonds
length on both molecules, and angles between bonds. Check how molecules
are oriented one relatively to another. Calculate energy of interaction,
pay attention to the role of hydrogen bonds. Measure deformation of
bonds.

Solution
--------

  -----------------------------------------
  Force field   Bond lenght, Å   Angle, °
                                 
  ------------- ---------------- ----------
  Ghemical      0.95             109.5
                                 

  MMFF(s)       0.97             104.0
                                 

  UFF           0.96             104.5
                                 
  -----------------------------------------

According to [Wikipedia
article](http://en.wikipedia.org/wiki/Water_(properties)) O-H bond
length is 95.84nm and the interior H-H angle is 104.5°.

![Hydrogen bond (yellow dashed line) between the two water molecules,
pay attention to the molecules
orientation](Water_molecules.png "fig:Hydrogen bond (yellow dashed line) between the two water molecules, pay attention to the molecules orientation")
![Electrostatic potential surface shows the bipolar nature of
water](Water_molecules_with_electrostatic_potential.png "fig:Electrostatic potential surface shows the bipolar nature of water")

Issues
------

Note that only the MMFF94 and MMFF94s force fields include hydrogen
bonding terms, so two water molecules may not attract each other using
other methods.

See also
--------

[HCN dipole]



