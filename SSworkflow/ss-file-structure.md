#File Organization 

## Input Files 

1. STARTER.SS:  required file containing filenames of the data file and the control file plus other run controls (required). 
2. <datafile>:  file containing model dimensions and the data with file extension .dat (required) 
3. <control file>:  file containing set-up for the parameters with file extension .ctl (required) 
4. FORECAST.SS:  file containing specifications for forecasts (required) 
5. SS3.PAR:  previously created parameter file that can be read to overwrite the initial parameter values in the control file (optional) 
6. RUNNUMBER.SS:  file containing a single number used as runnumber in output to CUMREPORT.SSO and in the processing of PROFILEVALUES.SS (optional) 7. PROFILEVALUES.SS:  file contain special conditions for batch file processing (optional)  

## Output Files 
1. SS3.PAR, SS3.STD, SS3.REP, SS3.COR etc.  standard ADMB output files 
2. Echoinput.sso:  This file is produced while reading the input files and includes an annotated echo of the input.  The sole purpose of this output file is debugging input errors. 
3. Warning.sso:  This file contains a list of warnings generated during program execution. 
4. checkup.sso:  Contains details of selectivity parameters and resulting vectors.  This is written during the first call of the objective function. 
5. Report.sso:  This file is the primary report file. 
6. CompReport.sso:  Beginning with version 3.03, the composition data has been separated into a dedicated report 
7. FORECAST-REPORT.sso:  Output of management quantities and for forecasts 
8. cumreport.sso:  This file contains a brief version of the run output, output is appended to current content of file so results of several runs can be collected together.  This is useful when a batch of runs is being processed. 
9. Covar.sso:  This file replaces the standard ADMB ss3.cor with an output of the parameter and derived quantity correlations in database format 
10. data.ss_new:  contains a user-specified number of datafiles, generated through a parametric bootstrap procedure, and written sequentially to this file 
11. Control.ss_new:  Updated version of the control file with final parameter values replacing the Init parameter values. 
12. Starter.ss_new:  New version of the starter file with annotations 
13. Forecast.ss_new:  New version of the forecast file with annotations. 
14. REBUILD.DAT:  Output formatted for direct input to Andre Punt’s rebuilding analysis package. Cumulative output is output to REBUILD.SS (useful when doing MCMC or profiles). 
 
## Auxiliary Excel Files 

1. SS3-OUTPUT.XLS: Excel file with macros to read report.sso and display results 
2. SELEX24_dbl_normal.XLS: 
  a. This excel file is used to show the shape of a double normal selectivity (option number 20 for age-based and 24 for length-based selectivity) given user-selected parameter values.
  b. Instructions are noted in the XLS file but, to summarize 
    i. Users should only change entries in a yellow box. 
    ii. Parameter values are changed manually or using sliders, depending on the value of cell I5. 
  c. It is recommend that users select plausible starting values for doublenormal selectivity options, especially when estimating all 6 parameters   d. Please note that the XLS does NOT show the impact of setting parameters 5 or 6 to “-999”.  In SS3, this allows the the value of selectivity at the initial and final age or length to be determined by the shape of the doublenormal arising from parameters 1-4, rather than forcing the selectivity at the intial and final age or length to be estimated separately using the value of parameters 5 and 6. 
3. SELEX17_age_randwalk.XLS:  
  a. This excel file is used to show the shape of age-based selectivity arising from option 17 given user-selected parameter values 
  b. Users should only change entries in the yellow box.  
  c. The red box is the maximum cumulative value, which is subtracted from all cumulative values.  This is then exponentiated to yield the estimated selectivity curve.  Positive values yield increasing selectivity and negative values yield decreasing selectivity. 
4. PRIOR-TESTER.XLS:  
  a. The “compare” tab of this spreadsheet shows how the various options for defining parameter priors work 
5. SS-Control_Setup.XLS: 
  a. Shows how to setup an example control file for SS 
6. SS-Data_Input.XLS:  
  a. Shows how to setup an example data input for SS 
7. Growth.XLS: 
  a. Excel file to test parameterization between the growth curve options within SS. 
  b. Instructions are noted in the XLS file but, to summarize 
    i. Users should only change entries in a yellow box.   
    ii. Entries in a red box are used internally, and can be compared with other parameterizations, but should not be changed. 
  c. The SS-VB is identical to the standard VB, but uses a parameterization where length is estimated at pre-defined ages, rather than A=0 and A=Inf.  The Schnute-Richards is identical to the Richards-Maunder, but similarly uses the parameterization with length at pre-defined ages.  The Richards coefficient controls curvature, and if the curvature coefficient = 1, it reverts to the standard VB curve.   
8. Movement.XLS:   a. Excel file to explore SS movement parameterization.   