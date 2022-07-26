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

$$\mathrm{DM}(z_i) = \mathrm{DM}_\mathrm{MW} + \mathrm{DM}_\mathrm{cosmo}(z_i | \lambda) + \mathrm{DM}_\mathrm{host}(z_i | \theta_i)/(1 + z_i)$$

where the MW contribution is a sum of the ISM and halo contributions, $\lambda$ are parameters that are common to every FRB in the Universe (like the background cosmology, including $\Omega_b$, fraction of cosmic baryons in diffuse ionized gas, mass fraction of Helium, scatter in electron column density along different lines of sight, etc.) and $\theta_i$ are parameters that are unique to the host galaxy. The host galaxy contribution is the dispersion in the rest frame of the host galaxy, hence the extra (1 + z) term. Technically some of the parameters in $\lambda$ also depend on the line of sight, if we have more information about the line of sight we can split the cosmo (equivalently, IGM) contribution into background cosmology + line of sight IGM. 

For some reasonable values for the ionized gas, the *average* cosmological contribution is approximately (Eq. 4 of Xu et al. 2021):
$$\mathrm{DM}_\mathrm{cosmo}(z_i) \approx  807\,\mathrm{pc}\,\mathrm{cm}^{-3} \int_0^{z_i} \frac{(1+z)dz}{(\Omega_m(1+z)^3 + \Omega_\Lambda)^{1/2}}$$

However the electron column density has some scatter due to large-scale structure. According to cosmological simulations, this scatter in terms of fractional standard deviation of $\mathrm{DM}_\mathrm{cosmo}$ is $Fz^{-1/2}$ for $z < 1$ (Macquart et al. 2020). $F$ measures the (inverse) strength of baryon feedback. 

Meanwhile, without specific information about the host galaxy, we can assume the host galaxy contribution is drawn from a log-normal distribution, giving us two additional population parameters: the mean and standard deviation of the underlying normal distribution. 

The MW terms can be assumed to be fixed. 

### Galaxy catalog prior

The galaxy catalog gives us a prior $p(z, \Omega, \theta)$ over the redshifts, sky positions, and (possibly) host galaxy properties $\theta$ that affect the host's DM contribution.

Assuming galaxy redshifts and sky positions are perfectly measured, this prior is:
$$p(z, \Omega, \theta) = \sum_\mathrm{gal} w_\mathrm{gal} \delta(z - z_\mathrm{gal})\delta(\Omega-\Omega_\mathrm{gal})p_\mathrm{gal}(\theta)$$
where $w$ are optional weights proportional to the probability that galaxy "gal" hosts an FRB. 

The term $p_\mathrm{gal}(\theta)$ should be thought of as a posterior on each galaxy's properties $\theta$ -- in other words, it includes a prior term (e.g. a lognormal distribution over DMs) so in the absence of specific information about a candidate host galaxy, it reduces to this prior, which should be the population distribution

### Likelihood given $N$ FRB events

$$p(\left{d_i \right}_N, \left{\mathrm{DM}_i \right}_N, \left{\Omega_i \right}_N, \left{z_i \right}_N, \left{\theta_i \right}_N | \lambda) = \Prod_{i = 1}^N \frac{p(d_i | \mathrm{DM}_i, \Omega_i) p(\mathrm{DM}_i | z_i, \lambda, \theta_i)p(\Omega_i, z_i, theta_i}{P_\mathrm{det}(\lambda)}$$

The numerator is 
$$p(d_i | \mathrm{DM}_i, \Omega_i) p(\mathrm{DM}_i | z_i, \lambda, \theta_i) \Sum_\mathrm{gal} $$

