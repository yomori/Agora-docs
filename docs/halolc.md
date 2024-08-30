# Halo lightcone

The raw ascii halo catalog files are halos in a cube box.
We tile the simulation box and produce a halo lightcone from it.
These are stored in:

 ```globus: halocat/```


These files are stored as numpy .npz files and can be loaded using 

```python
halocat = np.load('agora_halolc_rot_X_v050223.npz')
```
where X is the slice number. Slice number ranges from 4-200 and each integer increases by 25 ${\rm Mpc}/h$.
In other words:<BR>
X=0 -> 0-24 $ {\rm Mpc}/h$ <BR>
X=1 -> 25-49 $ {\rm Mpc}/h$ <BR>
X=2 -> 50-75 $ {\rm Mpc}/h$ <BR>
...<BR>
<BR>

The columns included in the catalog are: <BR>
```
ra     : Right Ascension [deg] 
dec    : Declination [deg]  
z      : Redshift [unitless]      
m200c  : x200 critial density [Msun/h]
m500c  : x500 critial density [Msun/h]
mvir   : Virial mass [Msun/h] 
rvir   : Virial radius [Mpc/h] 
vlos   : LOS velocity [km/s]  
vtht   : velocity in theta [km/s]  
vphi   : velocity in phi [km/s]  
rs     : Comoving scale radius [kpc/h]   
m200b  : Mass enclosed within overdensity 200$\rho_{\rm b}$ [Msun/h]
mpeak  : Peak mass over accretion history [Msun/h]
vpeak  : Peak Vmax over accretion history [km/s]
haloid : Halo ID [unitles]   
pid    : RockstarId of least massive host halo [unitles]
upid   : RockstarId of most massive host halo [unitles]
```
But in principle, one can include any of the columns included in the original Rockstar halo catalog.

A specific column can then be loaded using: 

```python
ra = halocat['ra']
```
