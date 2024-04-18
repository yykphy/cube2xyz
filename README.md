Transform .cube of Qchem and Gaussian file to x y z value (yk modified version)
==========================

cube2xyz can convert Gaussian type Cube files into "x y z value" columns, or project values on planes (slizes) or segments. Optionally, it can directly produce the plot for a faster visualization.

.cube files are originally from the Gaussian molecular modeling code, but nowadays can be produced and read by most of the computational chemistry programs. They consist of a lot of blocks of data describing the values of a measured property (charge, spin polarization, electronic density, …) on each point of the space inside the simulation cell.

The cube files are formatted as follows:

- 1st and 2nd lines: comment/free text

- 3rd line: Total number of atoms, and xyz coordinates of the origin of the volume data

- 4th to 6th line: number of voxels (partition points) for each axis followed axis vectors. If the number of voxels is possitive the units are in Bohr if it is negative in Angstrom.

- 7th to No. of atoms: atom number, no. of electrons and xyz coordinates for each atom

- from there to the EOF: blocks of n voxels in xyz containing the value of the property measured in the cube file


Let us think that we want to simulate an isolated molecule in vacuum, but we are not sure of whether our simulation box is large enough to prevent interactions with periodic replica. In this case, we can use the cube2xyz script to plot the data and check that a given magnitude (for example charge, electronic density…) is converged around the molecule.

The command used was:

```python3 cube2xyz-v0.1.py -f input.cube -o xyzspol.dat -x 1 -pl -A```

The usage information can be as usual obtained with the -h option on the command line, and in this case, it looks like:


```
usage: cube2xyz-v0.1.py [-h] -f FILE_NAME [-o OUT_FILE] [-pr PRINT_RANGE]
[-x X_COORD] [-y Y_COORD] [-z Z_COORD] [-pl] [-A]
[-no]cube2xyz can convert Gaussian type Cube files into “x y z value” columns, or
project values on planes (slizes) or segments. Optionally, it can directly
produce the plot for a faster visualization.
optional arguments:
-h, –help show this help message and exit
-f FILE_NAME, –file_name FILE_NAME
Name of cube file
-o OUT_FILE, –out_file OUT_FILE
Name of the file to which print the output (otherwise
printed to Standard Output).
-pr PRINT_RANGE, –print_range PRINT_RANGE
Print the range of x,y or z values and exit.
-x X_COORD, –x_coord X_COORD
Show only the values of x at this point.
-y Y_COORD, –y_coord Y_COORD
Show only the values of y at this point.
-z Z_COORD, –z_coord Z_COORD
Show only the values of z at this point.
-pl, –plot Plot graph using Mathplotlib.
-A, –angstrom Convert all distances to Angstrom.
-no, –no_output Do not produce any outupt.

Usage: cube2xyz -f out.spol.cube -o xyzspol.dat -x 3.1 -pl -A
```


All above are from
```https://blog.larrucea.eu/cube2xyz/```