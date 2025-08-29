



[Home](./index.html)

[Screenshots](./screens.html)

[Download](./download.html)

[Documentation](./docs.html)

[Extras/Options](./extras.html)

[Contributions](./contrib.html)

Development

[Simulation Environments](./resources.html)

[Quality](./quality.html)

Ngspice Development

-   [Developers Info](./devel.html)

-   [Bug Reports](./bugrep.html)

-   [Git Access](./gitaccess.html)

-   [Docs for developers](./devdocs.html)

-   [Mailing List Archives](./mlarch.html)

-   [Releases Info](./relinfo.html)

-   [Roadmap](./roadmap.html)

-   [Writing Docs](./docwrite.html)

-   

    ------------------------------------------------------------------------

-   [Tests](./applic.html#test)

OSDI/OpenVAF for ngspice

-   [What ADMS is ?](./osdi.html)

GSS-TCAD

-   GSS

TCLspice

-   [What TCLspice is ?](./tclspice.html)
-   [TCLspice users manual](./tclusers.html)
-   [TCLspice by examples](./tclexamples.html)
-   [Designer's note](./tclnotes.html)

GSS TCAD for ngspice no longer supported

With upcoming ngspice-39 GSS will no longer be supported. Please use ngspice-38 or older when using the GSS interface.

GSS TCAD for ngspice

GSS stands for General-purpose Semiconducor Simulator and is a TCAD software which enables two-dimensional numerical simulation of semiconductor devices with the drift-diffusion and hydrodynamic method.

Basic features:

-   GSS has Basic DDM (drift-diffusion method) solver, Lattice Temperature Corrected DDM solver and EBM (energy balance method) solver.
-   The GSS program is directed via input statements by a user specified disk file.
-   Support triangle mesh generation and adaptive mesh refinement.
-   Employed PMI (physical model interface) to support various materials, including compound semiconductor materials such as SiGe and AlGaAs.
-   Support DC sweep, transient and AC sweep calculations. The device can be stimulated by voltage or current source(s).
-   Support IV curve automatically trace. (Experimental)
-   Support some advanced features such as high field mobility, impact ionization, band-band tunneling and so on.
-   Support network level interface to ngspice for device/circuit mixed simulation.
-   2D and 3D plot capacity for post-process.

GSS distribution

GSS-TCAD is distributed separately from ngspice. You can download the GSS TCAD simulator from [it's web site](http://gss-tcad.sourceforge.net/). GSS compiles indipendently from ngspice, the two programs are linked via network interface.

GSS Licensing

GSS is a free open source software covered by the BSD license.

About the author:

The GSS TCAD has been developed by [Gong Ding](mailto:gdiso@ustc.edu). It is no longer maintained actively.

Relevant Links

-   [GSS](http://gss-tcad.sourceforge.net): The home page of the GSS TCAD.

