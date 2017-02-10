---
layout: single
title: Water
categories: Teaching
---

Investigate the geometry of water and hydrogen bonding between molecules.

Task
====

Create one molecule of water, run energy minimization. Check the bond
length and angle between them.

Add another molecule. Run force field energy minimization. Check the bond
length on both molecules, and angles between bonds. Check how the molecules
are oriented to each other. Calculate energy of interaction,
pay attention to the role of hydrogen bonds. Measure deformation of
bonds.

Solution
--------

  Force field  | Bond length (Å) | Angle (°)
  ------------- | ---------------- | ----------
  GAFF         | 1.10            |  102.8
  Ghemical     | 0.95            |  109.5
  MMFF94(s)    | 0.97            |  104.0
  UFF          | 0.96            |  104.5                                 

According to [Wikipedia](http://en.wikipedia.org/wiki/Water_(properties)) the experimental O-H bond
length is 95.84nm and the interior H-H angle is 104.5°, so both MMFF94 and UFF perform reasonably.

![Hydrogen bond (yellow dashed line) between the two water molecules,
pay attention to the molecules
orientation](/images/Water_molecules.png)

Note that there is a significant electrostatic interaction between the positively charged hydrogen atom
and the oxygen on neighboring molecules.
![Electrostatic potential surface shows the bipolar nature of
water](/images/Water_molecules_with_electrostatic_potential.png)

Issues
------

Note that only the MMFF94 and MMFF94s force fields include hydrogen
bonding terms, so two water molecules may not attract each other using
other methods.

See also
--------

[HCN dipole](../hcn_dipole/)
