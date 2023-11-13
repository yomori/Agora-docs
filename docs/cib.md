# CIB

CIB maps can be found in:

```globus: components/cib/```

There are three directories inside, and each corresponds to different units.

```nocc/``` contains CIB maps without colour correction (in Jy/Sr units)  <BR>
```withcc``` contains CIB maps with colour correction (in Jy/Sr units)    <BR>
```uK/``` contains CIB maps in uK units (colour correction + unit conversion) <BR>

In general ```nocc/``` are the one you want to use if you want to build a point source list
and ```uK``` are the ones you want to use if you are adding maps in uK units.

The reason why these are separate is because each individual source has its own SED, and the unit conversion can not be done exactly assuming a single number. In Agora, unit conversion is done separately per object.

-----

In each directory there are both:<BR>

 ```len/``` <BR>
 ```unl/``` <BR>

 directories, which correspond to lensed and unlensed maps.

-----

One directory lower are maps for a given experiement. CIB maps are generated for different experiments separately because band passes must be convolved.

```act/```   <BR>
```planck/``` <BR>
```spt3g/```  <BR>
```sptsz/```  <BR>

and in each directory there are files such as:

```agora_len_mag_cibmap_${expt}_${freq}ghz.fits```

These are stored as HEALPix T maps, which can be read in using:

```python
t = hp.read_map(file_cib)
```