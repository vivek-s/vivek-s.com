---
title: Solving Spring-Mass-Damper ODE with Matlab and Python
---

## 1. Solving a Spring-Mass -Damper system

Notes created after watching https://youtu.be/shOPcVublVA?t=2668

Consider a simple spring-mass-damper system which has the following governing equation

$$\ddot x + 2 \zeta \omega_n \dot x + \omega_n^2 x = 0$$

where,
$\omega_n$ is the undamped natural frequency 
$\zeta$ is the damping factor.

Let the initial condition be
Initial displacement  $x_0 = 0$
Initial velocity $v_0=2$

Expressed in terms of velocity $v$

$$\dot x =  v $$
$$\dot v = - \omega_n^2 x -2 \zeta \omega_n v $$

This can be written as
$$\frac{d}{dt}
\begin{bmatrix}
x \\
v\\
\end {bmatrix} =  \begin{bmatrix} 
0& 1 \\
- \omega_n^2 & -2 \zeta \omega_n 
\end{bmatrix}
\begin{bmatrix}
x \\
v\\
\end {bmatrix}
$$


### 1.1. MATLAB
The linear system of odes can be solved using the `ode45` method. Following code can be 

```MATLAB
w = 2 * pi; % natural frequency
zeta = 0.25; % damping factor

A = [0 1; -w^2 -2*zeta*w];

dt = 0.01; % arbitrary time step
T = 10; % total time to run the solution for

x0 = [2; 0]; % Initial Conditions

% ode45 solves linear expresssion of first derivative dy/dt = A *y 
[t,y] = ode45(@(t,y) A*y, 0:dt:T, x0);
```

### 1.2. Python
Roughly equivalent code in python using `solve_ivp` function from `scipy` is
```python
import numpy as np
from scipy.integrate import solve_ivp

w = 2 * np.pi # natural frequency
zeta = 0.25 # damping factor

A = np.array([[0, 1], [-w**2, -2*zeta*w]])

dt = 0.01 # max time step
T = 10 # total time to run solution for

x0 = np.array([0,2]) # initial conditions

sol = solve_ivp(lambda t,y: A.dot(y), [0,T], x0, max_step=dt)
```


