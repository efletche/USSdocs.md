#Starter File format

SS will call the file `STARTER.SS` during the data structuring phase. The format and content is a follows.

Some parameters in the starter file may require additional information in the immediate line if the conditional is met. Otherwise, omit or comment out these entries if the appropriate condition was not selected. For example, if there were more than zero *Extra SD report years* then the user must define the vector after this value.

## File Structure

* [Starter comment `#C`](#starter-comment-c)
* [Data Filename](#data-filename)
* [Control Filename](#control-filename)
* [Initial Parameter Values](#initial-parameter-values)
* [Run Display Detail](#run-display-detail)
* [Detailed age-sturcture Report](#detailed-age-structured-report-in-report-sso)
* [Checkup](#checkup)
* Parameter Trace
* Cumulative Report
* Full Priors
* Soft Bounds
* Data File Output
* Turn Off estimation
* MCMC burnin
* MCMC thin
* Jitter
* SD Report Start
* SD Report End
* Extra SD Report Years
  * (If Extra Report Years > 0) Vector of Extra Report Years
* Final convergence
* Retrospective year
* Summary biomass min age
* Depletion basis
* Depletion denominator fraction
* SPR report basis

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
