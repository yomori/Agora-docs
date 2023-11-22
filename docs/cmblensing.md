# CMB lensing 

CMB lensing maps can be found in:

```globus: components/cmbkappa/```

There is one file in that directory:

```raytrace16384_ip20_cmbkappa.zs1.kg1g2_highzadded_lowLcorrected.fits```

This is a $N_{\rm side}=8192$ total CMB lensing map, which consists of the low-$z$ ($z<8.6$) raytraced component, high-redshift ($8.6<z<1100$) Gaussian component, and  additional corrections at low-$L$. 

There are three fields in the file ```k```,```g1```,```g2``` which correspond to:<BR>
$\kappa\hspace{0.2cm}=\frac{1}{2}(\partial_{1}\partial_{1}+\partial_{2}\partial_{2})\psi=\frac{1}{2}\nabla^{2}\psi$<BR>
$\gamma_{1}=\frac{1}{2}(\partial_{1}\partial_{1}-\partial_{2}\partial_{2})\psi$<BR>
$\gamma_{2}=\frac{1}{2}\partial_{1}\partial_{2}\psi$<BR>

and the maps can be read using:
```python
k, g1, g2 = hp.read_map(file_cmblensing,field=[0,1,2])
```
