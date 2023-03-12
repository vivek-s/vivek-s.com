---
title: View Factor
---
View factor is the portion of radiative heat flux that leaves one surface that impacts another surface. 
It is purely based on geometry.

$$0 <F_{ij} < 1$$
### 0.1. Calculation of view factors
It depends on three factors
- Area of the two surfaces
- distance between surface
- angle between surface normals

$$dF_{ij}=\frac{cos\theta_icos\theta_j}{\pi s^2}dA_j$$
View factor depends on what is source and target if the source and targets have different areas
$$F_{ij}A_i=F_{ji}A_j$$

All radiation emitted from a face to all other faces in the domain should add up to 1 if it is radiating inside a closed domain

If you have 1000 elements view factor matrix will be 1000 x 1000. i.e. view factor from each element to each other element must be calculated

