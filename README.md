# FEAPpv

FEAPpv is a simplifed and free version of FEAP and does not included many advanced features such as a parallel capability, contact, fe2, igafeap. It only supports a limited number of material models. The programming architecture of FEAPpv is generally similar to that of FEAP but often is a bit behind in development. The official website of FEAPpv can be found at http://projects.ce.berkeley.edu/feap/feappv. To compile and build FEAPpv from the source code in this repository, see http://feap.berkeley.edu/wiki/index.php/Installation. 

The FEAPpv source code in this repository is an updated version with some corrections not avaialbe in the official version.  
* The `neoh3f(*)` subroutine for the [Neo-Hookean hyperelastic material model][Neohookean] has been updated.  
* The `hdata.h` file under `\include\integer4` has been updated due to an error. 

For information about FEAP, see http://projects.ce.berkeley.edu/feap and FEAP Wiki at http://feap.berkeley.edu/wiki. If you have any questions about this program or the full version FEAP, please visit the user's forum at http://feap.berkeley.edu.

[Neohookean]:https://en.wikipedia.org/wiki/Neo-Hookean_solid
