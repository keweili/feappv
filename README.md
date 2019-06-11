## FEAPpv ##

FEAPpv is a simplifed and free version of FEAP and does not included many advanced features such as a parallel capability, contact, fe2, igafeap. It only supports a limited number of material models. The programming architecture of FEAPpv is generally similar to that of FEAP but often is a bit behind in development. The official website of FEAPpv can be found at http://projects.ce.berkeley.edu/feap/feappv. To compile and build FEAPpv from the source code in this repository, see http://feap.berkeley.edu/wiki/index.php/Installation. 

The FEAPpv source code in this repository is an updated version with some corrections not avaialbe in the official version.  
* The `neoh3f(*)` subroutine for the [Neo-Hookean hyperelastic material model][Neohookean] has been updated.  
* The `hdata.h` file under `\include\integer4` has been updated due to an error. 


## Compiling and Installation of FEAPpv on Windows ##

The following workflow demonstrates how to compile and build FEAPpv from source code. The advantage of this new method is that you can build the FEAPpv main program and all the subroutines at once. In this method, we will create a Visual Studio solution which consists of two projects: the FEAPpv main program and a static library. At first, we will create a QuickWin Application for FEAPpv main program and then another project for the static library.   

1. Open Visual Studio. 
<ol type="a">
<li>Select File -> New -> Project…  </li>
<li>Select '''QuickWin Application''' on the left under Intel(R) Visual Fortran, then select '''QuickWin Application''' option on the right. </li>
<li>Name the main program, e.g. feappv.</li>
<li>Select a directory and remember it, e.g. <code>C:\Users\***\projects\feappv41\</code> </li>
<li>At the bottom, add a solution name, e.g. feappv41</li>
<li>Click OK</li>
</ol>  

2. At the top select "Release" build (as opposed to Debug)

3. Right-click the project name (feap) in the '''Solution Explorer''' window on the right and select Add ->  Existing Item...
<ol type="a">
<li>Set the file format to show "All Files (*.*)" in the window if needed </li>
<li>Add “feappv.f” from the "main" subdirectory of FEAP package, e.g. <br /> `C:\users\***\feappv41\main`</li>
</ol>

4.  Right-click the project name (feappv) again and select Properties
<ol type="a">
<li>Select Fortran on the left, then General</li>
<li>Add following FEAP include directories to the  ''Additional Include Directories'' : <br / >`C:\users\xxx\feappv41\include` <br /> and the appropriate directory for 32-bit Windows machine: <br /> `C:\users\xxx\feappv41\include\integer4` <br /> or for 64-bit Windows machine <br /> `C:\users\xxx\feappv41\include\integer8`. <br /> You only need one of them for your machine. </li>
</ol>

5. Right-click the solution name (feap85) -> Add -> New Project…
<ol type="a">
<li>Select Library on the left under Intel(R) Visual Fortran: </li>
<li>Select Static Library</li>
<li>Name library, e.g. lib41</li>
<li>Click OK</li>
</ol>

6. At top "Release" build should be selected already. If not, select Release build.

7. Right-click the ''lib41'' Project and select Properties
<ol type="a">
<li>Select Fortran, then General on the left</li>
<li>Add following FEAP include directories to the '''Additional Include Directories''': <br /> `C:\users\xxx\feappv41\include` <br /> and the appropriate directory for 32-bit Windows machine <br /> `C:\users\xxx\feappv41\include\integer4`, <br /> or 64-bit Windows machine,  <br />  `C:\users\xxx\feappv41\include\integer8`  <br /> Again, you only need one of them.
</li>
</ol>

8.  Right-click the ''lib41'' Project and select Add -> New Folder
<ol type="a">
<li>Change the name of the folder to ''elements''</li>
<li>Right-click the folder ''elements'' and Add -> Existing Item... </li>
<li>Navigate to the FEAP source folder at <br /> <code>C:\Users\***\feappv41\elements</code></li>
<li>Select all the Fortran source files in that folder and click Add button. </li>
</ol>

9.  Repeat Step 8 to add the following folders and their subfolders under the FEAP root directory ( <code>C:\Users\***\feappv41\</code>): ''plot'', ''program'', ''user'', and ''windows'' (do not add ''UNIX'', ''include'', and ''main'' folders in this step).   
 
10. If you have coded some user subroutines, you should remove the default dummy files under <code>feappv41/user</code> and add your own subroutines to a new folder or the same folder <code>feappv41/user</code>.

11. Right-click the Solution name ''feappv41'' given in Step 1 and select Properties
<ol type="a">
<li>In the window on the left, select '''Project Dependencies''' under '''Common Properties'''</li>
<li>In the project list on the right, select the ''feappv'' project we created in Step 1 if it is not selected. </li>
<li>In the "Depends on" window underneath, check the project ''lib41'' to indicate that the project ''feappv'' depends on project ''lib41''. </li>
<li>If you want to build FEAP for 64-bit version of Windows, select  ''Configuration Properties''  in the window on the left. Than, change the solution platform to the "x64" on the top and also change the platform for both the feappv main project and the lib41 project.</li> 
</ol>

12. Under the Build tab on the main menu select Build Solution. Then, the Fortran compiler will compile and build the static library and then the FEAPpv executable file (feappv.exe).  You can find the executable file in the solution directory chosen in Step 1, e.g. <br /> <code>C:\Users\***\projects\feappv41\feappv41\feappv\x64\Release</code> 

The program is ready to use.  


## FEAP User's Forum ##
For information about FEAP, see http://projects.ce.berkeley.edu/feap and FEAP Wiki at http://feap.berkeley.edu/wiki. If you have any questions about this program or the full version FEAP, please visit the user's forum at http://feap.berkeley.edu.

[Neohookean]:https://en.wikipedia.org/wiki/Neo-Hookean_solid
