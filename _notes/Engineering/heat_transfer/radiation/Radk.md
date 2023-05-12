---
title: Radiation Conductance
---

## 1. Grey Body Factor
Gebhart factor or grey body factor is the ratio of energy absorbed by the target body $A_j$ originating from a source body $A_i$ *through all possible paths including reflections of other bodies* to the total radiation emitted by the source $A_i$ and is denoted by $B_{ij}$

$$B_{ij}=\frac{energy\ absorbed\ at\ A_j\ originating\ from\ A_i}{Total\ radiation\ emitted\ at\ A_i}$$
$$B_{ij}=\frac{\dot q_{ij}}{\dot q_i}$$
Grey body factor differs from view factors because it includes the reflective paths for radiant heat to flow from source $i$ to target  $j$.

Heat transfer between the two bodies is given by 

$$\dot q_{ij} = A_i\epsilon_iB_{ij}\sigma(T^4_i-T^4_j)$$

If there are $n$ bodies participating in radiation, then

$$\sum_{j=1}^n B_{ij} =1$$

## 2. Radiation Conductance (Radk)

Radiation Conductance (Radk) is defined as 

$$Radk_{ij}=A_i\epsilon_iB_{ij}$$

Hence the radiative heat transfer is given by

$$\dot q_{ij} = Radk_{ij}\sigma(T^4_i-T^4_j)$$

and following properties are true

$$A_i\epsilon_iB_{ij} =  A_j\epsilon_jB_{ji}$$



## 3. Calculating Grey Body Factors
### 3.1. Gebhart's Method
Gebhart's method uses previously calculated [[view_factor|view factors]] to calculate grey body factors.  So if there are $n$ opaque bodies, then

$$B_{ij} = \epsilon_j FF_{ij} + \sum_{k=1}^n((1-\epsilon_k) FF_{ik}B_{kj})$$
#### 3.1.1. Example - three body system
For illistration, if we consider only three bodies, we arrive at the following set of equations

$$\begin{alignat*}{4}
B_{11} = \epsilon_1 FF_{11} +(1-\epsilon_1) FF_{11}B_{11}+(1-\epsilon_2) FF_{12}B_{21}+(1-\epsilon_3) FF_{13}B_{31}\\

B_{21} = \epsilon_1 FF_{21}+(1-\epsilon_1) FF_{21}B_{11} +(1-\epsilon_2) FF_{22}B_{21}+(1-\epsilon_3) FF_{23}B_{31}\\

B_{31} = \epsilon_1 FF_{31}+(1-\epsilon_1) FF_{31}B_{11} +(1-\epsilon_2) FF_{32}B_{21}+(1-\epsilon_3) FF_{33}B_{31}
\end{alignat*}
$$

We can solve for them using methods for solving [[linear_system_of_equations|Linear System of Equations]]

Note that $(1-\epsilon)$ term is equal to the radiation reflected by a body since transmissivity is zero (opaque bodies assumption)

[[monte_carlo_ray_tracing_method| Monte-Carlo Ray Tracing Method]]
