# やっぱり #

__YAPPARI__ stands for Yet Another Program for Analysis and Research in Impedance.
This program can perform fits for one or multiple datasets. By multiple I mean hunderths or even thousands datasets (I made one fit for 1367 datasets), this may be slow but you will get all the results in a run, the results can be saved in a datafile. For a single dataset you may want to use a simpler program called [Yappari 4.2](https://github.com/nitad54448/win10-installer-yappari-4.2), available also as a Windows 10 installer. This single dataset program will not be developed further so it might be better to take a leap and move to version 5.


__Note__ : there is no warrantee whatsoever for using this program. Use it if you want : you will not receive much help from me, everything is in this documentation file. If youd don't want : don't use it. There are many other programs, some commercial and some free.. and likely some are better than this one. 

# yappari-v5-2023 #
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
