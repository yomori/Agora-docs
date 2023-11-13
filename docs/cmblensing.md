# CMB lenisng 

CMB lensing maps can be found in:

```globus: components/cmbkappa/```


There is one file in that directory:

```raytrace16384_ip20_cmbkappa.zs1.kg1g2_highzadded_lowLcorrected.fits```

```python
k, g1, g2 = hp.read_map(file_cmblensing,field=[0,1,2])
```
