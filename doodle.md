

DRT calculations are based on the following expressions :

$$
Z(\omega)-R_{\infty}=R_{\mathrm{pol}} \int_{-\infty}^{+\infty} \frac{G(\tau) \mathrm{d} \ln (\tau)}{1+\mathrm{i} \omega \tau}
$$

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
 
For example, if we consider only the imaginary part of the impedance, the system can be described as :

$$
\left(\begin{array}{c}
Z_{1}^{\prime \prime} \\
\vdots \\
\vdots \\
Z_{m}^{\prime \prime}
\end{array}\right)=\left(\begin{array}{ccc}
\frac{-\omega_{1} \tau_{1}}{1+\left(\omega_{1} \tau_{1}\right)^{2}} & \cdots & \frac{-\omega_{1} \tau_{m}}{1+\left(\omega_{1} \tau_{m}\right)^{2}} \\
\vdots & \ddots & \vdots \\
\frac{-\omega_{m} \tau_{1}}{1+\left(\omega_{m} \tau_{1}\right)^{2}} & \cdots & \frac{-\omega_{m} \tau_{m}}{1+\left(\omega_{m} \tau_{m}\right)^{2}}
\end{array}\right)\left(\begin{array}{c}
b_{1} \\
\vdots \\
\vdots \\
\vdots \\
b_{m}
\end{array}\right)
$$


We note with $\lambda$ the Tikhonov regularization parameter.

$$
\min_{b}\left{\left\|\boldsymbol{K}\boldsymbol{b}\boldsymbol{Z}^{\prime\prime}\right\|_{2}^{2}+\lambda^{2}\|\boldsymbol{b}\|_{2}^{2}\right\}
$$





$$
\boldsymbol{b}=\left(\boldsymbol{K}^{T} \boldsymbol{K}+\lambda^{2} \boldsymbol{I}\right)^{-1} \boldsymbol{K}^{T} \boldsymbol{Z}^{\prime \prime}
$$

where $\boldsymbol{I}$ is the identity matrix.

This system can be solved for either real or imaginary part of impedance, or for both. Yappari can use either one of the three possibilities (I believe the best choice is to use both Zr and Zi, since they are related by Kramers-Kronig equations).
