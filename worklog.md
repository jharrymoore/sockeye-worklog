## Initial setup

- Working on sockeye headnode
- Installed miniconda via the standard linux installer, using default settings
- Installed mamba in the base env with
```
conda install mamba -c conda-forge
```
- Created new env from my existing env on the Cambridge machine. Since I'm working on the headnode I need to override the virtual cuda package
```
export CONDA_OVERRIDE_CUDA=11.8
mamba env create -f mace-openmm.yml

```

- Install mace and a MPI util package from GH
```
pip install git+https://github.com/choderalab/mpiplus.git
pip install git+https://github.com/ACEsuit/mace.git
pip install git+https://github.com/jharrymoore/openmm-ml.git@mace
pip install git+https://github.com/jharrymoore/openmmtools.git@development
```

- Tested with the following command, note I am using one of the MACE models distributed in the mace GH repo:
```
mace-md -f ala3_solv.xyz --ml_mol ala3_solv.xyz --model_path ~/mace/mace/calculators/foundations_models/
2023-12-03-mace-mp.model --output_dir md_test --nl nnpops --steps 1000 --minimiser 
ase
```



