These are example LAMMPS input scripts for hybrid Monte-Carlo-Molecular-Dynamics simulations intended to determine the solidus and liquidus at a given pressure and temperature. More details can be located in the jounral article associated with this work (link here).

These scripts show two cases for establishing the intial solid-liquid coexistence needed to perform the MC-MD to determine the melting behavior. In the first case, the solid and liquid are able to coexist at the desired temperature with the same composition. In this case, the solid and liquid are established with the same composition, then during the simulation, their compositions will diverge to the soldius and liquidus.
In the second case, the solid and liquid cannot coexist at the desired simulation temperature (for example, in the case of instbaility of the solid solution). In this case, the solid and liquid start with the compositions of the endmembers, converging towards the solidus and liquidus.

These scripts can be executed in LAMMPS, but as written, require additional inputs. For both cases, these require the input of the equilibrium temperature and the output folder where it is desired for the results to be stored. The third required variable input is  the composition of the system in atomic fraction.

An example command to start the simulation might thus look like:

"mpirun -np 12 lmp_mpi -in type2.lmp -var frac 0.85 -var equil_temperature 1120 -var folder out"

this would run a simulation where the solid and liquid start as pure phases, at temperature 1120K and place the outputs of the simulation in the folder "out"
