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

---------------------------------------

## Building your own ligtcones

Below is an example code snippet if you would like to build you own lightcone from scratch using the raw Rockstar halo catalogs.

```python
import os, sys
import numpy as np
import healpy as hp
import numexpr as ne 

def rd2tp(ra,dec):
    """Convert ra,dec -> tht,phi"""
    tht = (-dec+90.0)/180.0*np.pi
    phi = ra/180.0*np.pi
    return tht,phi

def tp2rd(tht,phi):
    """Convert tht,phi -> ra,dec"""
    ra  = phi/np.pi*180.0
    dec = -1*(tht/np.pi*180.0-90.0)
    return ra,dec


shellnum   = int(sys.argv[1])

shellwidth = 25       # Mpc/h 
origin     = [0,0,0]
boxL       = 1000     # Mpc/h

# download from https://halos.as.arizona.edu/simulations/MDPL2/hlists/
px,py,pz,...   = np.loadtxt('')

chilow = shellwidth*(shellnum+0)
chiupp = shellwidth*(shellnum+1)

for xx in range(-ntiles,ntiles):
    for yy in range(-ntiles,ntiles):
        for zz in range(-ntiles,ntiles):

            sx  = ne.evaluate("px -%d + boxL * xx"%origin[0])
            sy  = ne.evaluate("py -%d + boxL * yy"%origin[1])
            sz  = ne.evaluate("pz -%d + boxL * zz"%origin[2])
            r   = ne.evaluate("sqrt(sx*sx + sy*sy + sz*sz)")
            idx = np.where((r>chilow) & (r<chiupp))[0]              # only select halos that are within the shell

            if idx.size!=0:
                ux   = sx[idx]/r[idx]
                uy   = sy[idx]/r[idx]
                uz   = sz[idx]/r[idx]
                
                tht,phi = hp.vec2ang(np.c_[ux,uy,uz])
                ra,dec  = tp2rd(tht,phi)
                totra   = np.append(totra,ra)
                totdec  = np.append(totdec,dec)	

#Download from https://app.globus.org/file-manager?origin_id=3ff10f78-83d9-11ed-9b8c-19370d280681&origin_path=%2Fmisc%2Frotmat%2F
rotmat=np.eye(3)
if ((shellnum*shellwidth>=1000) & (shellnum*shellwidth<2000)): rotmat=np.loadtxt('rotmat_1000_2000mpc.txt')
if ((shellnum*shellwidth>=2000) & (shellnum*shellwidth<3000)): rotmat=np.loadtxt('rotmat_2000_3000mpc.txt')
if ((shellnum*shellwidth>=3000) & (shellnum*shellwidth<4000)): rotmat=np.loadtxt('rotmat_3000_4000mpc.txt')
if ((shellnum*shellwidth>=4000) & (shellnum*shellwidth<5000)): rotmat=np.loadtxt('rotmat_4000_5000mpc.txt')
if ((shellnum*shellwidth>=5000) & (shellnum*shellwidth<6000)): rotmat=np.loadtxt('rotmat_5000_6000mpc.txt')
if ((shellnum*shellwidth>=6000) & (shellnum*shellwidth<7000)): rotmat=np.loadtxt('rotmat_6000_7000mpc.txt')

tht,phi      = rd2tp(totra,totdec)
thtr,phir    = hp.rotator.rotateDirection(rotmat, tht, phi, do_rot=True)
totra_r,totdec_r = tp2rd(thtr,phir)
```
