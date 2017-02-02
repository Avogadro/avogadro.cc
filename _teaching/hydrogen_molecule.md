---
layout: default
title: Hydrogen Molecule
categories: Teaching
---

Task
----

-   Create H<sub>2</sub> molecule using drawing tool.
-   Minimize energy, measure length of bond.
-   Enable display of it's orbitals.

Solution
--------

![](Hydrogen molecule.png "Hydrogen molecule.png")

\_\_NOTOC\_\_

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

[Hydrogen cluster](Hydrogen cluster "wikilink")



