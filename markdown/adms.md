



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

ADMS for ngspice

-   What is ADMS ?
-   [ADMS and ngspice HOWTO](./admshowto.html)

GSS-TCAD

-   [GSS](./gss.html)

TCLspice

-   [What is TCLspice ?](./tclspice.html)
-   [TCLspice users manual](./tclusers.html)
-   [TCLspice by examples](./tclexamples.html)
-   [Designer's note](./tclnotes.html)

Ngspice uses OSDI/OpenVAF for including Verilog-A compact device models

Since ngspice-39 the simulator contains the [OSDI](https://semimod.de/projects/) interface, which allows dynamically loading of compiled Verilog-A compact device models. Advantages of this new approach are:

-   All Verilog-A compact device models (from [VA-Models](https://github.com/dwarning/VA-Models), [CMC](https://si2.org/standard-models/) and other sources) are now available for ngspice
-   Very fast model compilation with [OpenVAF](https://openvaf.semimod.de/) (around 2s, needed once per model for all subsequent simulations)
-   Very efficient model execution in ngspice, including parallel evaluation
-   No code changes and re-compilation of ngspice required
-   Multiple models within a single simulation run are loaded on the fly

Please have a look at the [OSDI/OpenVAF](./osdi.html) page for further information.
ADMS declared obsolete

ADMS is no longer part of the ngspice development project. Its usage has been difficult, its output often buggy, and there is no active maintenance available. It will be removed in a future release version.

Ngspice and ADMS for Verilog-AMS modeling

ADMS is a code generator that converts electrical models written in Verilog-AMS into C code conforming to the API of spice simulators. The generated code will then be compiled into the simulator executable and the new device is ready for simulation.

What is Verilog-AMS ?

Verilog-AMS (AMS stands for Analog and Mixed Signals) is a language designed to describe and simulate analog and mixed signal designs using both the top-level design methodology as well as the more traditional bottom up approach.

ADMS uses extensions to the Verilog-AMS language, developed for compact modeling of devices.

ADMS distribution in ngspice

ADMS is distributed separately from ngspice. You can download the ADMS compiler from the [adms for ngspice](adms2/adms-svn-ngspice-src.zip) link to a zipped source code directory. For details please have a look at [ADMS and ngspice HOWTO](./admshowto.html).

The process of adding a new device is far from being automatic and need a certain knowledge of spice internals. The file README.adms distributed with ngspice describes the process.

ADMS Licensing

ADMS is licensed under the terms of LGPL.

About the author:

The ADMS system has been developed by Laurent Lemaitre.

ADMS Version

Ngspice implements ADMS version 2.3.0, modified

Relevant Links

-   [ADMS](http://mot-adms.sourceforge.net): The home page of the ADMS system. (No longer on-line!)
-   [Verilog-AMS](http://www.eda.org/twiki/bin/view.cgi/VerilogAMS): The VerilogAMS Work Group page.
-   [Verilog-AMS Standard](http://www.accellera.org/downloads/standards)

