# yappari-v5-2023
Yappari 5.1, Windows 10, compiled with Labview 2023
version 16th of July 2023

This is an application that requires Labview 2023 64 run time engine. You may have this "engine" if you have previously installed Yappari or other program written in LV2023. If you don't have it, you should use the full installer which can be download from __Releases__ link, on the righ side of this page.

__YAPPARI__ stands for Yet Another Program for Analysis and Research in Impedance.
This program can be referenced in publications as http://dx.doi.org/10.13140/RG.2.2.15160.83200

This program can perform multiple datasets fits. For a single dataset you may want to use a simpler program called [Yappari 4.2](https://github.com/nitad54448/win10-installer-yappari-4.2), available also as a Windows 10 installer. This single dataset program will not be developed further.

You are encouraged to contribute to this help file, you can send it to me or fork it on Github. As much as I like programming, writing documentation is boring. A short tutorial is included in the help pdf file which is installed with the exe file. Otherwise, the most updated description of the program is always here on this page.
It is generally a good idea to read a help file before using the program, but if you are in a hurry, this is what you should do :

  - select string delimiter on the Parameters page (essential, if you are using MFLI csv or 3 columns file)
  - read some data
  - build a model
  - fit



# Panels #
The program has several graphic panels and a parameter list with several commands grouped on the right side of the window.

## Zr, -Zi ##
This panel shows a Nyquist plot, which is a standard way to visualize impedance data. The scale on the graph will adjust automatically based on the data, with the same axis range for the imaginary part and real part. However, if you want to manually set a specific range, you can disable the Auto-axis feature by clicking on the graph, or directly changing the scale in the legend. Some other standard graph functions are available in the top left "palette" such as zoom in, out... etc. All graphic panels will plot experimental and simulated data (if any) of selected datasets.
The change of the plot colors, style, etc.... in this graph will affect all the graphs.

## Zr, Zi, ln R, theta ##
These panels will show the dependency of impedances (real, imaginary, modulus or phase) as a function of frequency and the differences between the calculated and experimental values (if any).

## 3D plot ##
This panel will show a 3D plot of selected datasets, either in Nyquist, Zr or Zi or their difference, as selected by the user. This is useful for many datasets, more than 20 I guess, it will allow the user to see tendencies or check systematic errors in the fits. You can right click on the graph to adjust plotting properties to your liking (3D Plot Properties) or change the size of the graph.

## Model ##
A model can be created by the user in this panel, by selecting element circuits. 
Up to ten elements can be added in the circuit (obviously it is not realistic to fit such a circuit, unless you want to fit a crocodile). Only the first 18 parameters will be shown in the right side of the program.
When you click on one of the ten available cases, a new window will appear where you can select the element you want to add. Simply click on the picture of the element you want to add and it will be added to the model. The available circuit elements include resistors, capacitors, inductors, and more complex elements such as constant phase elements or Warburg elements (see below).

You can edit the png image files to your liking (just for aesthetics, the calculations are not affected), they are in the subdirectory __/models__. The size of the png files should be 150x100 pixels.

### Elements ###
The elements used now (as of march 2023) are: Resistor, Capacitor, Inductor, CPE, Zarc, simple Randles circuit, Randles with kinetic and diffusion, Warburg (semi-infinite linear diffusion), Warburg short, Warburg Long, Gerischer, Havriliak-Negami and several compositions of these.

Warburg element represents semi-infinite diffusion to or from a flat electrode, expressed here as:

Z(ω)= A<sub>w</sub>/($\sqrt{ω})$ -jA<sub>w</sub>/($\sqrt{ω})$

This element contributes equally to Zr and Zi so it appears as a straigh line in a Nyquist plot, at 45 degrees or a straight line in Bode plot (log |Z| vs. log ω) with a slope of value –1/2. The A<sub>w</sub> term is expressed in Ohm sec<Sup>-1/2</sup> and is called Warburg coefficient. It is expressed as

<img src="https://latex.codecogs.com/svg.image?Aw&space;=&space;\frac{RT}{{n^2&space;F^2&space;A&space;\sqrt{2}}}&space;\left(\frac{1}{{\sqrt{Do}&space;\cdot&space;Cb_o}}&space;-&space;\frac{1}{{\sqrt{Dr}&space;\cdot&space;Cb_r}}\right)" title="https://latex.codecogs.com/svg.image?Aw = \frac{RT}{{n^2 F^2 A \sqrt{2}}} \left(\frac{1}{{\sqrt{Do} \cdot Cb_o}} - \frac{1}{{\sqrt{Dr} \cdot Cb_r}}\right)" />

with n - number of electrons, A - electrode surface area, D - diffusion coefficient of the electroactive species, Cb,o , Cb,r - bulk concentrations of oxidized and reduced species.

The parameters for Warburg in other programs are typically obtained by fitting a CPE with n=0.5, you will get the same result but the Q parameter obtained in this case is

A<sub>w</sub>=1/(Q $\sqrt{2})$

For a finite space (or time) diffusion and if the thickness of the diffusion layer is known, two other models can be applied. The Warburg "open" describes the impedance of diffusion with __reflective boundary__. The formula used here is

Z<sub>o</sub>=(A<sub>w</sub>/ $\sqrt{jω})$ coth(B $\sqrt{jω})$

Here A<sub>w</sub> is the standard Warburg coefficient and B is B=d/ $\sqrt{D}$ , where d is the diffusion layer thickness and D is the diffusion coefficient.

The Warburg "short" describes the impedance of a finite-length diffusion with __transmissible boundary__, with the expression:

Z<sub>s</sub>=(A<sub>w</sub>/ $\sqrt{jω})$ tanh(B $\sqrt{jω})$

Aw is the standard Warburg coefficient and B=d/ $\sqrt{D}$ as defined above. Note that some other impedance programs use Y0 (with units Siemens sec^1/2) instead of Aw for the Warburg parameters.

Fitting the Warburg short and Warburg-open parameters will be $very$ slow in this program as checks on the validity of the calculations are required, particularly for high frequencies where the values are very small and may be translated as NANs (so, be patient with Warburgs open and short, or adjust manually the parameters before a final fit, starting from a good position in the solutions' space).

A very good introduction to all these parameters can be found [here](https://pubs.acs.org/doi/10.1021/acsmeasuresciau.2c00070).

Some others functions can be added upon request, if I will have the time and if there is real interest for them.

### Create a model ###

When you create a model using the  editor, the circuit is not valid unless a flow of current can be calculated (but not a short-circuit). Once the circuit is valid, a LED labeled "valid" will light up on the model panel, indicating that the circuit is ready for use and you can see a list of all the parameters for each element of the circuit. 
_Note : the parameters will be listed only if you have loaded experimental data!_ If you forgot to load data and already built a model, you can read data then modify the model to check for its validity (for instance, replace one element with the same one, this will trigger a validity check in the program). However, in doing so, the paramaters of the model will be initialized to some dummy values. To see the experimental data and the simulaion you need to select one or several datasets.

Calculations of impedances are made whenever the parameter values are changed... _if the model is valid_ and if you have some data loaded. You can use the wheel of the mouse to evaluate the change in the output impedance with the change in the value of a parameter.

Each parameter, listed on the right side of the page, is labeled with a decimal, which indicates which element it belongs to. For example, the first element of the circuit will have parameters labeled as 0.x, the second element as 1.x, and so on. When you add a parallel RQ element to the first element of the circuit (a Zarc as element 0), you need to create "electrical contacts" in the next three elements (elements 1, 2, and 3, or 4,5 and 6, or 7, 8 and 9….) for the circuit to be complete. 
Otherwise, the circuit will be open and no impedance can be calculated. In other words all the elements of the circuit need to be properly connected for the circuit to be valid and for impedance calculations to be performed.

Let’s make a valid circuit, with a Zarc and three shorts. As the circuit is valid, with a Zarc in element 0 position, three parameters will appear in the tab of the right side of the panel: 0ZARR, 0ZARQ and 0ZARN; the names are rather self-explaining for the parameters describing a Zarc located in the position 0 of the circuit, with the three parameters describing a parallel RQ. You can use a RQ element and fix the N to 1 to obtain the equivalent RC circuit. The equivalent capacitance for a RQ circuit is C=((RQ)<sup>1/n</sup>)/R.

For a more complex circuit, you can find on the right side of the screen names such as 2MR1D, 2MQ2D, 2MN2D, 2MR3D, 2MR4D, 2MR5D, and 2MW6D. The first number, "2", indicates which element case the device is in. The letters "M" and "D" are internal notations that are used by the program to identify the device type, but they are not important for the user. The type of device is listed after the "M" notation, such as "R" for resistor or "W" for Warburg. 

The numbering of the devices goes from left to right and top to bottom. For example, the first device is a resistor and can be described by the parameter "2MR1D". The second device in the circuit is a Zarc, which is a combination of a constant phase element (CPE, or Q) in parallel with a resistor. This device is described by the parameters "Q2" and "N2". 

Overall, the notation is quite straightforward once you become familiar with the conventions used.


## Parameters ##
On this page you can adjust the parameters boudaries for TRDL and constrained Levenberg-Marquardt procedure. In addition the datafile separator can be selected here. When reading a MFLI csv file you have probably a _,_ or _;_ separator. You need to inspect the data file then select the proper string here. For 3 columns, _tabs_ are typically used. Note that the separator used here for reading will also be used for exporting the data files. 

## About ##
Brief help listing the version of the program. 

# Commands #
## Read data ##
This command opens a menu with several options as of now, designing which type of file to read. Note that reading a new file will just add more data wihtout losing the previous ones. You can remove some of the datasets with the command __Erase selected datasets__. You will need to select one or more datasets in order to plot them. 

__MFLI csv__
This is a ';' or ',' separated values file as obtained from MFLI/MFIA, a Zurich Instruments impedance analyzer. As in the Zview text file, multiple data sets can be saved or read from this file. In the data folder that is provided with this installer you can find such a file containing 34 measurements of the same sample. It would be boring and useless to fit all these 34 datasets one by one. Yappari-5 can handle such multiple data sets. You can select the separator string to be used in the Parameters page.

__Versa Studio par__
This type of file contains data delimited by <Segments> and >/Segments>. I did not exenisively checked this type of file, an example is given in the /data folder. 

__Zview txt__
This is a Zview file, also an ASCII type, that can hold multiple data sets. Yappari will read all datasets it finds in this file and insert them in the datasets listing, with a name taken from the file name and a suffix indicating the position in the file : the first datasets will have__0__, then __1__, .. and so on. The separator setting will not be used in reading this file.
  
__3 cols__
This reads a three-column ASCII file, which should be separated by tabs, ; or , and contain frequency in Hz, Zr, and Zi. The separator used can be selected in the Parameters page. It is important to note that for French users (and some others), the separator value should be a dot “.” and not a comma “,”. If the reading is successful, the dataset will be inserted in the first position with a name taken from the filename open. This name can be changed by the user. Only one dataset can be read with this command. 
The first line of these files can be a text (the program will try to detect and discard a comment in the first line; if it fails, just remove all comments from the file and try again).

In the /data folder you will find some datafiles, experimental or simulated with other impedance programs. 
  
  - _test_data.txt : is a three columns datafile, separated by Tabs with a simulated circuit R(RQ)(RQ)
  - dev3221_imps_0_sample_0000 is a measurement of a sample (including more than 20 datasets) as obtained with a MFLI/MFIA from Zurich Instruments; separator for this file is ';'
  - mod_dev3221_imps_0_sample_0000 is a Zview txt file, as obtained with MFLI instrument (one dataset)
  - R(CR)(CR)W.txt is a simulated dataset with a Warburg element in a three columns separated by tabs
  - R(CR)O.txt is a simulated dataset with a Warburg "short" element (three columns separated by tabs)
  - R(CR)T.txt is a simulated dataset with a Warburg "open" element (three columns separated by tabs)
  

## Method ##
This command allows the user to select the method used for nonlinear fitting. There are three methods available: Trusted Region Dog Led algorithm (TRDL), Constrained Levenberg Marquardt, and Levenberg Marquardt. The user can choose any of these methods, and if the model is robust, they should obtain the same results. 

For TRDL and Constrained LM, the fit is constrained to certain intervals that are listed on the Parameters page. Initial limits are rather large, for example, resistors are limited to the range of 1 mOhm to 1 GOhm, capacitors are between 10^-4 and 10^-14, and so on. You may need to adjust the parameters limits. I recommend to manually adjust the initial parameters to some values that describe correctly the spectra, start with TRDL and then make a final fit with the standard (unconstrained) LM method. The fitting results may depend on the starting parameters.


## Fit selected ##
This command is used to fit the set of parameters that describes the circuit, if the circuit is valid (i.e., there are parameters to fit on the right side of the window). The user can select which parameters to fit and it is recommended to start with a few parameters first, ensuring that the initial values are close to the expected values. The simulated spectrum will be updated with every change in the parameters, and the user can perform manual adjustments as necessary. 
For large datasets, if the data are described by the same model circuit, I suggest to select one measurement, adjust the parameters manually to be close to solution, then fit. After fit you can “Clone” these parameters to all other datasets and select all datasets, then Fit all selected in a go.

The fitting can be performed using different methods, which are discussed before, although there is not much difference in the output of these methods. The fitting process involves up to 8000 cycles for a dataset, and multiple iterations may be necessary, particularly if the initial values are far from the actual values.

The quality of the fit is evaluated using the R<sup>2</sup> statistical parameter and the chi<sup>2</sup> value. However, the use of the chi<sup>2</sup> value as a statistical parameter is debatable, as discussed in the paper "Dos and don'ts of reduced chi-squared" by Andrae et al. (https://arxiv.org/abs/1012.3754). The chi<sup>2</sup> value reported here is calculated as (Sum ((Z<sub>obs</sub>-Z<sub>calc</sub>)<sup>2</sup>/Z<sub>calc</sub>))/DOF. The degree of freedom (DOF) is considered as Nr_of_points - nr_of_fitted_params. 

## Datasets ##
This list box shows all the datasets in memory. You can select one or more datasets. The parameters listed are those of the dataset selected (or the first selected dataset if you have more than one selection). The datasets label can be edited.


## Action ##
This button can trigger several commands:

### Clone these parameters to all ### 
Copy the listed parameters to all datasets. Useful for bulk fitting.

### Save active exp datasets ###
This command allows you to save the *active* experimental data, that means the selected ones, to a single file in a specific format. The format is three columns, separated by the string you selected in the Parameters page, with frequency in Hz, Zr, and Zi. This is useful for simulating impedance spectra for a given model. All the datasets will be saved in a single file, each data susequenntly added, with its name, to the same file.

### Save active calc datasets ###
This command allows you to save the *active* calculated data to a file in a three columns format, separated by the string you selected in the Parameters page.

### Save active exp and calc datasets ###
This command allows you to save the *active* experimental data and calculated data, in a 5 columns ASCII file. Note that all datasets are saved in a single file, each dataset will be separated by the label of the set. This might be used to plot nicer graphs.

### Average active datasets ###
This command will calculate the mean of Zr and Zi for the selected datasets. This function can be applied to datasets measured at the same frequencies.

### Erase active datasets ###
Irreversible action removing one or more datasets and all related parameters from memory (by active one should understand “selected”)

### Report all ###
This command generates an HTML report containing information about the model used, the parameters used, the fitted parameters, and their standard deviation. It also includes images of the fit as well as all experimental and calculated data. The report is saved in your temporary directory and automatically opened in a browser. You can use the data in the report to create your own graphs or to check for any discrepancies. If you find any errors in the calculations, please report them so they can be corrected.

### Z-Hit active datasets ###
This option will provide a Z-HIT simulation (which is a Hilbert transform of the phase into the real part of the impedance) for one or more datasets. The procedure, when and why to use it, is described [here](https://en.wikipedia.org/wiki/Z-HIT). In this implementation I am using the corrections including the 5th derivative of the phase as described in the link given here. This is a procedure similar to the better known Kramers-Kronig test.
  
### Help ###
This will open a help file in a pdf format (the most recent help is always in this github page and not in the pdf file installed with the program).

## Exit ##
No need for explications on what this command does.

## Author ##
This program can be used freely and distributed according to CC-BY-NC-SA.
It was written in Labview 2023, National Instruments and it includes the JKI toolkits for Labview, © 2023, JKI. All rights reserved.

For questions or comments:

__Nita DRAGOE__, Université Paris-Saclay, ICMMO/SP2M, 91400 Orsay, France
  
### Changes ###
  -  16/06/2023 : after loading a datafile, the first dataset is selected automatically.
  -  15/06/2023 : the user can select the separator used for MFLI CSV and 3 columns file. The same separator (space, comma or TAB) will be used for saving files.
  -  14/06/2023 : added user selected boundaries for TRDL and constrained LM fit.
  -  12/06/2023 : added a fourth term in the Z-hit calculations (the one with the pi^7/604800). It's contribution is very small though.
  -  10/06/2023 : added the Z-hit calculation.
  
--
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>


