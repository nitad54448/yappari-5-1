# YAPPARI
version 19-02-2024

__YAPPARI__ stands for Yet Another Program for Analysis and Research in Impedance, it can be referenced in publications as http://dx.doi.org/10.13140/RG.2.2.15160.83200

This document applies to version 5.1.71.1 or after. For prior releases see the **/help** folder.

<details>
  <summary>About this program</summary>
  
This program can perform several mathematical operations of interest in impedance spectroscopy: non-linear parametric fits for one or multiple datasets, DRT, Hilbert transform, spectra simulations etc. For a single dataset and non-linear optimization you can use an old and simpler program [Yappari 4.2](https://github.com/nitad54448/win10-installer-yappari-4.2). 
This single dataset program is not developed further and it has limited features so it might be better to start with this version. Some theoretical notions are given in the [theory file](https://github.com/nitad54448/yappari-5-1/blob/main/docs/theory.md) in this repository.

You are encouraged to contribute to this help file or write tutorials. If you want to contribute to the help file or tutorials, send them to me and I will add them to this repository. As much as I like programming, writing documentation is boring. The most updated description of the program is always here on this page.
  
 </details>

<details>
  <summary>Note to users</summary>

  There is no warrantee whatsoever for using this program. Use it if you want, see CC-BY-NC-ND [licence](https://creativecommons.org/licenses/by-nc-nd/4.0/), but you will probably not receive much help from me as everything is in this documentation file. If you don't want to use it... don't use it. There are many other programs, some commercial and some free... and likely some are better than this one. 
</details>

<details>
  <summary>Tutorials</summary>

- [A quick start](https://github.com/nitad54448/yappari-5-1/blob/main/help/A_quick_start.pdf).
- [Basic introduction](https://github.com/nitad54448/yappari-5-1/blob/main/help/tutorial_YAPPARI_5_1.pdf).
- [Simulate_and_DRT](https://github.com/nitad54448/yappari-5-1/blob/main/help/Simulate_and_drt.pdf).
- [Fit multiple datasets](https://github.com/nitad54448/yappari-5-1/blob/main/help/fit_multiple.pdf).
- [Another general tutorial](https://github.com/nitad54448/yappari-5-1/blob/main/help/another_tutorial_yappari_24_jan_2024.pdf).
</details>

<details>
  <summary>Changes</summary>

## Changes 
   - February 19, 2024 : Custom data format is now defined with xml files. Configuration file is saved and read from /config. Default parameters and limits of the circuits can be changed by editing the /config/*.xml files or by using an additional program provided here. Release 5.1.71.1
   - February 14, 2024 : Project files (all data, parameters, models) can be saved to or read from xml file. Release 5.1.71.
   - February 10, 2024 : Order of datasets can be changed by drag and drop. Release 5.1.70.6.
   - February 7, 2024 : Corrected an error in the "Report" function. Release 5.1.70.5.
   - February 4, 2024 : Changed the name of a function to drt_explore. Added a confirmation window to prevent accidental erase of datasets. Compiled on a Windwos 11 version (it should also work on Windows 10). 5.1.70.4.
   - December 21, 2023 : Added a multiplication factor for conversitng Ohm in Ohm cm or Ohm cm^2. Release 5.1.70.2.
   - September 20, 2023 : Fisk algorithm improvement; stop fitting if the changes in the solution are less than 0.25% than the norm of the vector u(k). Release 5.1.70.1.
   - September 19, 2023 : Changes in the Advanced commands (drt_search, drt_explore). Gold and Fisk DRT calculations are now included in the Action menu. Release 5.1.70.
   - September 14, 2023 : Minor changes in Advanced commands. Release 5.1.69.3.
   - September 13, 2023 : Added a Gold optimisation algorithm for DRT calculations. Tikhonov regularization parameter can be optimized based on the mean square error between experimental and reconstructed impedance. Release 5.1.69.2
   - September 12, 2023 : Calculating re-im cross-validation parameters. Release 5.1.69.1
   - September 11, 2023 : Memory optimizations for large arrays. Release 5.1.69
   - September 1st, 2023 : Added the command explore_lambda (will plot all DRT calculations for a range of lambda and the user can save all these data).
  -  August 30, 2023 : Added a config file; you can edit it to start with your own defaults. Removed hdf5 reading file, some errors appeared, problems with DLL linking (conflicts with python hdf5 dll's on some systems). Release 5.1.68.3 
  -  August 29, 2023 : The existing parameters are copied to the new datasets for Smooth and Spline functions. Release 5.1.68.3
  -  August 28, 2023 : More efficient 3D Plots. Active datasets can be removed with "Delete" key. Corrected an error in labelling Z-Hit datasets. Release tag 5.1.68.2
  -  August 26, 2023 : Changed the editing of parameters. Release tag 5.1.68.1
  -  August 25, 2023 : For cases of simple RC circuits, their values are estimated directly from the DRT plots (see Tips and Documentation in the DRT graph). Added a 2-Zarcs element. This release is named 5.1.68.
  -  August 23, 2023 : Changed the way _Max plots_ is used. In the past, the first _max_plots_ datasets were plotted; now the active datasets are decimated to the number _max_plots_.
  -  August 22, 2023 : Added the function DRT search lambda in the main Action menu.
  -  August 21, 2023 : Added a cursor on the lambda graph, it can be dragged to modify the value proposed by the program (see search_lambda in Advanced commands).
  -  August 20, 2023 : Show the criteria used in "Search lambda" procedure in a graph. Changed the way the data are saved. 
  -  August 19, 2023 : Changed the Report procedure. Added a simulate spectrum function. Release 5.1.67.4
  -  August 18, 2023 : Updated the documentation and files.
  -  August 17, 2023 : Added a spline interpolation function in "Developer commands", can upscale in log spaced frequency. Moved to version 5-1-65 as a new release.
  -  August 16, 2023 : Added a "Max plots" parameter on the Parameters panel.
  -  August 15, 2023 : DRT : plot only the first active dataset. 
  -  August 14, 2023 : The method of NNLS for DRT was changed to that of Altenbach. This version is much faster in DRT calculations.
  -  August 12, 2023 : Implemented a full DRT calculation for ore or more datasets (with a Tikhonov-type constrained non-negative parameters least-squares procedure, see the documentation for reference to the method used). Added the possibility to change the X-scale in DRT graph (sometimes is convenient to check the time constants). Added a debug/developper command to test things.
  -  August 10, 2023 : Cosmetics; DRT graph changed as a function of 1/&omega;
  -  August 9, 2023 : A rather simple calculation of DRT (Distribution of Relaxation Times) with unconstrained Tikhonov parametrisation has been added. The help command directs now to this page. In addition, an error in naming Z-Hit transformed files has been found and corrected. __This is a major upgrade, please use this version or later.__
  -  August 7, 2023 : Change in the error management in the fit process.
  -  August 6, 2023 : Small cosmetic changes, main font is the user system 15pt. Experimental points can now be removed from Nyquist, Zr, Zi and lnR plots.
  -  August 4, 2023 : Can copy parameters (aka clone) to active datasets. The number of iterations and stop limit are now adjustable parameters.
  -  August 2, 2023 : read impedance data from HDF5 data files. Some points can now be deleted from the Nyquist plot (see the Action menu).
  -  August 1st, 2023 : added an indication of the fitting progress.
  -  July 31, 2023 : increased he number of iterations to 10000 and decreased the limit step, erased an error that appeared when plotting more than 20 datasets
  -  July 29, 2023 : added the possibility to select which column to read if the data files have more columns or if the frequency is not in the first column
  -  July 28, 2023 : added the possibility to read custom definition files.
  -  July 16, 2023 : after loading a datafile, the first dataset is selected automatically.
  -  July 15, 2023 : the user can select the separator used for MFLI CSV and 3 columns file. The same separator (space, comma or TAB) will be used for saving files.
  -  July 14, 2023 : added user selected boundaries for TRDL and constrained LM fit.
  -  June 12, 2023 : added a fourth term in the Z-hit calculations (the one with the pi^7/604800).
  -  June 10, 2023 : added Z-hit calculation.
</details>


<details>
  <summary>Author</summary>

## Author
This program can be used freely and distributed according to CC-BY-NC-ND 4.0.
It was written in Labview 2023, National Instruments and it includes the JKI toolkits for Labview, © 2023, JKI and NI. All rights reserved.

For questions or comments (please do not ask questions unless you have carefully read this document):

__Nita DRAGOE__, Université Paris-Saclay, ICMMO/SP2M, 91400 Orsay, France

</details>

# Index
   - [How to install](#how-to-install)
   - [Panels](#panels)
     - [Zr, -Zi](#zr--zi)
     - [Zr, Zi, ln R, theta](#zr-zi-ln-r-theta)
     - [3D plot](#3d-plot)
     - [Model](#model)
     - [Elements](#elements)
     - [Create a model](#create-a-model)
   - [Parameters](#parameters)
     - [Max plots](#max-plots)
     - [Simulation limits](#simulation-limits)
     - [Advanced commands](#advanced-commands)
   - [About](#about)
   - [Read data](#read-data)
     - [3 columns](#3-columns)
     - [MFLI, csv](#mfli-csv)
     - [MFLI, Zview txt](#mfli-zview-txt)
     - [Versa Studio par](#versa-studio-par)
     - [Z-MFLI](#z-mfli)
     - [Custom](#custom)
     - [Read project, xml](#read-project-xml)
   - [Action](#action)
     - [Delete points from graph](#delete-points-from-graph)
     - [Delete active datasets](#delete-active-datasets)
     - [Apply correction to active](#apply-correction-to-active)
     - [Simulate spectrum](#simulate-spectrum) 
     - [Z-Hit active datasets](#z-hit-active-datasets)
     - [DRT active datasets](#drt-active-datasets)
     - [DRT search](#drt-search)
     - [Clone the parameters to all](#clone-the-parameters-to-all)
     - [Clone the parameters to active](#clone-the-parameters-to-active)
     - [Report active datasets](#report-active-datasets)
     - [Save active parameters](#save-active-parameters)
     - [Save data](#save-data)
     - [Save project, xml](#save-project-xml)
     - [Help](#help)
   - [Datasets](#datasets)
   - [Fit selected](#fit-selected)
 
# やっぱり #

## How to install
The recommended and simplest way to install this program is to use the full package which can be downloaded from [Releases](https://github.com/nitad54448/yappari-5-1/releases). Make sure you download the _Volume.zip_ file and not what is labelled as source file archives. Several versions are available, in general the last one is the best choice. In case of bugs please report them and grab an earlier version.

There is another way to install it, if you want to complicate things. Yappari 5.1 is compiled with Labview 2023. As such it will require a _Labview run-time engine_ which is installed, if needed, by the full installer. So, if you already have the run-time engine (either because you have peviously installed Yappari or you have installed another program compiled with Labview 2023) you can just download all the files from the green button __Code__ as a zip file. If you do not have the run-time engine but still want to go the hard way, you can download the LV 2023 engine freely from [ni.com](https://www.ni.com/fr/support/downloads/software-products/download.labview-runtime.html#484336) then get the zip file from __Code__. The files in __Code__ are always the latest version. For previous ones, look in [Releases](https://github.com/nitad54448/yappari-5-1/releases).

After installing the program in a directory of your choice, some other subdirectories will be created : **/config**, **/docs**, **/drt**, **/files**, **/help** and **/models**. The **/config** contains xml files with starting parameters for the program. The **/models** directory contains png files with images for showing circuits, **/files** and **/drt** contain some examples of data files and custom definitions.  The **/help** holds some tutorials and images for this document. You can remove **/drt**, **/files** and **/help** if you want but you must keep the **/models** and **/config** folders.

This program is supposed to work with Windows 10 64 bits or Win 11 and on my PC and many others it works fine; also it should work on win7 64bits, Win8 or Win8.1 as well but I am unable to test it on these systems.

## Panels
The program has several panels and a parameter list with several commands grouped on the right side of the window. When you start the program, if everything is normal, you should see something like this

![plot](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/panels.PNG)

### Zr, -Zi
This panel shows a Nyquist plot, which is a standard way to visualize impedance data. The scale on the graph will adjust automatically based on the data, with the same axis range for the imaginary part and real part. However, if you want to manually set a specific range, you need to disable the Auto-axis feature by right clicking on the graph and directly change the ranges. Some other standard graphic functions are available in the top left "palette" such as zoom in, zoom out... etc. All graphic panels will plot experimental and simulated data (if any) of selected datasets.
You can change the plot colors, style, etc.... by clicking on the label; the changes in this graph will affect all the other graphs, except for DRT. You can remove some outlier points by zooming in and use the command _Action_/_Delete points from Nyquist_. Points that are in that range are removed from all active datasets (equivalent with a mask, except that the removal of points is irreversible).
The number of plots can be selected by the user, see Max Plots on [Parameters](https://github.com/nitad54448/yappari-5-1#parameters) page. Note that, because of space limitations, only the first 24 plots will have legends. But you can plot as many datasets as you want (I tried 3700 datasets, see the tutorials, it is possible but slow to plot them and I wonder why you'd want to plot that many). 

### Zr, Zi, ln R, theta
These panels will show the dependency of impedances (real, imaginary, modulus or phase) as a function of frequency and the differences between the calculated and experimental values, something like this

![plot](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/fit_graph.PNG)

### 3D plot
This panel will show a 3D plot of selected datasets or a part of them, either in Nyquist, Zr or Zi or their differences, as selected by the user. This is useful for many datasets, more than 20 I guess, it will allow the user to see tendencies or check systematic errors in the fits. You can right click on the graph to adjust plotting properties to your liking (3D Plot Properties) or change the size of the graph. If you have many datasets, it will take some time to plot all data so to limit the waiting time, you may want to "decimate" the data for plotting). The number of plots shown is defined by the smallest value between the number of selected datasets and the "Max plots" value, see [Parameters](https://github.com/nitad54448/yappari-5-1#parameters). Depending on your computer, a few hunderth datasets can be plotted easily. If you try more than 1000 you'll have to wait, the program will appear irresponsive.
The 3D plot might be useful to look for tendencies, a plot looks like this :
![plot](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/Zidiff_3D.PNG)

### Model
In this panel a model can be created by the user, by selecting element circuits. 
Up to ten elements can be added in the circuit (obviously it is not realistic to fit such a circuit, unless you want to fit an [elephant](https://en.wikipedia.org/wiki/Von_Neumann%27s_elephant)). Only the first 18 parameters -more than enough- will be shown in the right side of the program.

![plot](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/page_model.PNG)

When you click on one of the ten available cases, a new window will appear where you can select the element you want to add. Simply click on the picture of the element you want to add to the model. The available circuit elements include resistors, capacitors, inductors, and more complex elements such as constant phase elements or Warburg elements (see below).

You can edit the png image files to your liking (just for aesthetics, the calculations will not be affected), they are in the subdirectory __/models__. The ideal size of the png files is 150x100 pixels.

### Elements
The elements used are rather common: Resistor, Capacitor, Inductor, CPE, Zarc, simple Randles circuit, Randles with kinetic and diffusion, Warburg (semi-infinite linear diffusion), Warburg short, Warburg Long, Gerischer, Havriliak-Negami and several compositions of these.

![plot](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/circuit.PNG)

Equations are described in the [theory](https://github.com/nitad54448/yappari-5-1/blob/main/help/theory.md) file. 

### Create a model

When you create a model using the  editor, the circuit is not valid unless a flow of current can be calculated (but not a short-circuit). Once the circuit is valid, a LED labeled __valid__ will light up on the model panel, indicating that the circuit is ready for use and you can see a list of parameters with some default values for each element of the circuit. You can change these default values see **Parameters** below.

_Note : the associated parameters will be listed only if your model is valid_. 

To see the experimental data and the simulation you need to select one or several datasets and the calculations will be made based on the model and the values of parameters for each dataset. If you select several datasets, the parameters of the first dataset are shown. If you modify a parameter while several datasets are selected, that parameter will be changed for all selected datasets.

Calculations of impedances are made whenever the parameter values are changed... _if the model is valid_ and if you have some data loaded or simulated. You can use the wheel of the mouse to evaluate the change in the output impedance with the change in the value of a parameter.

Each parameter listed on the right side of the page, is labeled with a decimal, which indicates which element it belongs to. For example, the first element of the circuit will have parameters labeled as 0.x, the second element as 1.x, and so on. For [this circuit](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/page_model.PNG) composed of two zarcs we need to close the circuit and make "electrical contacts" in other elements (elements 0 and 6) for the circuit to be valid. The parameters that will be listed for this circuit will be 4something and 5something (since the two elements are located on positions 4 and 5). 

![plot](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/param_values.PNG)

As the circuit is valid, with a Zarc in element 4 position and a Zarc in element 5 position, six parameters will appear in the tab of the right side of the panel: 4ZARR, 4ZARQ and 4ZARN and 5ZARR, 5ZARQ and 5ZARN; the names are rather self-explaining for the parameters describing a Zarc located in the position 4 of the circuit and a Zarc in the position 5. You can use a RQ element and fix the N to 1 to obtain the equivalent RC circuit. The equivalent capacitance for a RQ circuit is C=((RQ)<sup>1/n</sup>)/R.

For a more complex circuit, you can find on the right side of the screen names such as 2MR1D, 2MQ2D, 2MN2D, 2MR3D, 2MR4D, 2MR5D, and 2MW6D. The first number, "2", indicates which element case the device is in. The letters "M" and "D" are internal notations that are used by the program to identify the device type, but they are not important for the user. The type of device is listed after the "M" notation, such as "R" for resistor or "W" for Warburg. The numbering of the devices goes from left to right and top to bottom.

Overall, the notation is quite straightforward once you become familiar with the conventions used.

## Parameters
On this page you can adjust some parameters of the program. The basic parameters (but not the parameters related to electrical model) are loaded from a configuration file named **yappari_configuration.xml** that is located in **/config** folder. You can edit this file or save the actual values with **save_config** command in **Advanced commands**. 
The default circuit parameters are loaded from model definitions in **/config** xml files. You can edit all these xml to adapt the default values or the limits with the **change_default_parameters_xml.exe** program or by directly editing the **/config/*.xml** files. **Do not change** the names of the parameters in the xml files but only the numerical values. Edit xml files only if you understand what are you doing. Admin credentials are needed for **change_default_parameters_xml.exe** program).

For reading data the important point to remember is that the datafile separator _should_ be selected here. When reading a MFLI csv file you have probably a _,_ or _;_ separator. You need to inspect the data file then select the proper string here. For 3 columns, _tabs_ are typically used. Note that the separator used here for reading will also be used for exporting the data files. This data separator **will not be used** when reading files with a Custom configuration (in this case the definition file sets the separator to be used).

![plot](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/parameters.PNG)

The fitting algorithm (TRDL is the default) and the parameters bounds, if any, can be constrained to certain intervals that are listed on this page. Initial limits are rather large, for example, resistors are limited to the range of 1 mOhm to 1 GOhm, capacitors are between 10^-4 and 10^-15, and so on. You may need to adjust these parameters limits either on this page or the starting values that are located in the xml files (you can use the program change_default_parameters_xml). The fitting results may depend on the starting parameters since this is a non-linear system. You should probably start with TRDL to approach some values close to the solution then proceed with a LM fit. Note that esd's of the fitted parameters are calculated only for unconstrained LM fit.

The fit termination parameters can be adjusted here : by default they are set to 2000 iterations and a stop limit at 10E-15 or if you want them, the default values are in the program configuration file which can be edited or saved.
The same value listed as the maximum iteration number in this panel is used for DRT calculated with Gold or Fisk algorithms.

### Max plots
This is the maximum number of plots to show on the graphs (excluding DRT which will show only the first selected dataset). It should be small (up to about 200-300) if you are dealing with many datasets. The number of plots is determined by the number of selected datasets or this number, whichever is smaller. Note that I "decimate" the available data for plots, 3D plot is very slow if you have more than 200-300 datasets. Suppose you have 500 datasets selected (you can perform calculations on all of them), for plotting them it may be better to show only a part, let's say 200. The program will "decimate" the 500 datasets and show only 200, equally distributed among the 500. The tendencies will still be visible on the graphs, no need to plot all of them. If you want, you can, but for more than 500 datasets it will be very slow (slow means a few seconds for 500 datasets plotted on 3D graph, and several minutes for 3000 datasets on 3D graph, on my desktop computer).

### Simulation limits
This is used only for "Simulate" function, it will calculate a spectrum in this range of frequencies having a number of points defined here. Useful for testing and simulation.

### Advanced commands
These can be used for more advanced control of program. Most of the commands listed here are not available in the regular menu, see more details below (some commands are not likely to be used often so I didn't want to have too many entries in the Action menu). 

    save_config

will save a **yappari_configuration.xml** with the actual parameters (fit method, number of plots...) in **/config** folder. This file is read at the start of the program.

To make a Savitzky-Golay smooth of the active datasets :

    smooth
    
This will create new smoothed datasets with the same name and the prefix sm_.

To change the sign of Zi after reading a file that has -Zi (I always wondered why some softwares request -Zi in the datafile):

    negate_zi


You can also interpolate to log scale or upscale by spline interpolation (i.e. getting "artificially" more points). You can try it, if you don't have spurious points. The command:

    spline
    
will get 128 points interpolated from your data for the first command, in a log scale. 
You can specify the number of points by adding the number of points, for instance 99 (a parameter is passed with >>). 

    spline>>99
    
It might not be good to increase too much the number of points from he original ones, nor to use this function on noisy data. This command will create new datasets for every selected dataset, so you can play around to see how it is working. The log scale is important for DRT and Z-hit.

To add white noise to the selected impedance datasets in the range Z-1% to Z+1%   
    
    rndz>>1 

while
  
    rndzr>>0.5
    
will add white noise to the real part of the impedance in the range Z-0.5% to Z+0.5%
Other accepted parameters are _rndzi>>u_ for Zi white noise and _rndf>>u_ for frequency.

     average
     
will calculate the mean of Zr and Zi for the selected datasets. This function has a sense if it is applied to datasets measured at the same frequencies.

You can also search the best Tikhonov parameter for DRT calculations. The command :
 
    drt_search>>0.0002&0.1&256 
    
will calculate 256 [DRTs](https://github.com/nitad54448/yappari-5-1#drt-active-datasets) in the range 0.0002 and 0.1 and reconstruct all the 256 impedance sets. The best lambda parameter based on the minim squared error between the calculated and experimental sets will be shown. Obviously you can replace 0.0002, 0.1 and 256 with other values you want but you must separate them with _&_. No space should be in the command (you can use fractional or E string, for instance _search_lambda>>1E-6&2E-2&200_ is accepted). The interval of lambda will be scaned in log spacing over the interval specified with _start_value&stop_value&steps_

For a default range search (10E-4 to 10E-1) you can use the **Action** command then **DRT search** or 

    drt_search

If you want to see all DRT data and save them, you can use

    drt_explore

This will plot a 3D graph with all DRTs as a function of lambda, like this graph. Be patient, it takes time.
![plot](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/explore_lambda.png)

For drt_explore you can specify the defined values separated with & such as
    
    drt_explore>>0.0001&0.01&99

This command will calculate 99 DRT datasets in the interval 0.001 and 0.01. For Gold optimization you need to specify the number of iterations, for instance this command will calculate 80 datasets in the 500 to 5000 iterations interval:

    drt_search>>500&5000&80

## About
Brief help listing the version of the program, this is also the landing page of the program. 

## Read data
This command opens a menu with several options indicating the type of file to read. Reading a new file will just add more data at the beginning of the list wihtout losing the previous ones. You can remove some of the datasets with the command [Delete selected datasets](https://github.com/nitad54448/yappari-5-1#delete-active-datasets). You will need to select one or more datasets in order to perform operations like fit, save, plot.. etc. A selected dataset is coloured differently, it is named in this document as _active_. 
_Note : the files given as examples in the /files directory have a decimal separator . (a dot). When saving data there is a character separation between the numerical values (usually a TAB), this should be adjusted in Yappari, see the __Parameters__ page.

### 3 columns
This option reads a **single dataset** from a three-column ASCII file, which should be separated by the character selected in the [Parameters](https://github.com/nitad54448/yappari-5-1/blob/main/README.md#parameters) page, and it should contain frequency in Hz, Zr, and Zi. The data separator can be "TAB", "space", ",", ";".
The file may contain a description line (like parameters or type of the sample), if the description does not contain numbers which might be interpreted as data values by the program. The best option is to have only 3 columns and no text or empty lines in the file. If you want to keep one or more description lines in the file, it is better to use the "Custom" format and prepare an **XML template file**, see below. If you have multiple datasets in a single files they must be read with the **Custom** option.

If the reading is successful, the dataset will be inserted in the first position with a name taken from the filename. This name can be changed by the user. Only one dataset can be read with this command. 
_Note : You should select the proper separator string in the Parameters page prior to use of this function._

### MFLI, csv
This is a ';' or ',' separated values file as obtained from MFLI/MFIA, a Zurich Instruments impedance analyzer. As in the __MFLI, Zview text__, multiple data sets can be read from this file. In the /files folder that is provided with the installer you can find such a file containing 34 measurements of the same sample. It would be boring and useless to fit all these 34 datasets one by one. Yappari-5 can handle such multiple data sets. The dataseset are labeled with a name taken from the file name and a suffix indicating the position in the file : the first datasets in the file will have __0__, then __1__, .. and so on.
_Note : You should select the proper separator string in the Parameters page prior to of use this function._

### MFLI, Zview txt
This is a MFLI text file, an ASCII type, that can hold multiple data sets. Yappari will read all datasets it finds in this file and insert them in the datasets listing, with a name taken from the file name and a suffix indicating the position in the file : the first datasets will have __0__, then __1__,  and so on.

### Versa Studio par
This type of file contains data delimited by <Segments> and >/Segments>. I did not extensively checked this type of file, an example is given in the /data folder. If you encounter errors, feel free to drop me a line with examples of datafile saved by this system.

### Z-MFLI
This is a custom text file, that can hold multiple data sets, which is obtained by the programs I wrote in my lab. An exemple of such file is given in the /data directory but it has probably little interest for other users except that a Custom definition file is provided for this file, so the users may understand how to define such a file for reading custom formats.

### Custom
If your data file is of text type and has a format that is not usual you may define a _Custom_ format in an XML configuration file. In this case the program will ask the user to select two files : first the datafile then the XML file that describes the format used.
Several exemples of such files are given in the **/files** directory. A small program that saves this kind of file is also included (I think it is faster to use Notepad and edit one of the existing files).
The xml files can be viewed in a browser or edited by a standard text program (like Notapad). 

The XML parameters that are required for a definition file are 

**header**
	-a text separating datasets, required in order to separate the data blocks
**label_length**
        -a numeric value indicating how many characters after the header should be kept for naming a dataset, this value can be set to 0. If the label exists it must be located on the same line and after the header.
**data_separator**
        -the string that separates data fields (can be "tab", ",", ";" or " " space).
**ignore_first**
	-the number of lines to ignore before the start of the data (it can be 0)
**column_freq_Hz**
       -in which column the fequency is located
**column_Z_real**
       -in which column Z_real is located
**column_Z_imag**
	-in which column Z_imag is located
**ignore_last**
	-the number of lines to ignore after the end of the data (it can be 0)
  
For example, the Z-MFLI program saves a file like this:

    Temp /K before measurement : 449.810
    measure started : 26/07/2023  18:33:58
    T34B descente
    temp /K  : 0.000
    frequency /Hz, Real Z /Ohm, Im Z /Ohm 
    1.000000E+6	9.414706E+5	-2.383074E+5
    8.154407E+5	1.130474E+5	-6.121182E+4
    .....
    1.844263E-1	1.124571E+5	-5.840550E+2
    1.503887E-1	1.129925E+5	-7.342464E+2
    1.226330E-1	1.130371E+5	9.631194E+2
    1.000000E-1	1.137720E+5	9.809898E+0
    
    end of measure  : 26/07/2023  18:35:34
    Temp /K after measurement : 449.670 K
    ----------
    Temp /K before measurement : 449.660
    measure started : 26/07/2023  18:36:07
    T34B descente
    temp /K  : 0.000
    frequency /Hz, Real Z /Ohm, Im Z /Ohm 
    1.000000E+6	9.664908E+5	-2.747448E+5
    8.154407E+5	1.126409E+5	-6.080259E+4
    6.649436E+5	9.169096E+4	-5.206284E+4
    ....
    
In order to read this file we can observe that the datasets are separated by a string  __Temp /K before measurement :__  The label I use is the temperature shown in this line, just after the header. Next, there are 4 text lines that I can ignore. Four additional lines are at the end of the data which are separated by "tab". One can use an xml definition like this :

```xml
<Version>23.1f276</Version>
<Cluster>
	<Name>cluster</Name>
	<NumElts>8</NumElts>
	<String>
		<Name>header</Name>
		<Val>Temp /K before measurement : </Val>
	</String>
	<U8>
		<Name>label length</Name>
		<Val>6</Val>
	</U8>
	<EW>
		<Name>data_separator</Name>
		<Choice>space</Choice>
		<Choice>comma</Choice>
		<Choice>semicolon</Choice>
		<Choice>tab</Choice>
		<Val>3</Val>
	</EW>
	<U8>
		<Name>ignore first</Name>
		<Val>4</Val>
	</U8>
	<U8>
		<Name>column_freq</Name>
		<Val>1</Val>
	</U8>
	<U8>
		<Name>column_Zr</Name>
		<Val>2</Val>
	</U8>
	<U8>
		<Name>column_Zi</Name>
		<Val>3</Val>
	</U8>
	<U8>
		<Name>ignore last</Name>
		<Val>4</Val>
	</U8>
</Cluster>undefined</LVData>
```
This file can be created with the make-xml.exe program or just edited with a text editor. 
The command header will split the datafile (an example of this ZMFLI file is located in **/files/ZMFLI_datafile_example.dat**) in as many datasets it can find. The datasets are separated by the header read from the XML file (some repetitive text value). The program will find all the measurements (446 measurements for this case), then label each data set with the text following the header, ignore the following 4 lines then read the data found in the three columns separated by the delimiter specified in **data_separator**  (here, it is TAB, it is the index nr 3 of the list, the list start at index 0). After the data is read, an additional 4 lines are skipped.

Note that even if you don't use a label, i.e. label_length is 0, the dataset will have an index indicating the position of the data in the file : 0 is for the first dataset, 1 the second, and so on.

The custom file allows to read other columns from a data file. For instance, the file _example_custom_5_columns.dat_ was saved with yappari and contains 4 datasets with experimental and fitted data. It has a form like this :
 
    dev3221_imps_34, freq /Hz, Zr , Zi, Zr calc, Zi calc
    5.000000E+6;2.308040E+3;-4.358320E+3;2.656137E+3;-6.062695E+3
    4.304039E+6;2.506840E+3;-5.120760E+3;3.017911E+3;-6.767093E+3
    3.704951E+6;2.749520E+3;-5.969060E+3;3.432446E+3;-7.547331E+3
    3.189251E+6;3.044990E+3;-6.912400E+3;3.907999E+3;-8.409863E+3
    ...
    5.200320E-3;6.779950E+5;-1.059500E+6;6.713365E+5;-1.051917E+6
    4.476419E-3;7.530980E+5;-1.175940E+6;7.440566E+5;-1.164143E+6
    dev3221_imps_33, freq /Hz, Zr , Zi, Zr calc, Zi calc
    5.000000E+6;2.302790E+3;-4.372530E+3;2.825870E+3;-6.215076E+3
    4.304039E+6;2.499580E+3;-5.137940E+3;3.203636E+3;-6.927116E+3
    3.704951E+6;2.739930E+3;-5.990360E+3;3.635279E+3;-7.714612E+3
    3.189251E+6;3.033540E+3;-6.938630E+3;4.129017E+3;-8.583845E+3
   ...
   
If we want to read the calculated impedances, located in the columns 4 and 5 with a definition file (given in _example_custom_5_columns_template.xml_) the definition will look like this: 

```xml                
<LVData
	xmlns="http://www.ni.com/LVData">
	<Version>23.1f276</Version>
	<Cluster>
		<Name>cluster</Name>
		<NumElts>8</NumElts>
		<String>
			<Name>header</Name>
			<Val>dev3221_imps_</Val>
		</String>
		<U8>
			<Name>label length</Name>
			<Val>2</Val>
		</U8>
		<EW>
			<Name>data_separator</Name>
			<Choice>space</Choice>
			<Choice>comma</Choice>
			<Choice>semicolon</Choice>
			<Choice>tab</Choice>
			<Val>2</Val>
		</EW>
		<U8>
			<Name>ignore first</Name>
			<Val>0</Val>
		</U8>
		<U8>
			<Name>column_freq</Name>
			<Val>1</Val>
		</U8>
		<U8>
			<Name>column_Zr</Name>
			<Val>4</Val>
		</U8>
		<U8>
			<Name>column_Zi</Name>
			<Val>5</Val>
		</U8>
		<U8>
			<Name>ignore last</Name>
			<Val>0</Val>
		</U8>
	</Cluster>
</LVData>
```

This instructs the program to read the fourth column as Zr and the fifth as Zi. Make sure you have the separator set as ";" which is the one used in this file, it is index 2 in the data_separator list.

In the **/files** folder and in **/drt** you will find some other files, experimental or simulated with other impedance programs and exemples of configurations for XML templates (or definition files).
Be aware that the separator character is defined in the definition file only if you use a Custom file, otherwise the separator is defined in the **Parameters** page. 

### Read project, xml
This command will read an xml file saved with Yappari. It can read all data, models and parameters obtained. This is an xml file so it can be seen in a browser, but reading it is slow, it requires parsing all ASCII fields.

## Action
This button can trigger several commands, some others are in [Advanced commands](https://github.com/nitad54448/yappari-5-1#advanced-commands) :

### Delete points from graph
You can delete experimental points from selected datasets in the Nyquist, Zr, Zi or lnR plots: just zoom in the region to show only the points you want to delete then select this command (this is irreversible). Be aware that the points having values in the range shown on the plots are removed from _all selected datasets_ irrespective if they are actually seen on the plots or not. The datasets visible on the graph depends on the [Max plots](https://github.com/nitad54448/yappari-5-1#max-plots) value.

### Delete active datasets
Irreversible action removing one or more datasets and all related parameters from memory (by active one should understand “selected”). Datasets can be deleted also with the Key "Delete".

### Apply correction to active
Apply a correction factor to the experimental Zr and Zi for all selected datasets.  The impedance values will be multiplied with the factor you input here.  Be careful: this may change the units. For ionic conductivity multiply with S/L will give resistivity (in Ohm cm or Ohm m) instead of Ohm. For reactions at electrode surface you need to multiply with the electrode surface to get Ohm cm^2 or Ohm m^2. The calculated impedance will not be affected by this command.

### Simulate spectrum
This option will calculate an impedance spectrum based on the model and the values of the parameters of the model, in the frequency range that are on Parameters page. It will create a new dataset (called "sim_" but you can change its name). 

### Z-Hit active datasets
This option will provide a Z-HIT simulation (which is a Hilbert transform of the phase into the real part of the impedance) for one or more datasets. The procedure, when and why to use it, is described [here](https://en.wikipedia.org/wiki/Z-HIT). In this implementation I am using the corrections including the 5th derivative of the phase as described in the link given previously. This is a procedure similar to the better known Kramers-Kronig test.

### DRT active datasets
This performs a calculation of Distribution of Relaxation Times for one or more datasets for the case of serial RC circuits. The methods used and theory is detailed [here](https://github.com/nitad54448/yappari-5-1/blob/main/docs/theory.md).  
 
Data should be acquired with log spacing and with a decent number of points per decade (otherwise you may try to rearrange data with the command _spline>>number_ if you want a total _number_ interpolated datapoints scaled in log space).
For the fit, the optimal regularization parameter is decided by the user (there is no universal value for this, it can be estimated with a procedure known as L-curve). If the Tikhonov parameter, noted Lambda in this program, is too small some spurious peaks will appear while a parameter too large will just squash the information. 

Criteria for selecting the optimal value are included in this program. You can either use [DRT search](https://github.com/nitad54448/yappari-5-1/blob/main/README.md#drt-search) command or see other options in _Advanced commands_. 
The function _drt_explore_ allows you to see and save all data.
The procedure I use here is to provide an indication of the frequencies of the relaxations. More advanced free DRT programs are available, see for instance [Ciucci et al](https://github.com/ciuccislab/DP-DRT) and his papers and there are some others. The DRT procedure may help in detecting a proper electrical circuit for serial RC circuits and to some extent to serial RQ cirrcuits. If you want to use it, I suggest to read first some publications describing the procedure and the limitations.
There is no need for a circuit model for the DRT calculations. The usefulness of DRT depends much on the quality of the data and in particular the first and the last points of the data.
Three different algorithm are now used : Tikhonov regularization (the default one used today), an iterative variant of Tikhonov proposed by Fisk and the Gold decomposition. The latter seems more useful for RQ circuits but the number of iterations is large and it is up to the user to select this.
On the DRT graph, the experimental Zr and Zi are plotted together with the _recalculated impedances_ from the DRT data and a probability of distribution function. Calculations are made in real time if you change the Tikhonov parameter, so if you have multiple datasets and many iterations, it may be slow. Some files to test are in the /drt folder.
An example of a DRT fit is shown below :

![plot](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/drt_calc_RCRC_1k_3_5microF_80_20p_simulated.PNG)
Red dots are experimental Zr and the red line is calculated Zr based on the distribution function as RC (blue dots and line are experimental and calculated Zi values). The green spikes are calculated relaxation times. The fit is very good and corresponds well with the simulated values calculated only from the "experimental" imaginary impedance. 
Only the first selected dataset will be shown on the DRT graph, if the DRT calculation was performed for that dataset.

If you hold the mouse on the graph a Tip with an estimation of RC values will be shown (or you can right click on the graph and look for Description and Tips). These parameters are calculated based on the Rpol and the surface of the peaks and can be used as starting points for fitting a model. 

### DRT search
This command performs a search of optimal regularization parameter for the first active (aka selected) dataset.
A window with an indication of the optimal parameter will appear. The plot shows the mean squared error (MSE) between the experimental Zr and Zr calculated from DRT data as well as the variance (this is based on the method proposed [here](https://chemistry-europe.onlinelibrary.wiley.com/doi/full/10.1002/celc.201901863)).
It should look like this
![plot](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/params_drt_alten.PNG)

The optimal regularization parameter is the minimum of the MSE (or just at the change of the variance). You can zoom this image to check the selection made. The program proposes the optimum as the value of lambda where there is a minimum in MSE and show a red cursor position. You can drag this cusor to another position to impose another value for lambda. By default for Gold the program will calculate 50 points and for Tikhonov and Fisk 100 points. You can modify these values, see Advanced commands.
Similar to this function there is drt_explore which can be accesed in [Advanced commands](https://github.com/nitad54448/yappari-5-1#advanced-commands).

### Clone the parameters to all
Copy the listed parameters to all datasets. Useful for bulk fitting in order to set proper starting point for all the sets.

### Clone the parameters to active
Copy the listed parameters to selected datasets. Note that the listed parameters are those of the first selected dataset.

### Report active datasets
This command generates an HTML report containing information about the model used, the parameters used, the fitted parameters, and their standard deviation (if an LM fit was done, otherwise esd will appear as 0). It also includes images of the fit. The report is saved in your temporary directory and automatically opened in a browser. Beware that for each datasets you'll get 5 images and text with the obtained results, therefore if you fit 3700 datasets may get a 10000 pages pdf file. A warning is issued if the report will be too large.

### Save active parameters
Saves a file with the parameters for all selected datasets. Useful for multiple datasets, for a small number of datasets you may use also __Report__. Note that if the dataset was not fitted the parameter line corresponding to that dataset will be empty.

### Save data
This option saves the active datasets, as selected by the user, to a single file with data separated by the character you have on the Parameters page, in multiple columns format. All active datasets will be saved in a single file, each dataset subsequently added, with its name, to the same file.

### Save project, xml
Save all data, model and parameters, including calculated and DRT data, if any, into an xml file. This file can be read in Yappari, starting with release 5.1.71. 

### Help
This will open this website, hopefully the address will not change; while the program file may have some tutorial help files, the most recent help is always on this github page.

## Datasets
This list box shows all the datasets in memory. You can select one or more datasets and you can use common Windows shortcut like Ctrl+A, Delete.... The parameters listed are those of the dataset selected (or the first selected dataset if you have more than one selection). The datasets label can be edited.

## Fit selected
This command is used to fit the set of parameters that describes the circuit, if the circuit is valid (i.e., there are parameters to fit on the right side of the window) and if you have data. The user can select which parameters to fit and it is recommended to start with a few parameters first, ensuring that the initial values are close to the expected values. The simulated spectrum will be updated with every change in the parameters, and the user can perform manual adjustments as necessary. The data can be selected by standard click, ctrl+click,.. or if you want you can select all by using Ctrl+A.
For many datasets, the data are described by the same model circuit, I suggest to select one measurement, adjust the parameters manually to be close to solution, then fit. You may want to take a look at this [tutorial](https://github.com/nitad54448/yappari-5-1/blob/main/help/fit_multiple.pdf). After fit you can “Clone” these parameters to all other datasets and select all datasets, then _Fit all selected_ in a go.

The fitting can be performed using different methods, which are discussed before, although there is not much difference in the output of these methods (except for the esd, see below). The fitting process involves a number of cycles, by default 1000 for a dataset, and it will stop a limit is reached. These termination parameters can be adjusted on the _Parameters_ page or in configuration file. Multiple iterations may be necessary, particularly if the initial values are far from the actual values.

The quality of the fit is evaluated using the R<sup>2</sup> statistical parameter and the chi<sup>2</sup> value. However, the use of the chi<sup>2</sup> value as a statistical parameter is debatable, as discussed in the paper ["Dos and don'ts of reduced chi-squared"](https://github.com/nitad54448/yappari-5-1/blob/main/theory.md) by Andrae et al. The chi<sup>2</sup> value reported here is calculated as (Sum ((Z<sub>obs</sub>-Z<sub>calc</sub>)<sup>2</sup>/Z<sub>calc</sub>))/DOF. The degree of freedom (DOF) is considered as Nr_of_points - nr_of_fitted_params. 
The standard deviation is estimated, assumming independent errors, only for unconstrained Levenberg-Marquardt fit.

[# やっぱり #](https://github.com/nitad54448/yappari-5-1)
--
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>


