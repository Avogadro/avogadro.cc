---
title: LAMMPS input for water
---

## Prepare initial geometry

![Prepare initial geometry][1]

[1]: ../images/lammps-input-for-water/prepare-initial-geometry.png

The independently developed Packmol extension can be used to generate a box of water molecules.

## Open the LAMMPS input dialog

![Open the LAMMPS input dialog][2]

[2]: ../images/lammps-input-for-water/open-the-lammps-input-dialog.png



## Prepare simulation parameters

![Prepare simulation parameters][3]

[3]: ../images/lammps-input-for-water/prepare-simulation-parameters.png

1. Choose the number of repeating units of the input coordintes in x, y and z directions
1. Choose the water potential.  The current version supports SPC and SPC/E model potentials
1. Choose the name of LAMMPS formatted coordinates.  The name will be used in a later step when the lmpdat file is created.
1. Choose the total number of MD steps.
1. Choose the file name of the XYZ formatted trajectory file.

## Generate the LAMMPS parameters file

![Generate the LAMMPS parameters file][4]

[4]: ../images/lammps-input-for-water/generate-the-lammps-parameters-file.png

1. Click the Generate button
1. Choose a file name
1. Click save
1. Close the input generator dialog

## Generate the LAMMPS Coordintes file

![Generate the LAMMPS Coordintes file][5]

[5]: ../images/lammps-input-for-water/generate-the-lammps-coordintes-file.png

1. Select "Save As" from the file menu
1. Input the "water.lmpdat" file name from above
1. Select "All files"
1. Save the LAMMPS formatted coordinates file

## Run LAMMPS

![Run LAMMPS][6]

[6]: ../images/lammps-input-for-water/run-lammps.png

After 2700 time steps, the temperature is begining to stabilize.
