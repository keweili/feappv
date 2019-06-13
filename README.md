## FEAPpv ##

FEAPpv is a simplifed and free version of FEAP and does not included many advanced features such as a parallel capability, contact, fe2, igafeap. It only supports a limited number of material models. The programming architecture of FEAPpv is generally similar to that of FEAP but often is a bit behind in development. The official website of FEAPpv can be found at http://projects.ce.berkeley.edu/feap/feappv. To compile and build FEAPpv from the source code in this repository, see http://feap.berkeley.edu/wiki/index.php/Installation. 

The FEAPpv source code in this repository is an updated version with some corrections not avaialbe in the official version.  
* The `neoh3f(*)` subroutine for the [Neo-Hookean hyperelastic material model][Neohookean] has been updated.  
* The `hdata.h` file under `\include\integer4` has been updated due to an error. 


## Compiling and Installation of FEAPpv on Windows ##

The following workflow demonstrates how to compile and build FEAPpv from source code. The advantage of this new method is that you can build the FEAPpv main program and all the subroutines at once. In this method, we will create a Visual Studio solution which consists of two projects: the FEAPpv main program and a static library. At first, we will create a QuickWin Application for FEAPpv main program and then another project for the static library.   

1. Open Visual Studio.  
    a. Select File -> New -> Project...  
    b. Select "QuickWin Application" on the left under Intel(R) Visual Fortran, then select "QuickWin Application" option on the right.   
    c. Name the project for the main program, e.g. feappv.  
    d. Select a directory and remember it, e.g. `C:\Users\***\projects\feappv41\`   
    e. At the bottom, add a solution name, e.g. feappv41   
    f. Click OK 

2. At the top select "Release" build (as opposed to Debug)  

3. Right-click the project name (feappv) in the "Solution Explorer" window on the right and select Add ->  Existing Item...    
    a. Set the file format to show "All Files (*.*)" in the window if needed    
    b. Add “feappv.f” from the "main" subdirectory of FEAPpv source code, e.g. <br /> `C:\users\***\feappv41\main`   
 
4.  Right-click the project name (feappv) again and select Properties     
    a. Select Fortran on the left, then General  
    b. Add following FEAPpv include directories to the ''Additional Include Directories'' : <br />`C:\users\xxx\feappv41\include` <br /> and the appropriate directory for 32-bit Windows machine: <br /> `C:\users\xxx\feappv41\include\integer4` <br /> or for 64-bit Windows machine <br /> `C:\users\xxx\feappv41\include\integer8`. <br /> You only need one of them for your machine.  
 

5. Right-click the solution name (feappv41) -> Add -> New Project...   
    a. Select Library on the left under Intel(R) Visual Fortran:   
    b. Select Static Library     
    c. Name library, e.g. lib41   
    d. Click OK    

6. At top "Release" build should be selected already. If not, select Release build.

7. Right-click the "lib41" Project and select Properties  
    a. Select Fortran, then General on the left    
    b. Add following FEAPpv include directories to the '''Additional Include Directories''': <br /> `C:\users\xxx\feappv41\include` <br /> and the appropriate directory for 32-bit Windows machine <br /> `C:\users\xxx\feappv41\include\integer4`, <br /> or 64-bit Windows machine,  <br />  `C:\users\xxx\feappv41\include\integer8`  <br /> Again, you only need one of them.
 

8.  Right-click the *lib41* Project and select Add -> New Folder. This will create a new forlder with the defult name, e.g. "NewFolder1"      
    a. Rigth click that folder and change the name to *elements*.  
    b. Right-click the folder *elements* and Add -> Existing Item...   
    c. Navigate to the FEAPpv source folder at <br /> `C:\Users\***\feappv41\elements`   
    d. Select all the Fortran source (`.f`) files in that folder and click Add button.    

9.  Repeat Step 8 to add the following folders and their subfolders under the FEAPpv root directory `C:\Users\***\feappv41\`: *plot*, *program*, *user*, and *windows*' (do not add *UNIX*, *include*, and *main* folders in this step).   
 
10. If you have coded some user subroutines, you should remove the default dummy files under `feappv41/user` and add your own subroutines to a new folder or the same folder `feappv41/user`.   

11. Right-click the Solution name ''feappv41'' given in Step 1 and select Properties    
    a. In the window on the left, select "Project Dependencies" under "Common Properties" .   
    b. In the project list on the right, select the *feappv* project we created in Step 1 if it is not selected.    
    c. In the "Depends on" window underneath, check the project *lib41* to indicate that the project *feappv* depends on project *lib41*.    
    d. If you want to build FEAPpv for 64-bit version of Windows, select  "Configuration Properties"  in the window on the left. Than, change the solution platform to the "x64" on the top and also change the platform for both the feappv main project and the lib41 project. 
 
12. Under the Build tab on the main menu select Build Solution. Then, the Fortran compiler will compile and build the static library and then the FEAPpv executable file (feappv.exe). You can find the executable file in the solution directory chosen in Step 1, e.g. <br /> `C:\Users\***\projects\feappv41\feappv41\feappv\x64\Release` 

The program is ready to use. If you encountered an error saying that some dll files such as "libifcoremd.dll" are missing while runing the executable file for the first time, please install the [Intel Fortran Compiler Redistributable Libraries][IntelForRed] for your computer first.   


## FEAP User's Forum ##
For information about FEAP, see http://projects.ce.berkeley.edu/feap and FEAP Wiki at http://feap.berkeley.edu/wiki. If you have any questions about this program or the full version FEAP, please visit the user's forum at http://feap.berkeley.edu.

[Neohookean]:https://en.wikipedia.org/wiki/Neo-Hookean_solid
[IntelForRed]:https://software.intel.com/en-us/articles/intel-compilers-redistributable-libraries-by-version  
