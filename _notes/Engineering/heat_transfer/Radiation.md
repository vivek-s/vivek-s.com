The amount of radiation from a source surface $i$ to target surface $j$ is given by the Stefan Boltzmann's law
$$Q_{ij} = A_i\epsilon_iF_{ij}\sigma(T^4_i-T^4_j)$$
where,
$A_i$ is the area of the surface
$\epsilon$ is the [[Emissivity]] of the surface,
$F_{ij}$ is [[view_factor]]
$\sigma$ is Stephan Boltzman constant $5.67 * 10^-8$
$T$ is temperature in (absolute units aka Kelvin or Rankine)

Note that, the area, emissivity and view factor need to be consistent with respect to source or target in the equation.

$$A_i\epsilon_iF_{ij} =  A_j\epsilon_jF_{ji}$$

Temperature difference of 20°C at 520-500C range is significantly more than 50-30C range. So delta T alone isn't enough you have to lok at absoute

$$\tau + \alpha + \rho = 1$$
$\tau$ - transmissivity
$\alpha$ - absorbtivity
$\rho$ - reflectivity

| $\tau$ | $\alpha$ | $\rho$ | Type        |
| ------ | -------- | ------ | ----------- |
| 0      | >0       | >0     | Opaque      |
| 1      | 0        | 0      | Transparent |
| 0      | 1        | 0      | Black Body  |
| 0      | 0        | 1      | White Body  |
| >0     | >0       | >0     | Grey Body            |


## 1. Net outgoing Radiation
$$ Net\ outgoing\ radiation = \epsilon \sigma T^4 + (1-\epsilon)q_i - q_i$$
First term = emitted radiation
Second term = reflected radiation
Third term = incident radiation
