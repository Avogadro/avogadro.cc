---
title: Building a Crystal Surface (Slab)
---

Build up a crystal surface, e.g., Pt <111> for a defined Miller Plane.

## Import the appropriate crystal structure.

![Import the appropriate crystal structure.][1]

[1]: ../images/2-building-a-crystal-slab/import-the-appropriate-crystal-structure.png

Either open a CIF file with the crystal structure needed, or import one from the built-in Avogadro crystal library. The tutorial will assume you import a structure from the Avogadro library. Choose File > Import > Crystal to bring up the library.

![][2]

[2]: ../images/2-building-a-crystal-slab/media_1332447195630.png

Either browse through the crystals, or type a filter -- by element or name. Click "Insert" to import the selected structure.

![][3]

[3]: ../images/2-building-a-crystal-slab/media_1332447360825.png

Importing a crystal will show the asymmetric unit cell (e.g., one atom for Silver here).

![][4]

[4]: ../images/2-building-a-crystal-slab/media_1332448938642.png

To build a specified surface (e.g., Ag <121>) choose Crystallography > Build > Slab... to bring up the slab builder settings. Future crystal builders (e.g., nanoparticles, supercells) will also appear in this menu.

![][5]

[5]: ../images/2-building-a-crystal-slab/3d1781c8-d8ba-45ce-af85-65625a1c4d24.png

Specify the indices of the Miller plane desired (for hexagonal unit cells, all 4 indices will appear), and choose the dimensions in either distances or repeating cells of the resulting surface. The generated surface is aligned in the XY plane, and a specified thickness will be cleaved in the z-axis below the XY plane. This feature allows easy alignment between a new surface and a molecule for surface interaction calculations. Click "Build" to start the surface generation.

![][6]

[6]: ../images/2-building-a-crystal-slab/media_1332468285179.png

After clicking "Build," Avogadro will generate a large supercell, align, rotate, and cleave the designated surface. This may take some time, depending on the size of the crystal cell. Here translucent van der Waals spheres are used to illustrate the corrugation of the Ag <121> surface. The resulting surface is a 2x2 supercell, with a large spacing (40 Å) in the z-axis.
