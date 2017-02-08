---
title: Crystal Symmetry Perception
---

Calculation results often specify all atoms and translation vectors, but not the space group. Here we see how to perceive the space group from a set of crystallographic coordinates.

## Open a Crystal File

![Open a Crystal File][1]

[1]: ../images/4-crystal-symmetry-perception/open-a-crystal-file.png

Here we open an example VASP calculation by opening the POSCAR file.

![][2]

[2]: ../images/4-crystal-symmetry-perception/media_1340332954652.png

This example is triclinic, looking for L.. structures. Note that VASP files do not specify a space group, so it is reported as "Unknown."

![][3]

[3]: ../images/4-crystal-symmetry-perception/media_1340332967365.png

We can either set the spacegroup manually, or here, perceive the space group, using the open source spglib code.

![][4]

[4]: ../images/4-crystal-symmetry-perception/media_1340332976902.png

We need to set the tolerance, since some atoms may be slightly out of place in Cartesian coordinates.

![][5]

[5]: ../images/4-crystal-symmetry-perception/media_1340332995909.png

Our example VASP file isn't very interesting -- the space group is P1.

![][6]

[6]: ../images/4-crystal-symmetry-perception/media_1340333044109.png

Here's another example, where the space group is P 1 21 1.
