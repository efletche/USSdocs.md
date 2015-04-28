# Auxiliary Excel Files
<!--TODO: Verify inclusion of excel files to SS -->
These excel helper files handle Stock Synthesis output and ecosystem modeling with SS. These auxiliary files may not (?) be included with SS installation.

### SS3-OUTPUT.XLSX
Excel file with macros to read *report.sso* and display results

### SELEX24_dbl_normal.XLSX
This excel file is used to show the shape of a double normal selectivity (option number 20 for age-based and 24 for length-based selectivity) given user-selected parameter values.

Instructions are noted in the Excel file but, to summarize:
  * Users should only change entries in a yellow box.
  * Parameter values are changed manually or using sliders, depending on the value of cell I5.
  * It is recommend that users select plausible starting values for doublenormal selectivity options, especially when estimating all 6 parameters
  * Please note that the XLSX does **NOT** show the impact of setting parameters 5 or 6 to “-999”.  In SS3, this allows the the value of selectivity at the initial and final age or length to be determined by the shape of the doublenormal arising from parameters 1-4, rather than forcing the selectivity at the initial and final age or length to be estimated separately using the value of parameters 5 and 6.

### SELEX17_age_randwalk.XLSX
This excel file is used to show the shape of age-based selectivity arising from option 17 given user-selected parameter values

Users should only change entries in the yellow box.  

The red box is the maximum cumulative value, which is subtracted from all cumulative values.  This is then exponentiated to yield the estimated selectivity curve.  Positive values yield increasing selectivity and negative values yield decreasing selectivity.

### PRIOR-TESTER.XLSX
The “compare” tab of this spreadsheet shows how the various options for defining parameter priors work

### SS-Control_Setup.XLSX
Shows how to setup an example control file for SS

### SS-Data_Input.XLSX:  
Shows how to setup an example data input for SS

### Growth.XLSX:
Excel file to test parameterization between the growth curve options within SS.

Instructions are noted in the XLSX file but, to summarize:
* Users should only change entries in a yellow box.
* Entries in a red box are used internally, and can be compared with other parameterizations, but should not be changed.

The SS-VB is identical to the standard VB, but uses a parameterization where length is estimated at pre-defined ages, rather than `A=0` and `A=Inf`.  The Schnute-Richards is identical to the Richards-Maunder, but similarly uses the parameterization with length at pre-defined ages.  The Richards coefficient controls curvature, and if the curvature `coefficient = 1`, it reverts to the standard VB curve.

### Movement.XLSX
Excel file to explore SS movement parameterization.
