# statistical-frb
Inferring the DM-z relation statistically by associating poorly-localized FRBs with galaxy catalogs

Some relevant papers/links:

* [McQuinn 2013](https://arxiv.org/abs/1309.4451)
* [Macquart et al. 2020](https://arxiv.org/abs/2005.13161)
* [Xu et al. 2021](https://iopscience.iop.org/article/10.3847/2041-8213/ac399c/pdf)
* [CHIME catalog](https://www.chime-frb.ca/catalog)

### FRB observables

The relevant FRB observables are the DM and the sky location $\Omega$. 

So the single-event likelihood for each FRB $i$ is
$$p(d_i^\mathrm{FRB} | \mathrm{DM}_i, \Omega_i)$$

Looking at the CHIME catalog, it seems "poorly localized" is a (1-sigma) error of 0.2-0.3 degrees in RA and Dec each. 
The fractional uncertainty on DM is always less than 1/1000, it's essentially perfectly measured. 

### DM-z relation 

Following Macquart et al. (2020), 

$$\mathrm{DM}(z_i) = \mathrm{DM}_\mathrm{MW} + \mathrm{DM}_\mathrm{cosmo}(z_i | \Lambda) + \mathrm{DM}_\mathrm{host}(z_i | \theta_i)$$

where the MW contribution is a sum of the ISM and halo contributions, $\Lambda$ are parameters that are common to every FRB in the Universe (like the background cosmology, including $\Omega_b$, fraction of cosmic baryons in diffuse ionized gas, mass fraction of Helium, etc.) and $\theta_i$ are parameters that are unique to the host galaxy.

For some reasonable values for the ionized gas, the *average* cosmological contribution is approximately (Eq. 4 of Xu et al. 2021):
$$\mathrm{DM}_\mathrm{cosmo}(z_i) \approx  807\,\mathrm{pc}\,\mathrm{cm}^{-3} \int_0^{z_i} \frac{(1+z)dz}{(\Omega_m(1+z)^3 + \Omega_\Lambda)^{1/2}}$$

However the electron column density has some scatter due to large-scale structure. According to cosmological simulations, this scatter in terms of fractional standard deviation of $\mathrm{DM}_\mathrm{cosmo}$ is $Fz^{-1/2}$ for $z < 1$ (Macquart et al. 2020). $F$ measures the (inverse) strength of baryon feedback. 
