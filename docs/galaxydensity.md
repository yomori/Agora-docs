# Galaxy lensing 

Galaxy density maps can be found in

```globus: components/galaxydensity/```

These are simply produced by multiplying the matter density field with some linear galaxy bias factor and integrated over redshift (assuming some n(z)). For now, we provide the maps for LSST-Y1 (although its trivial to produce other galaxy surveys):

```/lsst_y1```

and in it, you will find:

```/maps```
```/nz```

---------------------------------------
# n(z)

The n(z) used to create galaxy density maps are stored in ```/nz``` directory. These have file names like:

```nz_{expt}_{year}_{galaxytype}_{nbins}bins.txt```

where:<BR>

```expt``` is the experiment (```lsst``` only for now)<BR>
```year``` is the specific data analysis year (```y1``` for LSST)<BR>
```galaxytype``` is ```lens``` (lens galaxies) in this case <BR>
```nbins``` is the number of tomographic bins. <BR>

The columns are organized as z, bin1, bin2 ... etc.<BR>
(Note: the z spacing depends on where the n(z) came from, and is therefore file dependent).

The n(z) for LSST were taken from the [DESC Science Requirement Document (SRD)](https://arxiv.org/abs/1809.01669)
