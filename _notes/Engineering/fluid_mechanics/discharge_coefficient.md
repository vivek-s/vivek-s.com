---
title: Discharge Coefficient
---

up: [[fluid_mechanics]]

## 1. Incompressible flow
Discharge coefficient of  a nozzle or a valve is the ratio of actual discharge to ideal discharge. For incompressible flow it can be expressed as
>
$$Q = C_dA_t\left[\frac{2(p_1-p_2)}{\rho(1-\beta^4)}\right]^{1/2}$$

where,

$Q$ - volumetric flow rate
$C_d$ - coefficient of discharge
$A_t$ - throat area
$p_x$ - pressure at location $x$
$\beta$ - diameter ratio (throat dia/inlet dia)
$\rho$ - density
$p_1$ and $p_2$ are *static* pressures

### 1.1. Velocity of approach factor
The $(1-\beta^4)^{-1/2}$ term is also known as *velocity-of-approach* factor

$C_dA$ is usually calculated for nozzles

$$C_dA_t=\frac{\dot{m}\sqrt{(1-\beta^4)}}{\sqrt{2\rho \Delta p}}$$

$\sqrt{(1-\beta^4)}$ looks like this
<iframe src= "https://www.desmos.com/calculator/tncq2kfukw?embed" width ="400", height="200" style= "border: 1px solid #ccc" frameborder=0/>

If $\beta$ is small (i.e inlet area >> throat area) , $\sqrt{(1-\beta^4)}$  can be ignored


### 1.2. Flow Coefficient
The following term is known as flow coefficient

$$\alpha = \frac{C_d}{(1-\beta^4)^{1/2}}$$

Expressed in terms of flow coefficient the mass flow rate is

$$\dot{m}=\alpha A_t \sqrt{2\rho\Delta P}$$

## 2. Derivation

Consider the following  figure showing flow through a sharp edged orifice. 
<img src="assets/orifice_flow.png" />

The flow  conditions are considered at three points 1) entrance conditions, t) throat conditions and 2) conditions at vena contracta, which is the narrowest area the flow goes through (it is downstream of the throat area)

Based on continuity,

$$A_1v_1=A_tv_t = A_2v_2$$

Assume circular pipe,

$$\pi\frac{D_1^2}{4}v_1=\pi\frac{d^2}{4}v_t = \pi\frac{D_2^2}{4}v_2$$

Note that we assume density is constant. $D_1$ is the diameter at the inlet and $d$ is the diameter at the throat.

$$v_1=\frac{D_2^2}{D_1^2}v_2$$

To get ideal flow rate, we will ignore friction and viscosity effects. Applying Bernoulli's equation between points 1 and 2

$$p_1+\frac{1}{2}\rho v_1^2 = p_2+\frac{1}{2}\rho v_2^2$$

substituting for $v_1$

$$p_1+\frac{1}{2}\rho \left(\frac{D_2}{D_1}\right)^4v_2^2=p_2+\frac{1}{2}\rho v_2^2 =$$

or 

$$v_2=\sqrt{\frac{2(p_1-p_2)}{\rho(1-(D_2/D_1)^4)}}$$

Since the exact vena contracta diameter depends on flow conditions, we would like to express this in terms of the throat diameter. Assume $D_2/D_1\approx d/D_1 =\beta$

The ideal flow rate would be

$$Q_{ideal}=A_t\sqrt{\frac{2(p_1-p_2)}{\rho(1-\beta^4)}}$$

The discharge coefficient is the ratio of Actual flow rate to ideal flow rate

$$C_d=\frac{Q_{actual}}{A_t\sqrt{\frac{2(p_1-p_2)}{\rho(1-\beta^4)}}}$$


Or 

$$Q_{actual} = C_dA_t\left[\frac{2(p_1-p_2)}{\rho(1-\beta^4)}\right]^{1/2}$$
# Reference
1. *Fluid Mechanics*, Frank White 