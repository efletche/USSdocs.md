#File Organization

## Input Files

#### STARTER.SS
Required file containing filenames of the data file and the control file plus other run controls **(required)**.

#### *datafile*
File containing model dimensions and the data with file extension .dat **(required)**

#### *control file*
file containing set-up for the parameters with file extension .ctl **(required)**

#### FORECAST.SS
file containing specifications for forecasts **(required)**

#### SS3.PAR
previously created parameter file that can be read to overwrite the initial parameter values in the control file (optional)

#### RUNNUMBER.SS
file containing a single number used as runnumber in output to *CUMREPORT.SSO and in the processing of *PROFILEVALUES.SS* (optional)

#### PROFILEVALUES.SS  
file contain special conditions for batch file processing (optional)  

## Output Files
#### SS3.PAR, SS3.STD, SS3.REP, SS3.COR, etc.
Standard ADMB output files

#### Echoinput.sso
This file is produced while reading the input files and includes an annotated echo of the input.  The sole purpose of this output file is debugging input errors.

#### Warning.sso
This file contains a list of warnings generated during program execution.

#### checkup.sso
Contains details of selectivity parameters and resulting vectors.  This is written during the first call of the objective function.

#### Report.sso:  
This file is the primary report file.

#### CompReport.sso
Beginning with version 3.03, the composition data has been separated into a dedicated report

#### FORECAST-REPORT.sso
Output of management quantities and for forecasts

#### cumreport.sso  
This file contains a brief version of the run output, output is appended to current content of file so results of several runs can be collected together.  This is useful when a batch of runs is being processed.

#### Covar.sso  
This file replaces the standard ADMB ss3.cor with an output of the parameter and derived quantity correlations in database format

#### data.ss_new
contains a user-specified number of datafiles, generated through a parametric bootstrap procedure, and written sequentially to this file

#### Control.ss_new
Updated version of the control file with final parameter values replacing the Init parameter values.

#### Starter.ss_new
New version of the starter file with annotations

#### Forecast.ss_new
New version of the forecast file with annotations.

#### REBUILD.DAT
Output formatted for direct input to Andre Punt’s rebuilding analysis package. Cumulative output is output to REBUILD.SS (useful when doing MCMC or profiles).
