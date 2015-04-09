#Parameter Line Elements

A primary role of the SS control file is to define the parameters to be used by the model.  The general syntax of a parameter line is described here.  Parameter lines will be used in three sections of the control file:  (1) natural mortality and growth; (2) spawnerrecruitment, initial F and catchability; and (3) selectivity.  The first seven elements of a parameter line are used in every section and will be referred to as a short parameter line.  The remaining elements are used just in sections (1) and (3).  Each parameter line contains: 

Short parameter lines have only the above 7 elements. The full parameter line syntax for the Mortality-Growth and Selectivity sections provides additional controls to give the parameter time-varying properties.  These are listed briefly below and described in more detail in the section Time Varying Parameter Options found at the end of the control file syntax section.

|Column|Element      |Description                                                                                                                                     |
|------|-------------|------------------------------------------------------------------------------------------------------------------------------------------------|
|1     |LO           |Minimum value for the parameter                                                                                                                 |
|2     |HI           |Maximum value for the parameter                                                                                                                 |
|3     |INIT         |Initial value for the parameter. If the SS3.PAR file is read, it overwrites these INIT values.                                                  |
|4     |Prior Value  |Expected value for the parameter.  This value is ignored if the Prior_type is –1 or 1                                                           |
|5     |Prior Type   |-1 = none, 0=normal, 1=symmetric beta, 2=full beta, 3=lognormal, 4=lognormal with bias adjustment, 5=gamma                                      |
|6     |Prior stddev |Standard deviation for the PRIOR, used to calculate likelihood of the current parameter value.  This value is ignored if Prior_type is –1       |
|7     |PHASE        |Phase in which parameter begins to be estimated.  A negative value causes the parameter to retain its INIT value (or value read from PAR file). |
|8     |ENV          |Create a linkage to an input environmental time series                                                                                          |
|9     |USE_Dev      |Invokes use of the dev vector                                                                                                                   |
|10    |DEV min yr   |Beginning year for the dev vector                                                                                                               |
|11    |DEV max yr   |Ending year for the dev vector                                                                                                                  |
|12    |DEV std.dev  |Standard deviation for elements in the dev vector.                                                                                              |
|13    |USE-BLOCK    |Set up blocks or parameter trends                                                                                                               |
|14    |BLOCK-TYPE   |Functional form for the block offset                                                                                                            |
