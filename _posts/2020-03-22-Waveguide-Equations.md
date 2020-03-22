---
title: 'Second Order Equations of Waveguide Problem'
date: 2020-03-22
permalink: /posts/2020/03/Waveguide-Equations/
tags:
  - PINN 
  - Waveguide 
  - Buris 
---

# Solving Ractangular Waveguide Problem using Deep Learning
## 1. $TE_{mn}$ modes in Rctangular Waveguide

The analysis of $TE_{mn}$ modes starts with the wave equation for $H_{z}$, that is  

$$
\tag{1} \nabla^{2} H_{z}+k^{2} H_{z}=0 
$$

Other components of electric field and magnetic field can be expressed on the top of $H_{z}$ 

$$
\tag{2}
E_{x}=\frac{-j w \mu_{0}}{k^{2}-\beta^{2}} \frac{\partial H_{z}}{\partial y} \\
E_{y}=\frac{j w \mu_{0}}{k^{2}-\beta^{2}} \frac{\partial H_{z}}{\partial x} \\
H_{x}=\frac{-j \beta}{k^{2}-\beta^{2}} \frac{\partial H_{z}}{\partial x} \\ 
H_{y}=\frac{-j \beta}{k^{2}-\beta^{2}} \frac{\partial H_{z}}{\partial y} 
$$

boundary conditions are

$$
\tag{3}
E_{y}(0, y, z)=E_{y}(a, y, z)=0 \\ 
E_{x}(x, 0, z)=E_{x}(x, b, z)=0 
$$

The exact $H_{z}$ is

$$
H z(x, y, z)=H_{0} \cos \left(k_{x} x\right) \cos \left(k_{y}y\right) e^{-j \beta z}, \quad (k_{x}= \frac{m \pi}{a},k_{y}= \frac{m \pi}{a}) 
$$

So we have the solution

$$
\begin{aligned}
H_{x} &=\frac{-j \beta \frac{\partial H_{z}}{\partial x}}{k^{2}-\beta^{2}}=\frac{j \beta H_{o} k_{x} \sin \left(k_{x} x\right) \cos \left(k_{y} y\right) e^{-j \beta z}}{k_{x}^{2}+k_{y}^{2}} \\
H_{y} &=\frac{-j \beta \frac{\partial H_{z}}{\partial y}}{k^{2}-\beta^{2}}=\frac{j \beta H_{o} k_{y} \cos \left(k_{x} x\right) \sin \left(k_{y} y\right) e^{-j \beta z}}{k_{x}^{2}+k_{y}^{2}} \\
E_{y} &=\frac{j \omega \mu_{o} \frac{\partial H_{z}}{\partial x}}{k^{2}-\beta^{2}}=\frac{-j \omega \mu_{o} H_{o} k_{x} \sin \left(k_{x} x\right) \cos \left(k_{y} y\right) e^{-j \beta z}}{k_{x}^{2}+k_{y}^{2}}\\
E_{x} &=\frac{-j \omega \mu_{o} \frac{\partial H_{z}}{\partial y}}{k^{2}-\beta^{2}}=\frac{j \omega \mu_{o} H_{o} k_{y} \cos \left(k_{x} x\right) \sin \left(k_{y} y\right) e^{-j \beta z}}{k_{x}^{2}+k_{y}^{2}}
\end{aligned}
$$

## 


Headings are cool
======

You can have many headings
======

Aren't headings cool?
------