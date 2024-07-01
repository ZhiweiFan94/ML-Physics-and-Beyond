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

### Comprehensive Understanding of the LLE

The Lugiato-Lefever Equation can seem complex at first glance, so let's break it down with a few examples and intuitive explanations.

1. **Optical Frequency Combs:**
   Optical frequency combs are spectra consisting of a series of discrete, equally spaced elements. They are crucial for high-precision measurements and have applications in spectroscopy, telecommunications, and the development of optical clocks. The LLE helps in understanding how these combs can be generated within an optical cavity. When a continuous wave laser is coupled into a nonlinear optical resonator, the interaction between the dispersion and the Kerr nonlinearity (intensity-dependent refractive index) described by the LLE can lead to the formation of a stable frequency comb.

2. **Temporal Cavity Solitons:**
   Temporal cavity solitons are stable pulses of light that can circulate indefinitely within an optical cavity. These solitons are solutions to the LLE and are formed due to a balance between dispersion, nonlinearity, and the driven-damped nature of the system. Imagine a single pulse of light that maintains its shape and energy as it circulates inside the cavity, thanks to the precise balance of the LLE terms. These solitons can be used in optical communication systems to transmit information over long distances without distortion.

3. **Pattern Formation:**
   The LLE also explains how certain patterns of light can form in an optical cavity. These patterns result from the interplay between the nonlinearity and dispersion in the medium. For example, under certain conditions, the light field within the cavity can spontaneously break symmetry and form periodic patterns or localized structures. This phenomenon is similar to how ripples form on the surface of a pond when disturbed.

### Practical Example

Let's consider a simple analogy to understand the LLE. Imagine you're pushing a swing (the light field) in a playground. The swing has a natural frequency (resonance), and you push it at this frequency (driving force). If you push too hard (high driving amplitude), the swing will move erratically, but if you push just right, it will swing back and forth smoothly. Now, if the swing's chain is stretchy (nonlinearity), the swing's frequency will change depending on how high it goes. Additionally, if there's a little friction (loss), you need to keep pushing to maintain the swing's motion.


## Mature numerical methods

When it comes to simulating the Lugiato-Lefever Equation, several mature numerical methods are commonly employed to achieve accurate and efficient solutions. Two of the most widely used methods are the Runge-Kutta method and the Split-Step Fourier method.

### Runge-Kutta Method

The Runge-Kutta method is a family of iterative methods for approximating the solutions to ordinary differential equations (ODEs). The fourth-order Runge-Kutta method (RK4) is particularly popular due to its balance between accuracy and computational efficiency. For the Lugiato-Lefever Equation, which involves partial differential equations (PDEs), the method can be adapted to handle the temporal evolution of the system. Here’s a basic outline of how the RK4 method works:

1. **Initial Conditions:** Start with an initial field $\psi(t=0, \theta)$.
2. **Iterative Steps:** For each time step $t \rightarrow t + \Delta t$:
   - Compute intermediate values (slopes) at different points within the time step.
   - Combine these slopes to obtain a weighted average that estimates the field at the next time step.
3. **Update Field:** Update the field $\psi(t, \theta)$ using the weighted average of slopes.

This method is advantageous for its simplicity and accuracy but can become computationally expensive for large-scale simulations due to the need for small time steps to maintain stability.

### Split-Step Fourier Method

The Split-Step Fourier method is a specialized technique for solving nonlinear PDEs, particularly useful for equations like the NLSE and LLE that involve both linear and nonlinear terms. The method separates (splits) the linear and nonlinear parts of the equation and solves them in a stepwise manner using Fourier transforms. Here’s an outline of the process:

1. **Initial Conditions:** Start with an initial field $\psi(t=0, \theta)$.
2. **Linear Step:** Apply the linear part of the LLE in the Fourier domain. This involves:
   - Transforming the field to the Fourier domain using the Fast Fourier Transform (FFT).
   - Evolving the field according to the linear dispersion relation.
   - Transforming back to the time/spatial domain using the inverse FFT.
3. **Nonlinear Step:** Apply the nonlinear part of the LLE in the time/spatial domain. This involves:
   - Updating the field according to the nonlinear interaction term.
4. **Iterate:** Repeat the linear and nonlinear steps for each time step $t \rightarrow t + \Delta t$.

The Split-Step Fourier method is highly efficient for handling the dispersion and nonlinearity separately, allowing for larger time steps compared to the Runge-Kutta method. It is particularly well-suited for problems where the dispersion relationship can be easily handled in the Fourier domain.

By employing these mature numerical methods, researchers can effectively simulate the dynamics described by the Lugiato-Lefever Equation, gaining insights into the complex behaviors of optical fields in nonlinear cavities.



