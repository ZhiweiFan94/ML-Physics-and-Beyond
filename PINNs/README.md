# Lugiato-Lefever Equation

The Lugiato-Lefever equation is a partial differential equation used in nonlinear optics to describe the field inside an optical cavity. It is given by:

$$
i\frac{\partial \psi(t, \theta)}{\partial t} = \delta_0 \psi(t, \theta) -  \frac{D_2}{2}\partial^2_\theta \psi(t, \theta) - \gamma|\psi(t, \theta)|^2 \psi(t,\theta)  + i\frac{\kappa}{2}\left(\psi(t, \theta)-H \right)
$$

where:

- $\psi(t, \theta)$ is the complex field envelope,
- $t$ is the slow time variable,
- $\theta$ is the spatial variable,
- $D_2$ is the group velocity dispersion coefficient (higher dispersions are omitted),
- $\kappa$ is the cavity loss rate,
- $\delta_0 = \omega_0 - \omega_p$ is the cavity detuning between laser and pump,
- $H$ is the driving field amplitude.

This equation is a variant of the nonlinear Schrödinger equation (NLSE) with additional terms to account for cavity effects and external driving. The term $i \frac{\partial^2}{\partial \tau^2} E(t, \tau)$ represents the group velocity dispersion, while $i |E(t, \tau)|^2 E(t, \tau)$ accounts for the Kerr nonlinearity.
