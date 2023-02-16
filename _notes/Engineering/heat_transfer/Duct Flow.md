---
title: Heat Transfer in Duct Flows
---

Single phase flow through pipes is one of the most common scenarios in engineering applications. 

Key terms in the page

$Nu_D$ -  [[Nusselt Number]]
$Re_D$ - [[Reynolds Number]]
$Pr$ -  [[Prandtl Number]]

## 1. Dittus Boelter
For a *smooth* tube with *small* temperature difference across the fluid in the thermal boundary layer
$$Nu_D=0.023Re^{4/5}_DPr^n$$

where,
$n$ = 0.4 for heatint (wall temp > fluid temp) and $n$=0.3 for cooling (wall temp < fluid temp)

valid for 

$$\begin{bmatrix}  
0.7 \le Pr \le 160\\  
Re_D \ge 10000\\
L/D \ge 10
\end{bmatrix}$$

The properties of the fluid need to be ealuated at film temperature or mean fluid temperature $T_f = (T_s + T_f)/2$ 

## 2. Gnielinski
Gnielinski's formulation is  more accurate compared to Dittus Boelter. It is also for *smooth* pipes

$$Nu_D=\frac{(f_D/8)(Re_D-1000)Pr}{1.07+12.7(f_D/8)^{0.5}(Pr^{2/3}-1)}$$

valid for 

$$\begin{bmatrix}  
0.5 \le Pr \le 2000\\  
3000 < Re_D < 5 \times 10^6\\
L/D \ge 10
\end{bmatrix}$$

The properties of the fluid need to be ealuated at film temperature or mean fluid temperature $T_f = (T_s + T_f)/2$ 

## 3. Chilton-Colburn
It is a simpler expression for turbulent flow through *smooth* pipes. It is not accurate as above options. 

$$Nu_D=0.125f_DRe_DPr^{1/3}$$

Reference: *"Heat and Mass Transfer: Fundamental and Applicaitons"*, Cengel & Ghajar