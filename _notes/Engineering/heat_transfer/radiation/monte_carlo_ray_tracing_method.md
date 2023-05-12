---
title: Monte-Carlo Ray Tracing Method
---

With modern computers, Monte-carlo ray tracing methods are widely used for [[view_factor]] and [[Radk|interchange factor]] calculation

## 1. View Factor Calculation
Rays are shot at random directions for surface $i$. View factor is calculated based on number of rays that hit a surface $j$ divided by the number of rays shot from a surface $j$

## 2. Grey body factor calculation
For calculating grey body factors, the rays emitted from a source surface at an energy equal to the emissivity of the source surface. They are not terminated once they hit a target surface (as in the case while calculating view factors) but are reflected carrying a fraction of the original energy (based on the emissivity of the target surface). When the ray loses energy below a tolerance value, it is eventually absorbed. Or if it goes to space, it is terminated

