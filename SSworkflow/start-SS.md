#Getting Started with Stock Synthesis 

Stock Synthesis (SS) runs an command-line interface.  The executable, ss3.exe, can be run from the command prompt (cmd.exe) in Windows and or unix terminal.

The executable can also be called from other programs, such as R or the SS GUI or a batch file. See the section in this manual on use of batch file which can allow ss3.exe to reside in a separate directory.  
Sometimes you may receive a version of SS with array checking turned on (SS-safe.exe) or without array checking (SS_opt.exe).  In this case, it is recommended to rename the one you are planning to use to SS3.exe before running it.  

When the program first starts, it reads the file STARTER.SS, which must be located in the same directory from which SS is being run.  The file STARTER.SS contains required input information plus references to other required input files, as described in the File Organization section.  

Output from SS is as text files containing specific keywords. SS GUI, or R4ss can search for these keywords and parse the specific information located below that keyword in the text file. 
