# hZIP8
MD simulation files for human ZIP 8 helical bundle 4M variant Zn over Cd selection
Open source restriction claim: The licensed PMEMD.cuda program from AMBER20 is needed; other programs, such as tLEaP, ParmEd (these two are available in the free AMBER20AmberTools20), and SLURM job scheduler, are open source. 

To run the code, please follow the steps below: 
1. Install AMBER 20, and then place all the files in a new directory with at least 100GB available disk space.
2. Run "tleap -s -f tleap.in". This will generate PARM7 and RST7 files for MD simulations.
3. Run "parmed -i addc4_pvdw.in". This will add enhanced 12-6-4 Lennard-Jones interactions to the two metal ions, Zn2+ and Cd2+.
4. Run "sbatch gpu.pbs". This will submit the whole simulation job to the cluster for computation.
   
Note here NVIDIA Ampere A100 GPU is used with CUDA support. The whole job takes about 14 days to finish.
The SLURM file was initially split into two (minimizing + heating + equilibrium for one and production for two, each has a 7-day job time reserved) but combined here for convenience. Users can run individual steps interactively by extracting commands from the SLURM file "gpu.pbs". 
The output files for the equilibrium and production steps are too large to be uploaded, so only the output files for the minimization and heating steps are provided. Users are welcome to generate output files following the instructions mentioned above.
