---
title: Methods for Calculating Friction Factor
---
up::[[Friction Factor]]

The Darcy friction factor is a function of

$$f_d = fnc(Re_D, \frac{\epsilon}{D}, duct\ shape)$$

For everything other than laminar flow, emperical correlations need to be used to obtain friction factor.

## 1. Laminar Flow

$$f_D=\frac{64}{Re}$$

## 2. Turbulent Flow
### 2.1. Colebrook Equation
Also called Colebrook-White. It is the classic formulation for Darcy friction factor. However it is implicit ($f_D$ term is in both left and right sides of the equation) and needs iteration

$$\frac{1}{\sqrt{f_D}}=-2log_{10}\left[\left(\frac{\varepsilon /D}{3.7}\right) + \frac{2.51}{Re\sqrt{f_D}}\right]$$

It was developed by Colebrook in 1939 extending work of Nikuradse who was a student of Prandtl. It was been plotted by Moody in 1944 into what is known as [[Moody chart]]

### 2.2. Haaland Equation

Haaland equation provides the Darcy friction factor similar to Colebrook equation. This was derived for a full flowing circular pipe for both laminar and turbulent flows.  It is easier to use than Colebrook equation since it can be solved explicitly

$$\frac{1}{\sqrt{f_D}}=-\frac{1.8}{n}log\left[\left(\frac{\varepsilon /D}{3.7}\right)^{1.11n} + \left(\frac{6.9}{Re}\right)^{n}\right]$$

where,

$\varepsilon /D$ is the pipes relative roughness
$Re$ is the [[Reynolds Number]]
n=1 for liquids and n=3 for gases

Reference: [Review of explicit approximations to the Colebrook relation for flow friction (hal.science)](https://hal.science/hal-01586547/document)

### 2.3. Petukhov equation
Darcy Friction Factor  for a *smooth* tube can be given by 

$$f_D = (0.790 ln(Re) - 1.64)^{-2}$$

for $10^4<Re<10^6$
