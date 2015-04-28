#File Organization

## Input Files

1. STARTER.SS:  required file containing filenames of the data file and the control file plus other run controls (required).
2. *datafile*:  file containing model dimensions and the data with file extension .dat (required)
3. *control file*:  file containing set-up for the parameters with file extension .ctl (required)
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
