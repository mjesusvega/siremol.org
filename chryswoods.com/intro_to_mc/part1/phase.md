
# Phase Changes

Now you have an understanding of how the Metropolis Monte Carlo program works, it is time to make it do something useful. Try to change the temperature, box size and maximum translation control variables so that you can make krypton crystallise into a solid. You should experiment by changing the variables, and then running the `metropolis.py` script.

(to help, the density of solid krypton is 2155 kg m-3, which is equal to 0.0155 krypton atoms per cubic angstrom. Krypton has a melting point of 115.79 kelvin)

For Monte Carlo to be efficient, you need about 40%-60% of the moves to be accepted. If too many moves are rejected, then reduce the value of `max_translate`. If too many moves are accepted, then increase `max_translate`.

Once you have promising values of the control variables (with an acceptable acceptance ratio), copy them into the C++ program `metropolis.cpp`. You can set the variables in the lines near the top of this program;

```c++
// Set the number of atoms in the box
const int n_atoms = 25;

// Set the number of Monte Carlo moves to perform
const int num_moves = 500000;

// Set the size of the box (in Angstroms)
const double box_size[3] = { 15.0, 15.0, 15.0 };

// The maximum amount that the atom can be translated by
const double max_translate = 0.5;  // angstroms

// Simulation temperature
const double temperature = 298.15;   // kelvin
```

The variables have the same name as in Python.

Compile the C++ program after every time you change these parameters by typing;

```
g++ -O3 metropolis.cpp -o metropolis
```

and then run the C++ program by typing;

```
rm output*.pdb
./metropolis
```

(note that you should remove the old `output???????.pdb` PDB files from each previous simulation before running each new simulation)

Once you have obtained solid krypton, use a spreadsheet to work out the average energy after equilibration.

***

# [Previous](control.md) [Up](README.md) [Next](ensemble.md) 
