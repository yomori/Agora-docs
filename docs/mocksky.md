# Mock sky

Mock skies are realizations where all the components are all added. 

```act/``` $\hspace{0.55cm}$   : Atacama Cosmology telescope (ACT) <BR>
```cmbs4d/``` : CMB-S4 deep <BR>
```cmbs4w/``` : CMB-S4 wide <BR>
```planck/``` : Planck <BR>
```sobl```$\hspace{0.7cm}$ : Simons Observatory (baseline) <BR>
```sptsz/``` $\hspace{0.1cm}$ : South Pole Telescope (SPT) SZ survey <BR>
```spt3g/``` $\hspace{0.1cm}$ : South Pole Telescope (SPT) 3G survey <BR>

Maps for each experiment are constructed separately because we assume different frequency channels and also the transmission function. These are obtained from the following locations:<BR>
ACT$\hspace{0.98cm}$   : private communication<BR>
CMBS4d $\hspace{0.1cm}$: private communication<BR>
CMBS4w $\hspace{0.05cm}$: private communication<BR>
Planck$\hspace{0.45cm}$ : [https://irsa.ipac.caltech.edu/data/Planck/release_3/ancillary-data/HFI_RIMO_R3.00.fits](https://irsa.ipac.caltech.edu/data/Planck/release_3/ancillary-data/HFI_RIMO_R3.00.fits)<BR>
Sobl $\hspace{0.7cm}$  :<BR>
SPT-3G$\hspace{0.3cm}$  : private communication<BR>

-------------------------------------------

In each directory there are files with names:

```agora_${expt}_${freq}ghz_${comoponent}_uk.fits```

where the components can be:

```lcmbNG```: lensed CMB (with non-Gaussian lensing field)  <BR>
```lcibNG```: lensed CIB <BR>
```lradNG```: lensed radio <BR>
```ltszNGbahamas80```: lensed tSZ maps (assuming BAHAMAS $T_{\rm AGN}=10^{8}K$ gas model) <BR>
```lkszNGbahamas80```: lensed kSZ maps (assuming BAHAMAS $T_{\rm AGN}=10^{8}K$ gas model) <BR>
```lcibNG_ltszNGbahamas80_lkszNGbahamas80_lradNG```: Sum of the components above except CMB (i.e., foreground only). <BR>
```lcmbNG_lcibNG_ltszNGbahamas80_lkszNGbahamas80_lradNG```: Sum of all the components above. <BR>

