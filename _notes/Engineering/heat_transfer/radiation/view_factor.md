---
title: View Factor
---
View Factor is also called **form factor**, **shape factor** or **configuration factor**

View factor is a metric of how well a surface can "see" another sufrace. If you draw a hemisphere from one flat surface (i.e. fisheye view), then how much of the fisheye view is blocked by a surface of interest

It is a number between 0 and 1. It expresses  the portion of radiative heat flux that leaves one surface that impacts another surface.  It is purely based on geometry.

View Factors are parts of [[Radk|Grey Body Factor]]

## 1. Definition view factors
It depends on three factors
- Area of the two surfaces $A_i$ and $A_j$
- distance between surface $r_{12}$
- angle between surface normals ($\theta_i$ and $\theta_j$)

$$dF_{ij}=\frac{1}{A_i}\int_{A_i}\int_{A_2} \frac{cos\theta_icos\theta_j}{\pi r_{12}^2}dA_i dA_j$$
View factor depends on what is source and target if the source and targets have different areas
$$F_{ij}A_i=F_{ji}A_j$$

All radiation emitted from a face to all other faces in the domain should add up to 1 if it is radiating inside a closed domain

## 2. Calculating view factors
Analytical calculation of view factors is complex even for the simplest of geometries. Hence numerical methods are used. Following methods are some of the techniques used
- Double area summation
- Nusselt Sphere technique
- Crossed-String Technique
- Monte-Carlo ray tracing
- Contour integration
- Hemi-cube
- Quadrature
- Newton Cotes Integrals

### 2.1. Double Area Summation Method
Instead of doing an integration, we just split the area into small finite elements of area $\Delta A$ and use summation

$$dF_{ij}=\frac{1}{A_i}\sum_{i=1}^n\sum_{j=1}^m \frac{cos\theta_icos\theta_j}{\pi r_{12}^2}\Delta A_i \Delta A_j$$
### 2.2. Nusselt Sphere Method
To calculate the view factor of an area $dA_1$ (think a small satellite) to a large spherical surface 2 (think a planet) is calculated as follows
- Draw a hemisphere of unit radius around $dA1$
- Draw tangents from the $dA1$ surface to the large surface 2
- Consider where the tangents intersect the unit hemisphere into a circle and project that down towards $dA1$. The projected circle has an area $A_p$
- Form factor is $A_p$ divided by area of unit hemisphere's circular base (unit circle)
### 2.3. Monte Carlo Ray Tracing Method

Monte Carlo method uses random numbers to perform integration. Let us suppose you have  4 surfaces A, B, C and D. If you shoot 1000 rays from surface A from bunch of random points on it in bunch of random directions (different azimuth $\theta$ and elevation $\phi$), let us suppose 200 rays hit surface B, 150 hit surface C and 80 hit surface D. The rest escape to ambient. View factor $FF_{AB}$ is 0.2, $FF_{AC}$ is 0.15 and so on. In all cases sum of view factors should be 1.

## 3. References
- [A Catalog of Radiation Heat Transfer Configuration Factors (thermalradiation.net)](http://www.thermalradiation.net/indexCat.html)
