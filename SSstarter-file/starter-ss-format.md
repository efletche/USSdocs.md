#Starter File format

SS will call the file `STARTER.SS` during the data structuring phase. The format and content is a follows.

Some parameters in the starter file may require additional information in the immediate line if the conditional is met. Otherwise, omit or comment out these entries if the appropriate condition was not selected. For example, if there were more than zero *Extra SD report years* then the user must define the vector after this value.

## File Structure

* [Starter comment `#C`](#starter-comment-c)
* [Data Filename](#data-filename)
* [Control Filename](#control-filename)
* [Initial Parameter Values](#initial-parameter-values)
* [Run Display Detail](#run-display-detail)
* [Detailed age-sturcture Report](#detailed-age-structured-report-in-reportsso)
* [Checkup](#checkup)
* [Parameter Trace](#parameter-trace)
* [Cumulative Report](#cumulative-report)
* [Full Priors](#full-priors)
* [Soft Bounds](#soft-bounds)
* [Data File Output](#data-file-output)
* [Turn Off estimation](#turn-off-estimation)
* [MCMC burn](#mcmc-burn)
* [MCMC thin](#mcmc-thin)
* [Jitter](#jitter)
* [SD Report Start](#sd-report-start)
* [SD Report End](#sd-report-end)
* [Extra SD Report Years](#extra-sd-report-years)
  * (If Extra Report Years > 0) [Vector of Extra Report Years](#sd-reporting-years)
* [Final convergence](#final-convergence)
* [Retrospective year](#retrospective-year)
* [Summary biomass min age](#-summary-biomass-min-age)
* [Depletion basis](#depletion-basis)
* [Depletion denominator fraction](#depletion-denominator-fraction)
* [SPR report basis](#spr-report-basis)
* [F reporting units](#f_std-report-units)
  * (If F reporting units = 4) [Age Range](#age-range)
* [F Report Basis](#f-report-basis)
* [End Of File](#end-of-file)

---

## Starter Comment `#C`
Starter files must begin with `#C`. Any remaining characters after the `#C` in that line is free form.

All lines in this file beginning with `#C` will be retained and written on the top of several output files.

## Data Filename
Filename of data file

## Control Filename
Filename of control file

## Inital Parameter Values
Option | Description
-------| ----
0      | Use Values in the Control File
1      | Use _SS3.PAR_ after reading setup in the control file

*Typical value: 0*

Do not use this if there have been any changes to the control file that would alter the number or order of parameters stored in the *SS3.PAR* file.

Values in the *SS3.PAR* file can be edited __*carefully*__.

## Run Display Detail
Option | Description
-------| ----
0      | None other than ADMB outputs
1      | One brief line of display for each iteration
2      | Fuller display per iteration

*Typical value: 1*

With option 2, the display shows the value of each logL component for each iteration and it displays where crash penalties are created.

## Detailed age-structured report in REPORT.sso
Option | Description
-------| ----
0      | Omit catch-at-age for each fleet and cohort
1      | Include all output

*Typical Value: 1*

## Checkup
Option | Description
-------| ----
0      | Omit
1      | Write detailed intermediate calculations to *CHECKUP.SSO* during first call

*Typical Value: 0*

*CHECKUP.SSO* is primarily used for debugging purposes. The output is unformatted and undocumented.

## Parameter Trace
Option | Description
-------| ----
0      | omit
1      | Write good iterations and active parameters
2      | Write good iterations and all parameters
3      | Write every iteration and all parameters
4      | Write every iteration and active parameters

*Typical value: 0*

This controls the output to *PARMTRACE.SSO*

The contents of this output can be used to determine which values are changing when a model approaches a crash condition.  It also can be used to investigate patterns of parameter changes as model convergence slowly moves along a ridge.

## Cumulative Report
Option | Description
-------| ----
0      | Omit
1      | Brief
2      | Full

*Typical Value: 1*

Controls reporting to the file *CUMREPORT.SSO*.

This cumulative report is useful when accumulating summary information from likelihood profiles or when simply accumulating a record of all model runs within the current subdirectory.

## Full Priors
Option | Description
-------| ----
0      | Only calculate priors for active parameters
1      | Calculate priors for all parameters that have a defined prior

*Typical Value: 1*

Enabling the full priors (with the option set to `1`) causes all priors to be calculated. With this option off (as `0`), the total logL, which includes the logL for priors would change between model phases as more parameters become active.


## Soft Bounds
Option | Description
-------| ----
0      | Omit
1      | Use

*Typical Value: 1*

The soft Bound option creates a weak symmetric beta penalty for the selectivity parameters.

Soft bounds becomes important when estimating selectivity functions in which the values of some of the parameters cause other parameters to have negligible gradients, or when bounds have been set too widely such that a parameter drifts into a region in which it has negligible gradient. Therefore, soft bound creates a weak penalty to move parameters away from the bounds.

## Data File Output
Option | Description
-------| ----
0      | None
1      | Output an annotated replicate of the data input file
2      | Add a second data file containing the model's expected values with no error added
3 to N | Add *N-2* parametric bootstrap data files

*Typical value: 1*

All output files are sequentially output to *DATA.SS_new* and will need to be parsed by the user into separate data files.

The output from the input data file makes no changes, so retains the order of the original file.

Output files 2 to N contain only observations that have not been excluded through use of the negative year denotation, and the order of these output observations is as processed by the model. The *N-obs* values are adjusted accordingly. At this time, the tag recapture data does not output to *DATA.SS_new*.


## Turn Off Estimation
Option | Description
-------| ----
-1     | Exit After reading input files
0      | Exit after reading one call to the calculation routines and production of _*.SSO_ and _*.SS_New_ files
Any Positive integer | Exit after completing this phase

*Typical Value: 8*

Option `0` is useful for:

1. Quickly reading in a messy set of input files and producing the annotated *CONTROL.SS_new* and *DATA.SS_new* files
2. Or examining model output based solely on input parameter values.  

Similarly, the value option allows examination of model output after completing a specified phase.  Also see usage note for restarting from a specified phase.

## MCMC burn
Burn value for MCMC runs

## MCMC thin
Thinning value for MCMC runs

## Jitter
Option | Description
-------| ----
Any Positive number | Adds a small random jitter to the initial parameter values

*Typical Value: 0.0*

The *Jitter* factor is multiplied by a random normal deviation *rdev=N(0,1)*, to a transformed parameter value based upon the predefined parameter bounds as:

<!--TODO: Embed math equations in GFM -->
```
                               P    - P    + 0.0.0000002
          1                     max    min
temp =  - - rdev * jitter * ln(------------------------- - 1)
          2                    P    - P    + 0.0.0000001
                                val    min
```
with the final *jittered* setting parameter value back transformed as:

```
                     P    - P
                      max    min  
P     =  P     +  ----------------
 new      min           - 2 * temp
                  1 + e
```

## SD Report Start
Option  | Description
--------|------------
-1      | Begin annual SD report in start year
year    | Begin SD report this year

*Typical Value: -1*

## SD Report End
Option  | Description
--------|------------
-1      | End annual SD report in end year
-2      | End annual SD report in last forecast year
year    | End SD annual report in this year

*Typical Value: -1*

## Extra SD Report Years
Option  | Description
--------|------------
0       | none
Any Positive Interger | Number of years to read

*Typical Value: 2*

In a long time series appilication, the model variance calculations will be smaller and faster if not all years are included in the SD report. For example, the annual SD report could start at 1960 and the extra option could select SD report in each decade before then.

## Condition: If Extra SD Report Years > 0
If the value of *Extra SD Report Years* > 0, include the following parameter line after [Extra SD Report Years](#extra-sd-report-years).

#### SD Reporting Years
Vector of years for additional reporting.

*Example Values:*
```
1940 1950 #vector of year values
```

## Final Convergence

*Default Value: 0.0001*

The default value, 0.0001, is reasonable for the change in *logL* denoting convergence.  For applications with big data and thus a large total *logL* value, a larger convergence criterion may still provide acceptable convergence.

## Retrospective Year
Option  | Description
--------|------------
0       | none
-X      | Retrospective year relative to end year.

*Typical Value: 0*

Adjusts the model end year and disregards data after this year.  May not handle time varying parameters completely.

## Summary Biomass Min Age

*Typical value: 2*

Minimum integer age for inclusion in the summary biomass used for reporting and for calculation of total exploitation rate

## Depletion Basis
Option  | Description
--------|------------
0       | skip
1       | X*B<sub>0</sub>
2       | X*B<sub>msy</sub>
3       | X*B<sub>styr</sub>

*Typical Value: 1*

Selects the basis for the denominator when calculating degree of depletion in SSB.  The calculated values are reported to the SD report

## Depletion denominator fraction

*Typical Value: 0.40*

The fraction (The X value of the [Depletion Basis](#depletion-basis) formulas) for depletion denominator to calculate the ratio SSBy / (0.40*SSB0)

## SPR Report Basis
Option  | Description
--------|------------
0       | Skip
1       | Use 1-SPR<sub>target</sub>
2       | Use 1-SPR at MSY
3       | Use 1-SPR at B<sub>target</sub>
4       | No denominator, report actual 1-SPR values

*Typical Value: 1*

**SPR** is the equilibrium SSB per recruit that would result from the current year’s pattern and intensity of F’s.  The SPR approach to measuring fishing intensity was implemented because the concept of a single annual F does not exist in SS.

The quantities identified by option 1, 2, and 3 here are all calculated in the benchmarks section.  Then the one specified here is used as the selected denominator in a ratio with the annual value of `1.0 – SPR`.

This ratio (and its variance) is reported to the SD report output for the years selected above in the SD report year selection.

## F_std report units
Option  | Description
--------|------------
0       | Skip
1       | Exploitation rate in biomass
2       | Exploitation rate in numbers
3       | Sum(full F’s by fleet)
4       | Population F for range of ages

*Typical Value: 4*

Also known as *F_report*, or *F_report_units*

Options **1** and **2** use total catch for the year and summary abundance at the beginning of the year, so combines seasons and areas.  But if most catch occurs in one area and there is little movement between areas, this ratio is not informative about the F in the area where the catch is occurring.

Option **3** is a simple sum of the full F’s by fleet, so may provide nonintuitive results when there are multi areas or seasons or when the selectivities by fleet do not have good overlap in age.  

Option **4** is a real annual F calculated as a numbers weighted F for a specified range of ages (read below).  The F is calculated as Z-M where Z and M are each calculated an ln(N(t+1)/N(t)) with and without F active, respectively. The numbers are summed over all biology morphs and all areas for the beginning of the year, so subsumes any seasonal pattern.

In addition to SPR, an additional proxy for annual F can be specified in this parameter.  As with SPR, the selected quantity will be calculated annually and in the benchmarks section.  The ratio of the annual value to the selected (see F report basis below) benchmark value is reported to the SD report vector.

## Condition: if F_std report units = 4
If the value of *F_std report units* or *F_report_units is *4* include the following parameter line after [F_std report units](#fstd-report-units).

###Age Range

*Typical Value: 14 17*

Specify range of ages.  Upper age must be less than max age because of incomplete handling of the accumulator age for this calculation.

## F report basis
Option  | Description
--------|------------
0       | Not relative, report raw values
1       | Use F_std value corresponding to SPR<sub>target</sub>
2       | Use F_std value corresponding to F<sub>msy</sub>
3       | Use F_std value corresponding to F<sub>Btarget </sub>

*Typical Value: 1*

Selects the denominator to use when reporting the [F_std report values](#f_std-report-units). Note that order of these options differs from the biomass report basis options

## End of file

To denote the end of the starter file put `999` as your last line.

```
999 #End of file
```

`999` must be the first 3 characters with no preceding tab or spaces in the character line in order to be correctly parsed by the #C comment reader. Inline comments after `999` are optional, and should not the effect the parser.
