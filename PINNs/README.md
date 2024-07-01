# Physical Informed Neural Network for a driven-damped NLSE
## Background
In the realm of nonlinear optics, the study of light-matter interactions in optical cavities has garnered significant interest due to its applications in various fields such as telecommunications, spectroscopy, and quantum computing. One of the fundamental equations describing the dynamics of the optical field in such systems is the Nonlinear Schrödinger Equation (NLSE). The Lugiato-Lefever Equation (LLE), a specific form of the driven-damped NLSE, models the behavior of light in a Kerr medium within an optical cavity, considering both dispersion and nonlinearity.

The LLE is pivotal for understanding phenomena like optical frequency comb generation, temporal cavity solitons, and pattern formation in nonlinear optical resonators. These phenomena have profound implications for the development of precise optical clocks, high-capacity data transmission systems, and advanced laser sources. The driven-damped nature of the LLE introduces additional complexity by accounting for the continuous injection of energy into the system and its subsequent dissipation, making it a rich subject for both theoretical and experimental investigations.

Traditional methods of solving the LLE involve numerical techniques which can be computationally intensive and sensitive to initial conditions. Recently, the advent of machine learning and, more specifically, Physics-Informed Neural Networks (PINNs) has provided a new paradigm for solving such differential equations. PINNs leverage the power of neural networks while embedding the physical laws governing the system into the learning process, thereby offering an efficient and potentially more accurate means of modeling complex dynamical systems like those described by the LLE.


## Modeling: A driven-damped NLSE -- Lugiato-Lefever Equation

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

This equation is a variant of the nonlinear Schrödinger equation (NLSE) with additional terms to account for cavity effects and external driving. The forms of dispersion and nonlinearity should be revised per materials and other factors, and here we assume the higher-order dispersion is weak in a Kerr medium.
