



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

-   What is OSDI/OpenVAF ?
-   Getting started with OSDI/OpenVAF

TCLspice

-   [What is TCLspice ?](./tclspice.html)
-   [TCLspice users manual](./tclusers.html)
-   [TCLspice by examples](./tclexamples.html)
-   [Designer's note](./tclnotes.html)

Ngspice uses OSDI/OpenVAF for including Verilog-A compact device models

Since version 39 ngspice contains the [OSDI](https://semimod.de/projects/) interface. OSDI allows loading compiled Verilog-A compact device models at run-time. Advantages of this new approach are:

-   All Verilog-A compact device models (from [VA-Models](https://github.com/dwarning/VA-Models), a collection of Verilog-A models preared for ngspice, from [CMC](https://si2.org/standard-models/), or from other sources) are now accessible by ngspice.
-   User-provided Verilog-A compact device models may be compiled, loaded and simulated as well.
-   Very fast model compilation with [OpenVAF](https://openvaf.semimod.de/) (around 2s, needed once per model, which then is usable for all subsequent simulations).
-   Very efficient model execution in ngspice, including parallel evaluation.
-   No code changes and re-compilation of ngspice required.
-   Multiple models within a single simulation run are loaded on the fly.

Getting started with OSDI/OpenVAF

Several steps are necessary to add Verilog-A models to ngspice. Here you will find only a coarse to do list. A detailed description is available in the ngspice manual, chapter 13 (available as [pdf](./docs/ngspice-manual.pdf) or [html](./docs/ngspice-html-manual/manual.xhtml)).

-   Get a Verilog-A compact model: There is a github repository [VA-Models](https://github.com/dwarning/VA-Models) providing nearly all of the publicly available Verilog-A compact models. The models are checked against the LRM 2.4.0 Verilog AMS standard. [CMC](https://si2.org/standard-models/) is another source. Or you may develop your own models!
-   Obtain suitable model parameters.
-   Obtain and install the OpenVAF compiler (Linux or MS Windows, no macOS for now).
-   Compile the model with OpenVAF, obtaining a shared model library \*.osdi.
-   Load \*.osdi into ngspice.
-   Create your netlist, adding device lines starting with N for the \*.osdi models.
-   Run your simulation.

Steps 1 to 5 need to be done only once, if you want to set up a series of simulations. Simulation speed has been proven to be similar (sometimes even faster) compared to built-in C-coded models.
ADMS is declared deprecated

ADMS is no longer part of the ngspice development project. Its usage for integrating Verilog-A compact device models has been difficult. Its output often has been buggy, and there is no active maintenance available. It will be removed in a future ngspice release version.

