# Raytracing outputs




Ray tracing was done using the [GrayTrix](https://sci.nao.ac.jp/MEMBER/hamana/GRayTrix/index.html) package. For most applications it is strongly suggested to use the pre-processed lensing maps instead (so you don't need to touch fortran code!), but they can nonetheless be found in:

 ```globus: raytrace/```

The files are combined in bundles:
```bash
tar -zvf raytrace16384_ip20.zsX_Y.mag.tar
```
```X``` is the starting slice number and ```Y``` is the last slice number contained in the bundle. The bundle ranges from 1-25 to 226-253.


The output files are stored in binary format which are most easily read using a fortan routine (found [here](https://github.com/yomori/graytrix/blob/master/degrade_nsideout.f90)), which can be compiled by doing:
```bash
gfortran degrade_nsideout.f90 -o degrade_nsideout.x -I${DIR_HEALPIX}/include -DGFORTRAN -fno-second-underscore -fopenmp -fPIC -L${DIR_HEALPIX}/lib -lhealpix -lcfitsio
```
where ```DIR_HEALPIX``` is the directory of where HEALPix is installed. Once compiled, it can be executed using:
```bash
./degrade_nsideout.x -infile ${infile}
```

where $infile is the input file.
This will degrade the maps from $N_{\rm side}$=16384 to a more managable $N_{\rm side}$=8192, and save it as a .fits file which can be read using ```healpy```:

```python
k,g1,g2 = hp.read_map(infile+'.kg1g2',field=[0,1,2])
```

where k is convergence and g1/g2 are the shear components. By default, the curl modes are not returned, but the maps are, in princle stored in the binary file as well (see [snippet](https://github.com/yomori/graytrix/blob/065ce951e1624e8d843209aeadc744b3805fa8bd/degrade_nsideout.f90#L94)).
