#Starter File format

SS will call the file `STARTER.SS` during the data structuring phase. The format and content is a follows.

Some parameters in the starter file may require additional information in the immediate line if the conditional is met. Otherwise, omit or comment out these entries if the appropriate condition was not selected. For example, if there were more than zero *Extra SD report years* then the user must define the vector after this value.

## File Structure

* [Starter comment `#C`](##Starter-comment-`#C`)
* Data Filename
* Control Filename
* Initial Parameter Value
* Run Display Detail
* Detailed age-sturcture Report
* Checkup
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
