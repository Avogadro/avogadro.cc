---
layout: single
title: Hydrogen Molecule
categories: Teaching
mathjax: true
---

Task
----

-   Create $$\ce{H2}$$ molecule using drawing tool.
-   Minimize energy, measure length of bond.
-   Enable display of it's orbitals.

Solution
--------

![]("/images/Hydrogen molecule.png")

Issues
------

Different optimization mechanisms gives different results:

| Force field | Bond lenght, Å           |
|-------------|--------------------------|
| Ghemical    | 1.01                     |
| MMFF(s)     | Cannot setup force field |
| UFF         | 0.71                     |

According to [1](http://hyperphysics.phy-astr.gsu.edu/hbase/molecule/hmol.html), accurate result is 0.074 nm, so UFF force field should be used.

See also
--------

[Hydrogen cluster](Hydrogen cluster)



