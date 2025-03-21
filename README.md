These are example LAMMPS input scripts for hybrid Monte-Carlo-Molecular-Dynamics simulations intended to determine the solidus and liquidus at a given pressure and temperature. More details can be located in the jounral article associated with this work (link here).

These scripts show two cases for establishing the intial solid-liquid coexistence needed to perform the MC-MD to determine the melting behavior. In the first case, the solid and liquid are able to coexist at the desired temperature with the same composition. In this case, the solid and liquid are established with the same composition, then during the simulation, their compositions will diverge to the soldius and liquidus.
In the second case, the solid and liquid cannot coexist at the desired simulation temperature (for example, in the case of instbaility of the solid solution). In this case, the solid and liquid start with the compositions of the endmembers, converging towards the solidus and liquidus.

These scripts can be executed in LAMMPS, but as written, require additional inputs. For both cases, these require the input of the equilibrium temperature and the output folder where it is desired for the results to be stored, for certain output files, the name of the folder is also appended to the front of the output name. The third required variable input is the composition of the system in atomic fraction. In the type one case (CuNi), the solid and liquid are both created with this composition. In the type 2 example (AuSi), the liquid is created as pure Au and the solid as pure Si, but with each region taking up the appropriate fraction of the box. For a Si fraction of 0.85, the first 0.15L of the box is filled with Au atoms and the remaining 0.85L of the box is populated with Si atoms. Because the atoms are all populated on the same lattice with the same lattice parameter, the volume and molar fractions of the starting condition are equivalent; however, this does not remain true once melting occurs. For the multicomponent case, the Cantor ally (equiatmic CrMnFeCoNi) is simulated chemically homogeneous solid and liquid. The example for a many component system is given as multicomponent.lmp.

An example command to start the simulation might thus look like:

"mpirun -np 12 lmp_mpi -in type2.lmp -var frac 0.85 -var equil_temperature 1120 -var folder AuSi_85_1120"

this would run a simulation where the solid and liquid start as pure phases, at temperature 1120K and place the outputs of the simulation in the folder "AuSi_85_1120"

Please note that the desired folder must exist prior to executing the LAMMPS script

The AuSi potential was developped by Starikov and colleagues and should be cited as:
  S.V. Starikov, N.Y. Lopanitsyna, D.E. Smirnova, and S.V. Makarov (2018), "Atomistic simulation of Si-Au melt crystallization with novel interatomic potential", Computational Materials Science, 142, 303-311. DOI: 10.1016/j.commatsci.2017.09.054.

The Cu-Ni potential was developped by Sheng and colleagues and should be cited as: 
  H.W. Sheng, M.J. Kramer, A. Cadien, T. Fujita, M.W. Chen, Highly optimized embedded-atom-method potentials for fourteen fcc metals, Physical Review B 83 (13)(2011) 134118.
  
The CrMnFeCoNi potential was developped by Choi and colleages, and should be cited as:

 W.M. Choi, Y.H. Jo, S.S. Sohn, S. Lee and B.J. Lee (2018), "Understanding the physical metallurgy of the CoCrFeMnNi high-entropy alloy: an atomistic simulation study" npj Computational Materials 4 1


