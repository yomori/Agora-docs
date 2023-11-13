# radio

radio maps can be found in:

```globus: components/rad/```


There are three directories insde:

```len/``` contains lensed radio <BR>
```unl/``` contains unlensed radio <BR>

-------------------------------------
## Catalog:

```agora_radiocat_len_universemachine_trinity_95_150_220ghz_randflux_datta2018_truncgauss.0.fits```<BR>


-------------------------------------
## Frequency maps

```agora_radiomap_len_universemachine_trinity_95ghz_randflux_datta2018_truncgauss.0.fits```<BR>
```agora_radiomap_len_universemachine_trinity_220ghz_randflux_datta2018_truncgauss.0.fits```<BR>
```agora_radiomap_len_universemachine_trinity_220ghz_randflux_datta2018_truncgauss.0.fits```<BR>

These are stored as HEALPix TQU maps, which can be read in using:

```python
t, q, u = hp.read_map(file_radio,field=[0,1,2])
```

-------------------------------------
## $dN/dS$

```agora_radiocat_len_universemachine_trinity_95_150_220ghz_randflux_datta2018_truncgauss_dnds.0.dat``` <BR>

