# Forecast File

The specification of options for forecasts is contained in the mandatory input
file named `FORECAST.SS`. For additional details on the forecast file see the
forecast module Appendix.

## File Structure

* [Forecast comment `#C`](#c-forecast-comment)
* [Benchmarks](#benchmarks)
* [Forecast Method](#forecast-method)
  * (If Forecast Method is 5):
    * [First year for recent average F](#recent-average-f-first-year)
    * [Last year for recent average F](#recent-average-f-last-year)
  * (If Forecast Method is 6)
    * [F multiplier](#f-multiplier)
* [SPR target](#spr-target)
* [Biomass target](#biomass-target)
* [Benchmarks Years](#benchmark-years)
* [Benchmark Relative F Basis](#benchmark-relative-f-basis)
* [Forecast](#forecast)
* [N Forecast Years](#n-forecast-years)
* [F scalar](#f-scalar)
* [Forecast Years](#forecast-years)
* [Control Rule](#control-rule)
* [Control Rule Upper Limit](#control-rule-upper-limit)
* [Control Rule Lower Limit](#control-rule-lower-limit)
* Control Rule Buffer
* Number Of Forecast Loops
* First forecast loop with stochastic recruitment
* Forecast Loop Control #3
* Forecast Loop Control #4
* Forecast Loop Control #5
* First Year for Caps and Allocations
* Implmentation Error
* Rebuilder
* Rebuilder Start Year (Y initial)
* Fleet Relative F
* Basis for Maximum Forecast Catch
* [End Of File](#end-of-file)


## `#C` Forecast Comment
Forecast files must begin with `#C`. Any remaining characters after the `#C` in that line is free form.

All lines in this file beginning with `#C` will be retained and written on the top of several output files.

## Benchmarks
Option | Description
-------| ----
0      | Omit
1      | Calculate F_spr, F_btgt, F_msy

*Typical Value: 1*

SS checks for consistency of the Forecast and benchmark specification. It will turn benchmarks on if necessary and report a warning

## Forecast Method
Option | Description
-------| ----
0      | None
1      | F(SPR)
2      | F(MSY)
3      | F(B<sub>target</sub>)
4      | F(endyr)
5      | Average recent F (enter years) --- unimplemented
6      | F<sub>multi</sub> --- unimplemented

*Typical Value: 1*

Specifies whether or not to do a forecast and which F to use for that forecast.

For option 5 and 6, some additional conditional input is required.

No additional input is required for options 0-4.

## Condition: If Forecast Method is 5
If *Forecast Method* is 5, include the following parameter lines after [Forecast Method](#forecast-method).

#### Recent average F first year  
*Typical Value: -4*

First year for recent ave F relative to end year. Read a range of years for calculation of recent average F *(not yet implemented)*

####Recent average F last year
*Typical Value: 0*

Last year for recent average F. Will be used to calculate an average F multiplier for each fleet over a range of years

## Condition: If Forecast Method is 6
If *Forecast Method* is 6, include the following parameter line after [Forecast Method](#forecast-method).

#### F multiplier
*Typical Value: 0.6*

*(not yet implemented)*

## SPR target
*Typical Value: 0.45*

SS searches for F multiplier that will produce this level of spawning biomass (Reproductive output) per recruit relative to unfished value.

## Biomass Target
*Typical Value: 0.40*

SS searches for F multiplier that will produce this level of spawning biomass relative to unfished value. This is not “per recruit” ([SPR<sub>Target</sub>](#spr-target))   and takes into account the Spawner-Recruitment relationship.

## Benchmark Years
Requires 6 years entered: beginning and ending years for biology, selectivity, and relative Fs. (*beg_bio*; *end_bio*; *beg_selex*; *end_selex*; *beg_relF*; *end_relF* ) These values will be used in to calculate benchmark quantities.  

Option | Description
-------| ----
>0     | Absolute Year
<=0    | Year relative to end year

*Typical Value: 0 0 0 0 0 0*

Option to enter the actual year or values of 0 or negative integer values that will set the value to the model ending year.  

## Benchmark Relative F Basis
Option | Description
-------| ----
1      | Use year range
2      | Set *relF* same as forecast below

*Typical Value: 1*

## Forecast
Option | Description
-------| -----------
0      | None (no forecast years)
1      | Set to F(SPR)
2      | Search for F(MSY)
3      | Set to F(B<sub>target</sub>)
4      | Set to F(endyr)
5      | Input annual [F scalar](#f-scalar)

*Typcical Value: 2*

SS will ignore this parameter if benchmarks are disabled.

If Benchmarks is enabled, then *F_spr* and *F_btgt* are calculated. This parameter determines whether *F_MSY* is also calculated or is set to one of these other quantities

## N Forecast Years
*Typical Value: 10*

Number of forecast years

## F Scalar
*Typical Value: 1*

Used if [Forecast](#forecast) parameter is set to 5

## Forecast Years
Requires 4 years entered: Beginning and ending years for selectivity, and relative Fs (*beg_selex*; *end_selex*; *beg_relF*; *end_relF*). These will be used in population forecasts.

Option | Description
-------| -----------
>0     | Absolute year
<=0    | Year relative to end year

*Typical Value: 0 0 0 0*

Option to enter the actual year or values of 0 or negative integer values that will set the value to the model ending year.

## Control Rule
Option | Description
-------| -----------
1      | catch = f(SSB) U.S. West Coast
2      | F = f(SSB)

## Control Rule Upper Limit
*Typical Value: 0.4*

Biomass level (as fraction of B0) above which F is constant

## Control Rule Lower Limit
*Typical Value: 0.1*

Biomass level (as fraction of B0) below which F is set to 0.0
