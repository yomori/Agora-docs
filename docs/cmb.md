# CMB

CMB maps can be found in:

```globus: components/cmb/```


There are three directories insde:

```unl/``` contains unlensed primary CMB <BR>
```phi/``` contains lensing potential realizations  <BR>
```len/``` contains lensed primary CMB  <BR>

---------------------------------------
## unl

Unlensed CMB realizations are produced from CAMB spectra using the file:

```globus: misc/camb/mdpl2_lenspotentialCls.dat ```

There are two sets, which are independent realizations of the primary CMB:

```teb1/agora_phiG_teb1_seed*.alm```<BR>
```teb2/agora_phiG_teb2_seed*.alm```

These files are stored as HEALPix alm files and can be read in using:
```python
tlm, elm, blm = hp.read_alm(file_unl_alm,hdu=[1,2,3])
```

---------------------------------------
## phi 
We provide two types of lensing potentials Gaussian and non-Gaussian.
Gaussian realizations are those generated from $C_{\ell}^{\phi\phi}$, and have names like:

```phi/agora_phiG_phi1_seed*.alm```

where $*$ ranges from 1-50.

Non-Gaussian realization refers to lensing potential from raytracing through the simulation, with names:

```phi/agora_phiNG_phi1_seed1.alm```

(note the label NG, which stands for non-Gaussian). Since we only have one full N-body simulation realization, we only have seed 1.
Similar to unlensed CMB files, these lensing potentials are stored as HEALPix alm, and can be read using:  


```python
plm = hp.read_alm(file_phi_alm)
```


---------------------------------------
## len
Two sets of lensed CMB which correspond to the two sets of unlensed CMB are provided.
These are stored in:<BR>

```tqu1/agora_tqu1_phiG_seed1_lmax16000_nside8192_interp1.6_method1_pol_1_lensedmap.fits``` <BR>
```tqu2/agora_tqu2_phiG_seed1_lmax16000_nside8192_interp1.6_method1_pol_1_lensedmap.fits``` <BR>

The two sets of lensed CMB are lensed by the same lensing potention $\phi$, and each seed uses a <ins>different</ins> $\phi$ realization.

Additionally, two sets of lensed CMB, lensed with the non-Gaussian lensing potential can be found in:<BR>

```tqu1/agora_tqu1_phiNG_seed1_lmax16000_nside8192_interp1.6_method1_pol_1_lensedmap.fits``` <BR>
```tqu2/agora_tqu2_phiNG_seed1_lmax16000_nside8192_interp1.6_method1_pol_1_lensedmap.fits``` <BR>

We provide realizations with different background CMB but the <ins>same</ins> lensing potential (since we only have one). 

These are stored as HEALPix TQU maps, which can be read in using:

```python
t, q, u = hp.read_map(file_phi_alm,field=[0,1,2])
```