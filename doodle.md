

DRT calculations are based on the following expressions :

$$
Z(\omega)-R_{\infty}= \int_{-\infty}^{+\infty} \{g(\tau) \mathrm{d} (\tau)}
where $G(\tau)=\tau \gamma(\tau)$.

In a log-scale grid we obtain a linear system of equations of the form $\mathbf{A} \vec{b}=\vec{Z}$

The components of matrix $A_{m, n}$ are given by, for the real part of the impedance :

$$
A_{m, n}=\frac{R_{p o l} \delta \ln \left(\tau_{n}\right)}{1+\omega_{m}^{2} \tau_{n}^{2}}, \quad \delta \ln \left(\tau_{n}\right)=\ln \left(\tau_{n+1}\right)-\ln \left(\tau_{n}\right), \quad \tau_{n}=1 / \omega_{n}
$$

and the components of the matrix for the imaginary part are

$$
A_{m, n}=-R_{\mathrm{pol}} \frac{\omega_{m} \tau_{n} \delta \ln \left(\tau_{n}\right)}{1+\omega_{m}{ }^{2} \tau_{n}{ }^{2}}, \quad \delta \ln \left(\tau_{n}\right)=\ln \left(\tau_{n+1}\right)-\ln \left(\tau_{n}\right)
$$
 
An approximate solution is 

$$
\boldsymbol{b}=\left(\boldsymbol{A}^{T} \boldsymbol{A}+\lambda^{2} \boldsymbol{I}\right)^{-1} \boldsymbol{A}^{T} \boldsymbol{Z}
$$

where $\boldsymbol{I}$ is the identity matrix and $\lambda$ is the Tikhonov regularization parameter.

This system can be solved for either real or imaginary part of impedance, or for both. Yappari can use either one of the three possibilities (I believe the best choice is to use both Zr and Zi, since they are related by Kramers-Kronig equations).

