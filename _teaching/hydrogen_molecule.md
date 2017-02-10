---
layout: single
title: Hydrogen Molecule
categories: Teaching
mathjax: true
---

Investigate the hydrogen molecule and bond length using different force fields.

Task
----

-   Create $$\ce{H2}$$ molecule using drawing tool.
-   Minimize energy, measure length of bond.
-   Enable display of it's orbitals.

Solution
--------

![](/images/Hydrogen_molecule.png)

Issues
------

Different force fields give different results:

| Force field | Bond length (Å)          |
|-------------|--------------------------|
| GAFF        | 1.10                     |
| Ghemical    | 1.01                     |
| MMFF(s)     | Cannot setup force field |
| UFF         | 0.71                     |


According to [1](http://hyperphysics.phy-astr.gsu.edu/hbase/molecule/hmol.html), accurate result is 0.074 nm, so the UFF force field should be used.

See also
--------

[Hydrogen cluster](../hydrogen_cluster)
