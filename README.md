# Butanol-Phase-Separated-membranes

### Domain_Butanol

> Tan, L., Scott, H. L., Smith, M. D., Pingali, S. V., Cheng, X.,
> O’Neill, H. M., ... & Nickels, J. D. (2025).
> Toxic Effects of Butanol in the Plane of the Cell Membrane.
> Langmuir 2025, 41, 2, 1281–1296

Details of simulation can be found in the method section in this paper.

In these simulations, we utilized the 2023.2 version of gromacs.
Forcefield and topology files have been included.
To replicate the MD simulations we ran for this paper, you can excute the following
code.

```shell
# please input the path to the file you want to run
path="path_to_file"
gmx mdrun -o $path/step7.1.trr -s $path/step7.1.tpr \
-e $path/step7.1.edr -g $path/step7.1.log  -v -c step7.1.gro \
-cpo $path/state_step7.1.cpt -nb gpu -pme auto -pin on
```

This code will produce 50ns of production run.

To extend the production run, please excute the following code.

```shell
# please input the steps you want to extend for the production run
time_extend="steps_to_extend"
# please input the path to the file you want to run
path="path_to_file"
gmx mdrun -cpi $path/state_step7.1.cpt -o $path/step7.1.trr \
-s $path/step7.1.tpr -e $path/step7.1.edr -g $path/step7.1.log \
-v -c $path/step7.1.gro  -cpo $path/state_step7.1.cpt \
-nsteps $time_extend -nb gpu –pme auto -pin on -noappend
```

Analysis scripts can found in this
[link](https://github.com/jon33dn/Lipid-Membrane-Partitoning-Analysis---MD-Simulation)
