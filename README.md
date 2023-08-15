# やっぱり #

__YAPPARI__ stands for Yet Another Program for Analysis and Research in Impedance, it can be referenced in publications as http://dx.doi.org/10.13140/RG.2.2.15160.83200

This program can perform fits for one or multiple datasets (by multiple I mean hunderths or even thousands datasets, this may be slow but you'll get all the results in a run, the results can be saved in a datafile). For a single dataset you may want to use a simpler program called [Yappari 4.2](https://github.com/nitad54448/win10-installer-yappari-4.2), available also as a Windows 10 installer. This single dataset program will not be developed further so it might be better to take a leap and move to version 5.

You are encouraged to contribute to this help file, either you can send it to me or fork it on Github. As much as I like programming, writing documentation is boring. A short tutorial is included in the help pdf file which is installed with the exe file. Otherwise, the most updated description of the program is always here on this page.
It is generally a good idea to read a help file before using a program.

__Note__ : if you want I can setup an automatic email reminder when there is an update, if this is the case leave a note (just be warned that I am fidgeting a lot with it these days, so you can get 10 mails per day).

__Second note__ : there is no warrantee whatsoever for using this program. Use it if you want : you will not receive much help from me, everything is in this documentation file. If youd don't want : don't use it. There are many other programs, some commercial and some free.. and likely some are better than this one. 

# yappari-v5-2023 #
version 14-08-2023

  * [How to install](#how-to-install)
  * [Panels](#panels)
    + [Zr, -Zi](#zr--zi)
    + [Zr, Zi, ln R, theta](#zr-zi-ln-r-theta)
    + [3D plot](#3d-plot)
    + [Model](#model)
      - [Elements](#elements)
      - [Create a model](#create-a-model)
    + [Parameters](#parameters)
    + [About](#about)
  * [Commands](#commands)
    + [Read data](#read-data)
      - [3 columns](#3-columns)
      - [MFLI csv](#mfli-csv)
      - [Versa Studio par](#versa-studio-par)
      - [Zview txt](#zview-txt)
      - [HDF5-MFLI](#hdf5-mfli)
      - [Z-MFLI](#z-mfli)
      - [Custom](#custom)
    + [Action](#action)
      - [Delete points from graph](#delete-points-from-graph)
      - [Erase active datasets](#erase-active-datasets)
      - [Clone the parameters to all](#clone-the-parameters-to-all)
      - [Clone the parameters to active](#clone-the-parameters-to-active)
      - [Save active exp datasets](#save-active-exp-datasets)
      - [Save active calc datasets](#save-active-calc-datasets)
      - [Save active exp and calc datasets](#save-active-exp-and-calc-datasets)
      - [Report active](#report-active)
      - [Z-Hit active datasets](#z-hit-active-datasets)
      - [DRT active datasets](#drt-active-datasets)
      - [Help](#help)
    + [Datasets](#datasets)
    + [Fit selected](#fit-selected)
    + [Exit](#exit)
    + [Author](#author)
    + [Changes](#changes)



## How to install ##
Yappari 5.1 is compiled with Labview 2023 for Windows 10.
It is supposed to work with win7 64bits, Win8 or Win8.1, as well as windows 11, but I am unable to test it on these systems.
This application requires Labview 2023 runtime engine or a subsequent LV 64 bits runtime engine. You may have this "engine" if you have previously installed Yappari or other program written in LV2023 or you can download it freely from ni.com. 
The recommended way to install is to use the full package which can be downloaded from [Releases](https://github.com/nitad54448/yappari-5-1/releases). Make sure you download the yappari_installer.zip file and not what is labelled as source file archive. The source is not included in this distribution. 

After installing the program in a directory of your choice, two other directories will be created : /Data and /models. The _models_ directory contains png files with images for creating circuit. The _data_ directory contains exemples of data files and some dll required by the program (if you remove these files the program will still work except for reading the HDF5 files.

## Panels ##
The program has several graphic [panels](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/panels.PNG) and a parameter list with several commands grouped on the right side of the window.

### Zr, -Zi ###
This panel shows a Nyquist plot, which is a standard way to visualize impedance data. The scale on the graph will adjust automatically based on the data, with the same axis range for the imaginary part and real part. However, if you want to manually set a specific range, you can disable the Auto-axis feature by right clicking on the graph, or directly changing the scale in the legend. Some other standard graph functions are available in the top left "palette" such as zoom in, out... etc. All graphic panels will plot experimental and simulated data (if any) of selected datasets.
You can change the plot colors, style, etc.... by clicking on the label; the changes in this graph will affect all the graphs. You can remove some outlier points by zooming in and use the command _Action_/_Delete points from Nyquist_.
If you use a large number of datasets (more than 200 sets), plotting can give some errors, they are inoffensive and can be ignored.

### Zr, Zi, ln R, theta ###
These panels will show the dependency of impedances (real, imaginary, modulus or phase) as a function of frequency and the differences between the calculated and experimental values ([if any](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/fit_graph.PNG)).

### 3D plot ###
This panel will show a 3D plot of selected datasets, either in Nyquist, Zr or Zi or their difference, as selected by the user. This is useful for many datasets, more than 20 I guess, it will allow the user to see tendencies or check systematic errors in the fits. You can right click on the graph to adjust plotting properties to your liking (3D Plot Properties) or change the size of the graph.

### Model ###
In this panel a model can be created by the user, by selecting element circuits. 
Up to ten elements can be added in the circuit (obviously it is not realistic to fit such a circuit, unless you want to fit a crocodile). Only the first 18 parameters will be shown in the right side of the program.
When you click on one of the ten available cases, a new window will appear where you can select the element you want to add. Simply click on the picture of the element you want to add to the model. The available circuit elements include resistors, capacitors, inductors, and more complex elements such as constant phase elements or Warburg elements (see below).

You can edit the png image files to your liking (just for aesthetics, the calculations will not be affected), they are in the subdirectory __/models__. The ideal size of the png files is 150x100 pixels.

#### Elements ####
The [elements](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/circuit.PNG) used are the most common: Resistor, Capacitor, Inductor, CPE, Zarc, simple Randles circuit, Randles with kinetic and diffusion, Warburg (semi-infinite linear diffusion), Warburg short, Warburg Long, Gerischer, Havriliak-Negami and several compositions of these.

Warburg element represents semi-infinite diffusion to or from a flat electrode, expressed here as:

Z(ω)= A<sub>w</sub>/($\sqrt{ω})$ -jA<sub>w</sub>/($\sqrt{ω})$

This element contributes equally to Zr and Zi so it appears as a straight line in a Nyquist plot, at 45 degrees or a straight line in Bode plot (log |Z| vs. log ω) with a slope of value –1/2. The A<sub>w</sub> term is expressed in Ohm sec<Sup>-1/2</sup> and is called Warburg coefficient. It is expressed as

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

#### Create a model ####

When you create a model using the  editor, the circuit is not valid unless a flow of current can be calculated (but not a short-circuit). Once the circuit is valid, a LED labeled "[valid](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/model_circuit.PNG)" will light up on the model panel, indicating that the circuit is ready for use and you can see a list of all the parameters for each element of the circuit. 
_Note : the parameters will be listed only if you have loaded experimental data!_ If you forgot to load data and already built a model, you can read data then modify the model to check for its validity (for instance, replace one element with the same one, this will trigger a validity check in the program). However, in doing so, the paramaters of the model will be initialized to some dummy values. To see the experimental data and the simulaion you need to select one or several datasets.

Calculations of impedances are made whenever the parameter values are changed... _if the model is valid_ and if you have some data loaded. You can use the wheel of the mouse to evaluate the change in the output impedance with the change in the value of a parameter.

Each [parameter](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/param_values.PNG), listed on the right side of the page, is labeled with a decimal, which indicates which element it belongs to. For example, the first element of the circuit will have parameters labeled as 0.x, the second element as 1.x, and so on. When you add a parallel RQ element to the first element of the circuit (a Zarc as element 0), you need to create "electrical contacts" in the next three elements (elements 1, 2, and 3, or 4,5 and 6, or 7, 8 and 9….) for the circuit to be complete. 
Otherwise, the circuit will be open and no impedance can be calculated. In other words all the elements of the circuit need to be properly connected for the circuit to be valid and for impedance calculations to be performed.

Let’s make a valid circuit, with a Zarc and three shorts. As the circuit is valid, with a Zarc in element 0 position, three parameters will appear in the tab of the right side of the panel: 0ZARR, 0ZARQ and 0ZARN; the names are rather self-explaining for the parameters describing a Zarc located in the position 0 of the circuit, with the three parameters describing a parallel RQ. You can use a RQ element and fix the N to 1 to obtain the equivalent RC circuit. The equivalent capacitance for a RQ circuit is C=((RQ)<sup>1/n</sup>)/R.

For a more complex circuit, you can find on the right side of the screen names such as 2MR1D, 2MQ2D, 2MN2D, 2MR3D, 2MR4D, 2MR5D, and 2MW6D. The first number, "2", indicates which element case the device is in. The letters "M" and "D" are internal notations that are used by the program to identify the device type, but they are not important for the user. The type of device is listed after the "M" notation, such as "R" for resistor or "W" for Warburg. 

The numbering of the devices goes from left to right and top to bottom. For example, the first device is a resistor and can be described by the parameter "2MR1D". The second device in the circuit is a Zarc, which is a combination of a constant phase element (CPE, or Q) in parallel with a resistor. This device is described by the parameters "Q2" and "N2". 

Overall, the notation is quite straightforward once you become familiar with the conventions used.

### Parameters ###
On this page you can adjust some parameters of the program. In particular the datafile separator _should_ be selected here. When reading a MFLI csv file you have probably a _,_ or _;_ separator. You need to inspect the data file then select the proper string here. For 3 columns, _tabs_ are typically used. Note that the separator used here for reading will also be used for exporting the data files. By default the separator is set to TAB.

The fitting algorithm (TRDL is the default) and the parameters bounds, if any, can be constrained to certain intervals that are listed on this page. Initial [limits](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/parameters.PNG) are rather large, for example, resistors are limited to the range of 1 mOhm to 1 GOhm, capacitors are between 10^-4 and 10^-14, and so on. You may need to adjust the parameters limits. The fitting results may depend on the starting parameters. You should probably start with TRDL to approach some values close to the solution then proceed with a LM fit. Note that esd of the fitted parameters are correct only for u constrained LM fit.

The fit termination parameters can be adjusted here : by default they are set to 500 iterations and a stop limit at 10E-8.

__Developer commands__
Can be used for manual control of program, useful mostly for testing. Some commands are not available elsewhere, some examples :
_smooth_active_ will make a Savitzky smooth the active datasets
_rndz>>1_ will add white noise to the selected impedance datasets in the range Z-1% to Z+1%
_rndzr_>>0.5_ will add white noise to the real part of the impedance in the range Z-0.5% to Z+0.5%
Other accepted parameters are _rndzi>>u_ for Zi white noise and _rndf>>u_ for frequency.
_average_ will calculate the mean of Zr and Zi for the selected datasets. This function has a sense if it is applied to datasets measured at the same frequencies.
You can also search the best Tikhonov parameter, the command :
_search_lambda>>0.0002&0.1_ 
will calculate 1024 DRTs in the range 0.0002 and 0.1 and reconstruct all the 1024 Z sets, then select best lambda parameter based on the minim squared error between the calculated and experimental sets. Obviously you can replace 0.0002 and 0.1 with other values you want but you must separate them with _&_. No space should be in the command (you can use fractional or E string, for instance _search_lambda>>1E-6&2E-2_ is accepted). 1024 values is a fixed value, the interval of lambda will be scaled in log spacing over the interval specified with _start_value&stop_value
Another command you may try is
_calculate_drt_fisk
if you want to test another non-negative Least-squares (NNLS) procedure. It is based on the algorithm proposed by [Fisk](https://arxiv.org/abs/1307.7345) and implemented in versions of Yappari prior to 14th of aug 2023. 

### About ###
Brief help listing the version of the program. 

## Commands ##
### Read data ###
This command opens a menu with several options as of now, designing which type of file to read. Note that reading a new file will just add more data wihtout losing the previous ones. You can remove some of the datasets with the command __Erase selected datasets__. You will need to select one or more datasets in order to plot them. 

#### 3 columns ####
This option reads a three-column ASCII file, which should be separated by the character selected in the Parameters page, and it should contain frequency in Hz, Zr, and Zi. Is important to note that for French users (and some others), the separator value for a number should be a dot “.” and not a comma “,” (you may need to adjust this in the Windws parameters). I did not check if the program works when a number is represented as 1,256 instead of usual 1.256, but obviously one can not use ',' for separating both the digits in a number representation and separating values in a text file. 
If the reading is successful, the dataset will be inserted in the first position with a name taken from the filename open. This name can be changed by the user. Only one dataset can be read with this command. 
The first line of these files can be a text (the program will try to detect and discard a comment in the first line; if it fails, just remove all comments from the file and try again), or use the Custom format.

#### MFLI csv ####
This is a ';' or ',' separated values file as obtained from MFLI/MFIA, a Zurich Instruments impedance analyzer. As in the Zview text file, multiple data sets can be saved or read from this file. In the data folder that is provided with this installer you can find such a file containing 34 measurements of the same sample. It would be boring and useless to fit all these 34 datasets one by one. Yappari-5 can handle such multiple data sets. You should select the proper separator string in the Parameters page.

#### Versa Studio par ####
This type of file contains data delimited by <Segments> and >/Segments>. I did not extenisively checked this type of file as I don't have access to this type of instrument, an example is given in the /data folder. If you encounter errors, feel free to drop me a line.

#### Zview txt ####
This is a Zview file, also an ASCII type, that can hold multiple data sets. Yappari will read all datasets it finds in this file and insert them in the datasets listing, with a name taken from the file name and a suffix indicating the position in the file : the first datasets will have __0__, then __1__, .. and so on.

#### HDF5-MFLI ####
This is a HDF5 file, a binary file, that can hold multiple data sets. The datafile must be saved by MFIA or MFLI with impedance options. It must hold an _imps_ group. An exemple of such file is given in the /data directory, it has a _h5_ extension. An error will appear if the file does not hold _imps_ groups.

#### Z-MFLI ####
This is a text file, that can hold multiple data sets, which is obtained by programs I wrote in my lab. An exemple of such file is given in the /data directory but it has probably little interest for other users.

#### Custom ####
If your data file has a format that is not usual you may define the format in a configuration file. Several exemples of such files are given in the /data directory. The accepted keywords are :

     [header]=
     [label_length]=
     #label
     #ignore_line
     #data_columns=


For example, the Z-MFLI program saves a file like this:

    Temp /K before measurement : 449.810
    measure started : 26/07/2023  18:33:58
    T34B descente
    temp /K  : 0.000
    frequency /Hz, Real Z /Ohm, Im Z /Ohm 
    1.000000E+6	9.414706E+5	-2.383074E+5
    8.154407E+5	1.130474E+5	-6.121182E+4
    6.649436E+5	9.185450E+4	-5.269764E+4
    5.422221E+5	9.023882E+4	-4.824161E+4
    4.421500E+5	9.325740E+4	-4.422129E+4
    3.605471E+5	9.751274E+4	-3.975290E+4
    
    ----------
    Temp /K before measurement : 449.660
    measure started : 26/07/2023  18:36:07
    T34B descente
    temp /K  : 0.000
    frequency /Hz, Real Z /Ohm, Im Z /Ohm 
    1.000000E+6	9.664908E+5	-2.747448E+5
    8.154407E+5	1.126409E+5	-6.080259E+4
    6.649436E+5	9.169096E+4	-5.206284E+4
    5.422221E+5	9.002227E+4	-4.803786E+4
    4.421500E+5	9.300340E+4	-4.387796E+4
    3.605471E+5	9.711612E+4	-3.944369E+4
    2.940048E+5	1.011267E+5	-3.451051E+4
    
In order to read this file we can observe that the datasets are separated by a string  __Temp /K before measurement :__  One can use a definition like this :

    [header]=Temp /K before measurement : 
    [label_length]=5
    #label
    #ignore_line
    #ignore_line
    #ignore_line
    #ignore_line
    #data_columns=1,2,3

The command header will split the datafile (an exemple is /data/custom_file_ZMFLI.txt) in as many datasets it can find in the file, to each data set it will add a label consisting of the first 5 characters found after the header text which in this case is the temperature of the measurement.  The program will find all the measurements (446 for this case !), then label each data set with the text following the header (which is, in this case, the temperature), ignore the following 4 lines then read the data found in the three columns separated by the delimiter specified by the user in the Parameters case (here, it should be TAB). Yappari can fit in batch all these 446 measurements and save the results to a file.

Note that even if you don't use a label, the dataset will have an index indicating the position of the data in the file : 0 is for the first dataset, 1 the second, and so on.
An exemple of configuration file for a three columns separated by tab is also given in the /data directory. 
The custom file allows to read other columns from the data file. 

For instance, the file _exemple_custom_5_columns.txt_ was saved with yappari and contains 4 data sets with experimental and fitted data. It has a form like this :
 
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
   
If we want to read this data we can use a a definition file like

    [header]=dev3221_imps_ 
    [label_length]=2
    #label
    #data_columns=1,4,5

This instructs the program to read the fourth columns as Zr and the fifth as Zi (which are the calculated values saved in this file). Make sure you have the separator set as ";" which is the one used in this file.

In the /data folder you will find some files, experimental or simulated with other impedance programs and exemples of configurations for custom files.
  * definition_file_3_columns.ini
  * definition_file_5_columns.ini
  * definition_file_ZMFLI.ini
  * dev3221_imps_0_sample_0000.csv is a measurement of a sample (including more than 20 datasets) as obtained with a MFLI/MFIA from Zurich Instruments; separator for this file is ';'
  * exemple_custom_3_columns_datafile.txt, to be used with the custom read function
  * exemple_custom_5_columns_datafile.txt, to be used with the custom read function
  * exemple_custom_file_ZMFLI_datafile.txt, to be used with the custom read function or with Read ZMFLI and practice batch fitting for more than 400 measurements
  * mod_dev3221_imps_0_sample_0000 is a Zview txt file, as obtained with MFLI instrument (one dataset)
  * R(CR)(CR)W.txt is a simulated dataset with a Warburg element in a three columns separated by tabs
  * R(CR)O.txt is a simulated dataset with a Warburg "short" element (three columns separated by tabs)
  * R(CR)T.txt is a simulated dataset with a Warburg "open" element (three columns separated by tabs)
  * type_VersaStudio.par
  * ZMFLI_exemple_file_.txt


### Action ###
This button can trigger several commands:

#### Delete points from graph ####
You can delete experimental points from datasets visible in the Nyquist, Zr, Zi or lnR plots: just zoom in the region to show only the points you want to delete then select this action command. This is irreversible and it applies to the shown graph. Calculated points angle will not be erased (this action is not performed to differences plots nor to phase angle).

#### Clone the parameters to all ####
Copy the listed parameters to all datasets. Useful for bulk fitting in order to set proper starting point for all the sets.

#### Clone the parameters to active ####
Copy the listed parameters to selected datasets. 

#### Save active exp datasets ####
This command allows you to save the *active* experimental data, that means the selected ones, to a single file in a specific format. The format is three columns, separated by the string you selected in the Parameters page, with frequency in Hz, Zr, and Zi. This is useful for simulating impedance spectra for a given model. All the datasets will be saved in a single file, each data susequenntly added, with its name, to the same file.

#### Save active calc datasets ####
This command allows you to save the *active* calculated data to a file in a three columns format, separated by the string you selected in the Parameters page.

#### Save active exp and calc datasets ####
This command allows you to save the *active* experimental data and calculated data, in a 5 columns ASCII file. Note that all datasets are saved in a single file, each dataset will be separated by the label of the set. This might be used to plot nicer graphs.

#### Erase active datasets ####
Irreversible action removing one or more datasets and all related parameters from memory (by active one should understand “selected”)

#### Report active ####
This command generates an HTML report containing information about the model used, the parameters used, the fitted parameters, and their standard deviation. It also includes images of the fit as well as all experimental and calculated data. The report is saved in your temporary directory and automatically opened in a browser. You can use the data in the report to create your own graphs or to check for any discrepancies. If you find any errors in the calculations, please report them so they can be corrected.

#### Z-Hit active datasets ####
This option will provide a Z-HIT simulation (which is a Hilbert transform of the phase into the real part of the impedance) for one or more datasets. The procedure, when and why to use it, is described [here](https://en.wikipedia.org/wiki/Z-HIT). In this implementation I am using the corrections including the 5th derivative of the phase as described in the link given previously. This is a procedure similar to the better known Kramers-Kronig test.

#### DRT active datasets ####
This performs a calculation of Distribution of Relaxation Times for one or more datasets. The method used is constrained non-negative linear regression with a Tikhonov parameter. The procedure used was implemented by [Christian Altenbach](https://sites.google.com/site/altenbach/Home) for EPR spectrocopy. This [method](https://sites.google.com/site/altenbach/labview-programs/epr-programs/long-distances/ld-algorithms) is very fast and therefore it is possible to search an optimal regularization parameter, see below and the description of [Parameters](https://github.com/nitad54448/yappari-5-1/blob/main/README.md#parameters) page.

Only the values of imaginary part of the impedance are taken into calculations. Data should be acquired with log spacing.
For the fit, the optimal regularization parameter is decided by the user (there is no universal value for this, it can be estimated with a procedure known as L-curve). If the Tikhonov parameter, noted Lambda in this program, is too small some spurious peaks will appear while a parameter too large will just squash the information. 
The procedure I use here is to provide an indication of the frequencies of the relaxations. Much more advanced free DRT programs are available, see for instance [Ciucci et al](https://github.com/ciuccislab/DP-DRT) and his papers but there are many others. The DRT procedure may help in detecting a proper electrical circuit. If you want to used it, I suggest to read first some publications describing the procedure and the limitations.
There is no need for a circuit model for the DRT calculations. The usefulness of DRT depends much on the quality of the data and in particular the first and the last points of the data.
On the DRT graph, the experimental Zr and Zi are plotted together with the _recalculated impedances_ from the DRT data and a probability of distribution function. Calculations are made in real time if you change the Tikhonov parameter, so if you have multiple datasets and many iterations, it may be slow. Some files to test are in the /drt folder.
An example of a DRT fit is shown below :

![plot](https://github.com/nitad54448/yappari-5-1/blob/main/help/images/drt_calc_RCRC_1k_3_5microF_80_20p_simulated.PNG)
Red dots are experimental Zr and the red line is calculated Zr based on the distribution function as RC (blue dots and line are experimental and calculated Zi values). The green spikes are calculated relaxation times. The fit is very good and corresponds well with the simulated values. Note that full impedance is calculated only from the "experimental" imaginary impedance, this should be correct for experimental spectra that respect the KK relation. This might not be the case if the data is noisy or inadequate. 

#### Help ####
This will open a this website, hopefully the address will not change; while the program file may have some pdf help files, the most recent help is always on this github page.

### Datasets ###
This list box shows all the datasets in memory. You can select one or more datasets. The parameters listed are those of the dataset selected (or the first selected dataset if you have more than one selection). The datasets label can be edited.

### Fit selected ###
This command is used to fit the set of parameters that describes the circuit, if the circuit is valid (i.e., there are parameters to fit on the right side of the window). The user can select which parameters to fit and it is recommended to start with a few parameters first, ensuring that the initial values are close to the expected values. The simulated spectrum will be updated with every change in the parameters, and the user can perform manual adjustments as necessary. The data can be selected by standard Ctrl+Click, or if you want you can select all by using Ctrl+A.
For many datasets, the data are described by the same model circuit, I suggest to select one measurement, adjust the parameters manually to be close to solution, then fit. After fit you can “Clone” these parameters to all other datasets and select all datasets, then Fit all selected in a go.

The fitting can be performed using different methods, which are discussed before, although there is not much difference in the output of these methods (except for the esd, see below). The fitting process involves a number of cycles, by default 5000 for a dataset, and it will stop a limit is reached. These termination parameters can be adjusted on the _Parameters_ page. Multiple iterations may be necessary, particularly if the initial values are far from the actual values.

The quality of the fit is evaluated using the R<sup>2</sup> statistical parameter and the chi<sup>2</sup> value. However, the use of the chi<sup>2</sup> value as a statistical parameter is debatable, as discussed in the paper "Dos and don'ts of reduced chi-squared" by Andrae et al. (https://arxiv.org/abs/1012.3754). The chi<sup>2</sup> value reported here is calculated as (Sum ((Z<sub>obs</sub>-Z<sub>calc</sub>)<sup>2</sup>/Z<sub>calc</sub>))/DOF. The degree of freedom (DOF) is considered as Nr_of_points - nr_of_fitted_params. 
The standard deviation is properly estimated (assumming independent errors) only for unconstrained Levenberg-Marquardt fit.

### Exit ###
No need for explications on what this command does.

### Author ###
This program can be used freely and distributed according to CC-BY-NC-SA.
It was written in Labview 2023, National Instruments and it includes the JKI toolkits for Labview, © 2023, JKI. All rights reserved.

For questions or comments:

__Nita DRAGOE__, Université Paris-Saclay, ICMMO/SP2M, 91400 Orsay, France
  
### Changes ###
  -  August 15, 2023 : I limited the DRT gaph to the first active dataset, otherwise it akes too much time to show the DRT graphs. 
  -  August 14, 2023 : The method of NNLS for DRT was changed to that of Altenbach.
  -  August 12, 2023 : Implemented a full DRT calculation for ore or more datasets (with a Tikhonov-type constrained non-negative parameters least-squares procedure, see the documentation for reference to the method used). Added the possibility to change the X-scale in DRT graph (sometimes is convenient to check the time constants). Added a debug/developper command to test things.
  -  August 10, 2023 : Cosmetics; DRT graph changed as a function of 1/&omega;
  -  August 9, 2023 : A rather simple calculation of DRT (Distribution of Relaxation Times) with unconstrained Tikhonov parametrisation has been added. The help command directs now to this page. In addition, an error in naming Z-Hit transformed files has been found and corrected. This is a major upgrade, please use this version or later.
  -  August 7, 2023 : Change in the error management, if one fit fails, do not stop the oher fits anymore.
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
  -  June 12, 2023 : added a fourth term in the Z-hit calculations (the one with the pi^7/604800). It's contribution is very small though.
  -  June 10, 2023 : added the Z-hit calculation.
  
--
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>


