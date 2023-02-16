---
title: Fluid Properties
---

The following are fluid properties commonly encountered while working in Fluid Mechanics. Also included is a simple snippet that shows how to get properties of water using [[CoolProp]] and [[REFPROP]]

## Density
Density $\rho$ is the mass per unit volume of the fluid.

### Unit Conversion

$$1 kg/m^3 = 0.001 g/cm^3= 1/16.018 lbm/ft^3 = 1/(16.018*1728) lbm/in^3 $$

### CoolProp
SI Units
```python
Cp.PropsSI("D", "P", 101325, "T", 300, "Water")
# Density of water at 101325 Pa and 300 K is 996.556935...kg/m^3
```

### REFPROP
English Units
```Excel
=Density("Water","TP","E",80.33, 14.6959)
"62.21301706 lbm/ft^3"
```


## Specific Weight
*do not confuse with [[Fluid Properties#Specific Gravity|Specific Gravity]]*

Specific weight is the weight (force exerted under gravity) per unit volume of the fluid. Units are $N/m^3$ or $lbf/ft^3$. It is denoted by $\gamma$

$$\gamma = \rho g$$

Where $g$ is the gravitational constant at the location (typically 9.81 $m/s^2$ or 32.174 $ft/s^2$)

## Specific volume

Specific volume is inverse of density

$$v=\frac{1}{\rho}$$

## Specific Gravity
Specific gravity is the ratio of density of a substance to density of water. It is denoted by $SG$

$$SG= \frac{\rho_{liquid}}{\rho_{water}}$$

### API Gravity
API gravity is used in the oil industry to measure specific gravity. It is a measure of how heavy or light a petroleum liquid is compared to water. If API >10, it floats on water and if API<10 it sinks. It is usually calulated at standard conditions of 60°F

$$API\ gravity = \frac{141.5}{SG}-131.5$$

## Specific Heat
Specific heat is the amount of heat that must be applied to a substance to increase the temperature of a unit mass by one degree. Typical units are $J/kg.°C$ or $BTU/lbm.°F$

### Gases
Gases have two types of specific heat depending on how the heat is added 
- constant volume $c_v$
- constant pressure $c_p$

Since $c_p$ is based on a constant pressure process

$$c_p = \frac{\partial h}{\partial T}$$

where, $h$ is the enthalpy of the fluid.
and since $c_v$ is based on a constant volume process

$$c_v=\frac{\partial u}{\partial T}$$

where, $u$ is the enthalpy of the fluid.

#### Gas Constant
Difference getween cp and cv gives the [[#Gas Constant|gas constant]] R

$$c_p-c_v=R$$

#### Specific heat Ratio
Ratio of specific heat is denoted by a greek symbol $\gamma$ 

$$\gamma = \frac{c_p}{c_v}$$

### CoolProp
SI Units
```python
# c_p using c_p
Cp.PropsSI('C','P',101325,'T',300,'Air') # you can use C, CPMASS, or Cpmass
# c_p using derivative
Cp.PropsSI('d(Hmass)/d(T)|P','P',101325,'T',300,'Air')
# 1006.3739...J/kg-K

# c_v using c_v
Cp.PropsSI('CVMASS','P',101325,'T',300,'Air') # you can use CVMASS, or Cvmass
#  717.9715...J/kg-K
```

### REFPROP
English Units
```Excel
=Cp("Air","TP","E",80.33, 14.6959)
=Cv("Air","TP","E",80.33, 14.6959)
```


## Viscosity
### Absolute (Dynamic) Viscosity
Absolute viscosity $\mu$ is the proportionality factor relating fluid shear stress and rate of  deformation

$$\tau = \mu \frac{\partial u}{\partial y}$$

where, 
- $\tau$ is shear stress
- $\frac{\partial u}{\partial y}$ is rate of change of deformation. i.e.delta change in velocty per delta change in distance normal to the wall

Units of absolute viscosity are $kg/m.s$ or $N.s/m^2$  or  $Pa.s$ or $lbm/ft.s$ or $lbf/ft^2.s$

#### Conversion
- $lbf/ft^2.s$ is also called $Reyn$
- $0.1 kg/m.s$ is  $1Poise$
- Viscosity of water is ~ $0.01 Poise$ or $0.001 kg/m.s$ or $6.7304\times10^{-4}\ lbm/ft.s$

#### CoolProp
SI Units
```python
Cp.PropsSI('V','P',101325,'T',300,'Water')
```

#### REFPROP
English Units
```Excel
=Viscosity("Water","TP","E",80.33, 14.6959)
"result- 6.73042E-04 lbm/ft-s"
```
Note: Using SI units in REFPROP gives viscosity in $\micro Pa-s$

### Kinematic Viscosity
Kinematic viscosity is dynamic viscosity divided by density. Measurement of kinematic viscosity is more accurate than measuring dynamic viscosity. Kinematic viscosity is measured by the noting the time required to pass a given volume of fluid under its own head through a small diameter tube. A *Saybolt viscosimeter* is most commonly used.

Units of kinematic viscosity are $m^2/s$ or $centistokes$ or $ft^2/s$

$1\ stoke = 1\ cm^2/s$
## Heat of Vaporization & Fusion
Fusion - heat  necessary to change a unit mass of liquid into solid state at constant temerature.
Vaporization - heat  necessary to change a unit mass of solid or liquid into gaseous  state at constant temerature.
## Bulk Modulus
Bulk modulus $\beta$ is a measure of fluid compressibility. It can be calculate adiabatic or iso thermal

$$\beta = -V\left(\frac{\partial \rho }{\partial V}\right)$$

#### REFPROP
English Units
```Excel
=AdiabaticCompressibilty("Air","TP","E",80.33, 14.6959)
units are 1/psia
```

##  Volumetric Thermal Expansion Coefficient
$\beta$ is volumetric thermal expansion coefficient (volume expansivity in [[REFPROP]])
i.e. fractional change in density to a change in temperature at constant pressure

$$\beta = -\frac{1}{\rho}\left(\frac{\partial \rho }{\partial T}\right)_p$$

ideal gas $\rho=p/RT$ and the above equation reduces to 

$$\beta=\frac{1}{T}$$

#### REFPROP
English Units
```Excel
=VolumeExpansivity("Air","TP","E",80.33, 14.6959)
units are 1/°R
```
