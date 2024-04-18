Transform .cube of Qchem and Gaussian file to xyz
==========================

.cube files are originally from the Gaussian molecular modeling code, but nowadays can be produced and read by most of the computational chemistry programs. They consist of a lot of blocks of data describing the values of a measured property (charge, spin polarization, electronic density, …) on each point of the space inside the simulation cell.

The cube files are formatted as follows:

1st and 2nd lines: comment/free text
3rd line: Total number of atoms, and xyz coordinates of the origin of the volume data
4th to 6th line: number of voxels (partition points) for each axis followed axis vectors. If the number of voxels is possitive the units are in Bohr if it is negative in Angstrom.
7th to No. of atoms: atom number, no. of electrons and xyz coordinates for each atom
from there to the EOF: blocks of n voxels in xyz containing the value of the property measured in the cube file
Let us think that we want to simulate an isolated molecule in vacuum, but we are not sure of whether our simulation box is large enough to prevent interactions with periodic replica. In this case, we can use the cube2xyz script to plot the data and check that a given magnitude (for example charge, electronic density…) is converged around the molecule.

The command used was “python3 cube2xyz-v0.1.py -f input.cube -o xyzspol.dat -x 1 -pl -A”.