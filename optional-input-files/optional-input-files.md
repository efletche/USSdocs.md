# Optional Input Files

## RUNNUMBER.SS
This file contains a single integer value.  It is read when the program starts, incremented by 1, used when processing the profile value inputs (see below), used as an identifier in the batch output, then saved with the incremented value.  Note that this incrementation may not occur if a run crashes.  

## PROFILEVALUES.SS
This file contains information for changing the value of selected parameters for each run in a batch.  In the ctl file, each parameter that will be subject to modification by `PROFILEVALUES.SS` is designated by setting its phase to `-9999`.  
 
The first value in `PROFILEVALUES.SS` is the number of parameters to be batched.  This value **MUST** match the number of parameters with phase set equal to `-9999` in the ctl file.  The program performs no checks for this equality.  If the value is zero in the first field, then nothing else will be read.  Otherwise, the model will read `runnumber * Nparameters` values and use the last `Nparameters` of these to replace the initial values of parameters designated with phase = `-9999` in the ctl file.  

*Usage Note*: If one of the batch runs crashes before saving the updated value of `runnumber.ss`, then the processing of the `profilevalue.ss` will not proceed as expected.  Check the output carefully until a more robust procedure is developed.
