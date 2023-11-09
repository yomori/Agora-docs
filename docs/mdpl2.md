# Raw MDPL2 products

The underlying N-body simulation used for Agora is the Multi-Dark Planck 2 simulation.
Some products can be downloaded from the [CosmoSim](https://www.cosmosim.org/metadata/mdpl2/) website, in addition to useful products such as semi-analytic models.

---------------------------------------

## Halo catalogs/merger trees
The Rockstar halo catalogs and merger trees can be found on Peter Behroozi's website:
[https://halos.as.arizona.edu/simulations/MDPL2/hlists/](https://halos.as.arizona.edu/simulations/MDPL2/hlists/)
[https://halos.as.arizona.edu/simulations/MDPL2/hlists/](https://halos.as.arizona.edu/simulations/MDPL2/hlists/)

These are ascii files that can be loaded using:
```python
halos = np.loadtxt(...)
```

---------------------------------------

## UniverseMachine catalogs
UniverseMachine catalogs can also be found on Peter Behroozi's website:

[https://halos.as.arizona.edu/UniverseMachine/DR1/MDPL2_SFR/](https://halos.as.arizona.edu/UniverseMachine/DR1/MDPL2_SFR/)


These are binary files that can be read using Peter's snippet:
```python
#!/usr/bin/python
import numpy as np

dtype = np.dtype(dtype=[('id', 'i8'),('descid','i8'),('upid','i8'),
                        ('flags', 'i4'), ('uparent_dist', 'f4'),
                        ('pos', 'f4', (6)), ('vmp', 'f4'), ('lvmp', 'f4'),
                        ('mp', 'f4'), ('m', 'f4'), ('v', 'f4'), ('r', 'f4'),
                        ('rank1', 'f4'), ('rank2', 'f4'), ('ra', 'f4'),
                        ('rarank', 'f4'), ('A_UV', 'f4'), ('sm', 'f4'), 
                        ('icl', 'f4'), ('sfr', 'f4'), ('obs_sm', 'f4'), 
                        ('obs_sfr', 'f4'), ('obs_uv', 'f4'), ('empty', 'f4')],
                 align=True)

halos = np.fromfile('/path/to/sfr_catalog.bin', dtype=dtype)
```

---------------------------------------

## Particles
The raw simulation particles are stored on NERSC tape.
The snapshots are 1.7TB each and there are 130 snapshots, which makes them very diffcult to transfer. 
If you need these, please contact me directly.

