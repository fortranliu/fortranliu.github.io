---
layout: post
title:  "Turbulent Prandtl Number"
date:   2016-03-08 10:10
categories: 学术
tags: CFD
mathjax: true
---

In laminar flow the viscosity is used to compute the heat-flux using Fourier's law and a laminar, well defined, Prandtl number $Pr \equiv \frac{C_p \mu}{\lambda}$ as:
$$
q_j = -\lambda \frac{\partial T}{\partial x_j} \equiv -C_p \frac{\mu}{Pr} \frac{\partial T}{\partial x_j}
$$

Most turbulence models just give a turbulent eddy viscosity $\mu_t$. By setting a turbulent Prandtl number the turbulent heat flux can be estimated in the same way by just using the turbulent eddy viscosity that the turbulence mode predicts:

$$
q_j^{turb} \equiv C_p \overline{\rho u''_j T} \approx - C_p \frac{\mu_t}{Pr_t} \frac{\partial \widetilde{T}}{\partial x_j}
$$

Using a constant turbulent Prandtl number is a simplification and it is not fully correct. Experimentally a value of something close to 0.9 has been measured.

参考链接：
[CFD-ONLINE: Turbulent Prandtl Number](http://www.cfd-online.com/Forums/fluent/115585-turbulent-prandtl-number.html)
[CFD_ONLINE Wiki: Favre averaged Navier-Stokes equations](http://www.cfd-online.com/Wiki/Favre_averaged_Navier-Stokes_equations)