DRT calculations are based on the follwing expressions :



$$
Z(\omega)-R_{\infty}=R_{\mathrm{pol}} \int_{-\infty}^{+\infty} \frac{G(\tau) \mathrm{d} \ln (\tau)}{1+\mathrm{i} \omega \tau}
$$

where $G(\tau)=\tau \gamma(\tau)$.

In a log-scale grid we obtain a linear system of equations of the form $\mathbf{A} \vec{G}=\vec{Z}^{\prime}$

$\mathbf{A} \vec{G}=\vec{b}, \quad \vec{b} \equiv \vec{Z}_{r e}-R_{H F R}$

where the components of matrix $\mathbf{A}$ are given by

$$
A_{m, n}=\frac{R_{p o l} \delta \ln \left(\tau_{n}\right)}{1+\omega_{m}^{2} \tau_{n}^{2}}, \quad \delta \ln \left(\tau_{n}\right)=\ln \left(\tau_{n+1}\right)-\ln \left(\tau_{n}\right), \quad \tau_{n}=1 / \omega_{n}
$$
 The numerical approximation for the imaginary part is $\mathbf{A} \vec{G}=\vec{Z}^{\prime \prime}$ where the matrix $A_{m, n}$ is

$$
A_{m, n}=-R_{\mathrm{pol}} \frac{\omega_{m} \tau_{n} \delta \ln \left(\tau_{n}\right)}{1+\omega_{m}{ }^{2} \tau_{n}{ }^{2}}, \quad \delta \ln \left(\tau_{n}\right)=\ln \left(\tau_{n+1}\right)-\ln \left(\tau_{n}\right)
$$

The remaining part of the algorithm is described by eqn (9)-(11) with the evident replacement $\gamma$ by $G$. Note that in eqn (27) and (28),



