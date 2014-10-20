---
layout: default
title: Tutorials:Force fields
---

# Tutorials:Force fields

The OpenBabel library provides several force fields which can be used in Avogadro. For good results, it is important to select the right force field for a given molecule. Below you can find a list with the available force fields and the chemical families for which they were parameterized.

-   MMFF94(s): organic chemistry and drug-like molecules.
-   UFF: This force field can be used across the entire periodic table.
-   Ghemical: simple organic molecules

More information (links, references to articles, ...) can also be found on the [OpenBabel wiki](http://openbabel.org/wiki/Molecular_mechanics)

Common problems
===============

If you get strange geometries after optimizing, you should always check to make sure your using the right force field (see above). It is also important to realize that each force field has it's limitations. If you want to know more about each force fields strengths or weaknesses, you can

UFF
---

MMFF94(s)
---------

Among "monofunctional" chemical families, MMFF94 has been parameterized for alkanes, alkenes, alcohols, phenols, ethers, aldehydes, ketones, ketals, acetals, hemiketals, hemiacetals, amines, amides, peptide analogs, ureas, imides, carboxylic acids, esters, carboxylate anions, ammonium cations, thiols, mercaptans, disulfides, halides (chlorides and fluorides), imines, iminium cations, amine N-oxides, hydroxylamines, hydroxamic acids, amidines, guanidines, amidinium cations, guanidinium cations, imidazolium cations, aromatic hydrocarbons, and heteroaromatic compounds.

MMFF94 and MMFF94s both use the same functional form to calculate the potential energy. They only differ in the Torsion and Out-Of-Plane bending parameters used. The 's' in MMFF94s stands for static and this set of parameters is more suited for tasks where the output is static. This can easily be remembered when you think of the output of an energy minimization as a static result (only one geometry). A dynamic result would be a the trajectory of a molecular dynamics simulation.

### Nitro groups

Nitro groups have to be drawn using a single and double bond. If you draw a double bond to both oxygen atoms, force field setup will fail. ![nitromethane](nitromethane.png "fig:nitromethane")
 --figure nitro --

### Sulfone groups

The S-O bonds in sulfone groups have to be single. ![dimethylsulfone](sulfone.png "fig:dimethylsulfone")
-- figure sulfone --

<Category:Tutorials>

