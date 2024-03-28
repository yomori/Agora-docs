# kSZ

kSZ maps can be found in:

```globus: components/ksz/```


There are three directories insde:

```len/``` contains lensed kSZ <BR>
```unl/``` contains unlensed kSZ <BR>

The file naming convention are:

```agora_{flag}_{bahamsmodel}_bnd_unb_1.0e+12_1.0e+18.fits``` <BR>

flag &nbsp;&nbsp;    : ```ltszNG```/```utszNG``` stands for "lensed"/"unlensed" kSZ "non-Gaussian" <BR>
model: ```bahamas78```/```bahamas80```  stands for the BAHAMAS halo model with $T_{\rm AGN}=10^{7.8}$ K

The other labels imply that it includes both the bound and unbound components and mass range $10^{12}<M<10^{18} M_{\odot}/h$


These are stored as HEALPix T maps, which can be read in using:

```python
ksz = hp.read_map(file_ksz)
```

Note: the Q/U extensions have been filled with random non-zero numbers so that we have a T/Q/U set which is needed for PolSpice.

Additionally, $\tau$ maps generated using the exact same code without multiplying the $v_{\rm LOS}$ can be found in:

```globus: components/ksz/unl```

