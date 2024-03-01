# YAPPARI #
version 14-09-2023

__YAPPARI__ stands for Yet Another Program for Analysis and Research in Impedance.

This is a brief description of theorethical basis used in this program.

<details>
  <summary>Note to users</summary>

  There is no warrantee whatsoever for using this program. Use it if you want, see CC-BY-NC-ND [licence](https://creativecommons.org/licenses/by-nc-nd/4.0/), but you will probably not receive much help from me as everything is in the documentation files. If you don't want to use it... don't use it. There are many other programs, some commercial and some free... and likely some are better than this one. 
</details>

# やっぱり #

## Elements ##
The elements used are rather standard, the equations used in Yappari are described here.

### Zarc ###
A Zarc is a resistor R in parallel with a Constant Phase Element (or Q). If you fix the N value to 1, you'll get a capacitor instead of Q. The equivalent capacitance for a RQ circuit is C=((RQ)^1/n)/R. 

### Warburg ###
Warburg element represents semi-infinite diffusion to or from a flat electrode, expressed in this program as:

Z(ω)= A<sub>w</sub>/($\sqrt{ω})$ -jA<sub>w</sub>/($\sqrt{ω})$

This element contributes equally to Zr and Zi so it appears as a straight line in a Nyquist plot, at 45 degrees or a straight line in Bode plot (log |Z| vs. log ω) with a slope of value –1/2. The A<sub>w</sub> term is expressed in Ohm sec<Sup>-1/2</sup> and is called Warburg coefficient. It is expressed as

$$
A w=\frac{R T}{n^2 F^2 A \sqrt{2}}\left(\frac{1}{\sqrt{D o} \cdot C b_o}-\frac{1}{\sqrt{D r} \cdot C b_r}\right)
$$

with n - number of electrons, A - electrode surface area, D - diffusion coefficient of the electroactive species, Cb,o and Cb,r - bulk concentrations of oxidized and reduced species.

The parameters for Warburg in other programs are typically obtained by fitting a CPE with n=0.5, you will get the same result but the Q parameter obtained in this case is

A<sub>w</sub>=1/(Q $\sqrt{2})$

### Warburg open ###
For a finite space (or time) diffusion and if the thickness of the diffusion layer is known, two other models can be applied. The Warburg "open" describes the impedance of diffusion with __reflective boundary__. The formula used here is

Z<sub>o</sub>=(A<sub>w</sub>/ $\sqrt{jω})$ coth(B $\sqrt{jω})$

Here A<sub>w</sub> is the standard Warburg coefficient and B is B=d/ $\sqrt{D}$ , where d is the diffusion layer thickness and D is the diffusion coefficient.

### Warburg short ###
The Warburg "short" describes the impedance of a finite-length diffusion with __transmissible boundary__, with the expression:

Z<sub>s</sub>=(A<sub>w</sub>/ $\sqrt{jω})$ tanh(B $\sqrt{jω})$

Aw is the standard Warburg coefficient and B=d/ $\sqrt{D}$ as defined above. Note that some other impedance programs use Y0 (with units Siemens sec^1/2) instead of Aw for the Warburg parameters.

Fitting the Warburg short and Warburg-open parameters will be $very$ slow in this program as checks on the validity of the calculations are required, particularly for high frequencies where the calculated values are very small and may be translated as NANs (so, be patient with Warburgs open and short, or adjust manually the parameters before a final fit, starting from a good position in the solutions' space).

A very good introduction to all these parameters can be found [here](https://pubs.acs.org/doi/10.1021/acsmeasuresciau.2c00070).

## Fit ##
This command is used to fit the set of parameters that describes the circuit, if the circuit is valid (i.e., there are parameters to fit on the right side of the window) and if you have data. The user can select which parameters to fit and it is recommended to start with a few parameters first, ensuring that the initial values are close to the expected values. The simulated spectrum will be updated with every change in the parameters, and the user can perform manual adjustments as necessary. The data can be selected by standard click, ctrl+click,.. or if you want you can select all by using Ctrl+A.
For many datasets, the data are described by the same model circuit, I suggest to select one measurement, adjust the parameters manually to be close to solution, then fit. You may want to take a look at this [tutorial](https://github.com/nitad54448/yappari-5-1/blob/main/help/fit_multiple.pdf). After fit you can “Clone” these parameters to all other datasets and select all datasets, then _Fit all selected_ in a go.

The fitting can be performed using three different methods, although there is not much difference in the output of these methods (except for the esd, see below). 
The quality of the fit is evaluated using the R<sup>2</sup> statistical parameter and the chi<sup>2</sup> value. However, the use of the chi<sup>2</sup> value as a statistical parameter is debatable, as discussed in the paper "Dos and don'ts of reduced chi-squared" by Andrae et al. (https://arxiv.org/abs/1012.3754). The chi<sup>2</sup> value reported here is calculated as (Sum ((Z<sub>obs</sub>-Z<sub>calc</sub>)<sup>2</sup>/Z<sub>calc</sub>))/DOF. The degree of freedom (DOF) is considered as Nr_of_points - nr_of_fitted_params. 
The standard deviation is estimated, assumming independent errors, only for unconstrained Levenberg-Marquardt fit.

### DRT ###
This performs a calculation of Distribution of Relaxation Times for one or more datasets for the case of serial RC circuits. Thre are three methods used now in Yappari : constrained non-negative linear regression (NNLS) with a Tikhonov regularization parameter, a variant proposed by Fisk and finally a Gold optimization method. 

DRT calculations are based on the following expressions :

$$
Z(\omega)-R_{\infty}=R_{\mathrm{pol}} \int_{-\infty}^{+\infty} \frac{g(\tau) \mathrm{d} \ln (\tau)}{1+\mathrm{i} \omega \tau}
$$

with

$$
\int_{-\infty}^{+\infty} \{g(\tau) \mathrm{d} (\tau)} = 1
$$

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

This system can be solved for either real or imaginary part of impedance, or for both. Yappari can use either one of the three possibilities.

Data should be acquired with log spacing and with a decent number of points per decade (otherwise you may try to rearrange data with the command _spline>>number_ if you want a total _number_ interpolated datapoints scaled in log space).

The Tikhonov procedure used now in Yappari is a NNLS method implemented by [Christian Altenbach](https://sites.google.com/site/altenbach/Home) for EPR spectrocopy. This [method](https://sites.google.com/site/altenbach/labview-programs/epr-programs/long-distances/ld-algorithms) is very fast and therefore it is possible to search an optimal regularization parameter.
 
Fisk is a non-negative Least-squares (NNLS) procedure based on the Tikhonov algorithm and described in this [paper](https://arxiv.org/abs/1307.7345). This is an iterative method, with solution vector v= u^{2}, and u is obtained with

$$
u_\alpha^{(k+1)}=\omega u_\alpha^{(k)}+(1-\omega)\left(D\left(u_\alpha^{(k)}\right) A^T A D\left(u_\alpha^{(k)}\right)+\lambda I\right)^{-1} D\left(u_\alpha^{(k)}\right) A^T p
$$

where $\omega$ is a relaxation parameter, fixed at 0.1 in this program and $\lambda$ is the regularization parameter. 

In releases posterior to 5.1.69.2 there is also an iterative algorithm named Gold, based on this [paper](https://chemistry-europe.onlinelibrary.wiley.com/doi/10.1002/cphc.202200012). It does not require a fitting parameter like Tikhonov but a given number of iterations is requested. In my tests I had to use 10^4 iterations or more. In my tests on simulated data it works better for Zi data.

Criteria for selecting the optimal regularization parameters are included in this program. You can either use _DRT search_ command in "Action" menu or in __Advanced commands__ the command _drt_search_. Similarly, in  __Advanced commands__ you can use _drt_explore_ which allows you to obtain and save all drt data. _DRT_search_ and _drt_explore_ are CPU intensive and will be performed only on the first selected dataset.

The procedure I use here is to provide an indication of the frequencies of the relaxations. More advanced free DRT programs are available, see for instance [Ciucci et al](https://github.com/ciuccislab/DP-DRT) and his papers but there are some others. The DRT procedure may help in detecting a proper electrical circuit for serial RC circuits and to some extent to serial RQ circuits. If you want to use it, I suggest to read first some publications describing the procedure and the limitations.
The usefulness of DRT depends much on the quality of the data.

On the DRT graph, the experimental Zr and Zi are plotted together with the _recalculated impedances_ from the DRT data and a probability of distribution function. Calculations are made in real time if you change the regularization parameter, so if you have multiple datasets and many iterations, it may be slow. Some files to test are in the /drt folder.
An example of a DRT fit is shown below :

![plot](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/drt_calc_RCRC_1k_3_5microF_80_20p_simulated.PNG)
Red dots are experimental Zr and the red line is calculated Zr based on the distribution function as RC (blue dots and line are experimental and calculated Zi values). The green spikes are calculated relaxation times. The fit is very good and corresponds well with the simulated values calculated only from the "experimental" imaginary impedance. 
Only the first selected dataset will be shown on the DRT graph, if the DRT calculation was performed for that dataset.

If you hold the mouse on the graph a Tip with an estimation of RC values will be shown (or you can right click on the graph and look for Description and Tips). These parameters are calculated based on the Rpol and the surface of the peaks and can be used as starting points for fitting a model. 


## Advanced commands ##
These can be used for manual control of program, useful mostly for testing. 

### Smooth ###
To make a Savitzky-Golay smooth of the active datasets you may use:

    smooth
    
This will create new smoothed datasets with the same name and the prefix sm_. By default the number of sidepoints and the polynomial degree are 5 and 2 respectively. If you want o change them specify the new values

    smooth>>7&3

### Interpolate ###
You can interpolate to log scale or upscale by spline interpolation (i.e. getting "artificially" more points). You can try it, if you don't have spurious points. The command with 128 points as default is :

    spline

you will get 128 points from your data, in a log scale. It might not be good to increase too much the number of points from he original ones, nor to use this function on noisy data. This command will create new datasets for every selected dataset, so you can play around to see how it is working. The log scale is important for DRT and Z-hit. For a different number of points you may use :

    spline>>100

### Noise ###
To add white noise to the selected impedance datasets in the range Z-1% to Z+1%   
    
    rndz>>1 

while
  
    rndzr_>>0.5
    
will add white noise to the real part of the impedance in the range Z-0.5% to Z+0.5%
Other accepted parameters are _rndzi>>u_ for Zi white noise and _rndf>>u_ for frequency.

### Average ###
The command 

     average
     
will calculate the mean of Zr and Zi for the selected datasets. This function has a sense if it is applied to datasets measured at the same frequencies.

### DRT search ###
You can search the best regularization parameter for DRT calculations. The command :
 
    drt-_search>>0.0002&0.1&256 
    
will calculate 256 DRT in the range 0.0002 and 0.1 and reconstruct all the 256 impedance sets. The best lambda parameter based on the minim squared error between the calculated and experimental sets will be shown. Obviously you can replace 0.0002, 0.1 and 256 with other values you want but you must separate them with _&_. No space should be in the command (you can use fractional or E string, for instance _search_lambda>>1E-6&2E-2&200_ is accepted). The interval of lambda will be scaned in log spacing over the interval specified with _start_value&stop_value&steps_

For a default range search (10E-4 to 10E-1 for Tikhonov or Fisk, and 300 o 30000 fo Gold method) you can use the Action/DRT search or the manual command 

    drt_search

If you want to see all DRT data and save them, you can use

    drt_explore
   
This will plot a 3D graph with all DRTs as a function of lambda, like this graph.
![plot](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/explore_lambda.png)

You can modify the range for explore with similar commands, for 100 points in the 1 to 10 range

    drt_explore>>1&10&100


### Z-Hit active datasets ###
This option will provide a Z-HIT simulation (which is a Hilbert transform of the phase into the real part of the impedance) for one or more datasets. The procedure, when and why to use it, is described [here](https://en.wikipedia.org/wiki/Z-HIT). In this implementation I am using the corrections including the 5th derivative of the phase as described in the link given previously. This is a procedure similar to the better known Kramers-Kronig test.

--
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>


