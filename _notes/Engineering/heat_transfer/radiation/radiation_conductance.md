---
title: Radiation Conductance
---
## 1. Radiation Conductance (Radk)
For analytical calcuation of radiation, bodies are represented as nodes and conductors. Nodes represent the object participating in radiation and might be represented with or without mass. Conductors are heat flow paths in a thermal resistance network

Radiation is modeled in thermal networks using radiation conductors which have a property of Radiation conductance or Radk ($G_{rad}$)

$$\dot q = G_{rad} \Delta T^4$$
Radk between two nodes $i$ and $j$ is the product of the emissivity of the node $\epsilon_i$, area of the node $A_i$ and [[Radk|grey body factor]] $B_{ij}$. 

$$(G_{rad})_{ij}=A_i \epsilon_i B_{ij}$$

Note that

$$A_i\epsilon_iB_{ij} =  A_j\epsilon_jB_{ji}$$


For solving in a thermal network software we would like linearize the above equation so that it looks similar to a conduction and convection problem.

$$\dot q = G_{rad} \Delta T^4 = G_{rad} [(T_1^2+T_2^2)(T_1+T_2)] \Delta T $$

## 2. References:
1. [Form Factors, Grey Bodies and Radiation Conductances | NESC Academy Online (nasa.gov)](https://nescacademy.nasa.gov/playlist/d70d74cb91ba4ad0bac3c178bd5626a454)