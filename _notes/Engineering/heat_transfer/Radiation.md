---
title: Radiation
---
## 1. Black Body Radiation 
Black body is a perfect absorber and emitter of radiation. The Stefan Boltzmann's law says that energy radiation from a black body is a function of its absolute temperature given by the following equation

$$\dot q = \sigma T^4$$
where,
$\sigma$ is Stephan Boltzman constant $5.67 * 10^{-8} W/m^2\cdot K^4$ or $1.7134*10^{-9}BTU/hr\cdot ft^2\cdot °R^4$
$T$ is temperature in (absolute units aka Kelvin or Rankine)

Every medium continuously emits radiation in all directions at the rate determined by its absolute temperature. This is known as *Prevost's law*

## 2. Grey Body Radiation
Most bodies have imperfect absorption and emission of radiation. We use a proportionality constant $\epsilon$ or emissivity to account for this imperfection. 

Radiant energy is absorbed ($\alpha$), reflected ($\rho$) or transmitted ($\tau$). 
$\tau$ - transmissivity or transmittance
$\alpha$ - absorptivity or [[absorptance]]
$\rho$ - reflectivity or reflectance

$$\tau + \alpha + \rho = 1$$

Bodies are classified according to how they transmit and absorb radiation. 

| $\tau$ | $\alpha$ | $\rho$ | Type        |
| ------ | -------- | ------ | ----------- |
| 0      | >0       | >0     | Opaque      |
| 1      | 0        | 0      | Transparent |
| 0      | 1        | 0      | Black Body  |
| 0      | 0        | 1      | White Body  |
| >0     | >0       | >0     | Grey Body            |

## 3. Kirchhoff's law
Kirchoff's law is named after German physicist Gustav Kirchhoff. It states that *in steady state* the a body emits precisely as much radiant energy as it absorbs. It is inferred from this reasoning that a black body is a perfect absorber and emitter of radiation at every wavelength and every frequency.

For grey bodies, it is always true that *for a given wavelength*, absorptivity is equal to emissivity. But we might make this generalizing assumption over a band of wavelength (IR/solar etc.). See more discussion in [[absorptance]]

## 4. Reflection
Based on the direction of reflection a body might be classified as
- **Diffuse** - Energy striking a surface is scattered in all directions. Think of a white sheet of paper
- **Specular**- energy is reflected at an angle equal to an angle of incidence. Think of a mirror
- **Mixed** - Most real surfaces are a combination of above two. It ischaracterized by "specular fraction" - i.e. fraction of total reflected radiation that is specular

## 5. Wavelength
Generally for space applications we are interested in radiation in a range 100nm to 4000nm (i.e in the Infrared range)

## 6. Radiant flux between two grey bodies
In real world problems, you are commonly dealing with radiative heat transfer between two surfaces. The radiation heat flux from a grey body source surface $i$ to  grey body target surface $j$ is given by following equaiton.

$$\dot q_{ij} = A_i\epsilon_iF_{ij}\sigma(T^4_i-T^4_j)$$
where,
$A_i$ is the area of the surface
$\epsilon$ is the [[Emittance]] of the surface,
$F_{ij}$ is [[view_factor|View Factor]]

Note that, the area, emissivity and view factor need to be consistent with respect to source or target in the equation.

$$A_i\epsilon_iF_{ij} =  A_j\epsilon_jF_{ji}$$

See also [[Radk]] for more complex radiation cacluations involving more than two surfaces

## 7. Net outgoing Radiation
$$ Net\ outgoing\ radiation = \epsilon \sigma T^4 + (1-\epsilon)q_i - q_i$$
First term = emitted radiation
Second term = reflected radiation
Third term = incident radiation

[[radiation_conductance| Radiation Conductance]]
[[radiation_historical_perspective|Radiation - Historical Perspective]]