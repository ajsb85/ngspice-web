



[Home](./index.html)

[News](./news.html)

[Screenshots](./screens.html)

[Download](./download.html)

[Documentation](./docs.html)

[Extras/Options](./extras.html)

[Applications](./applic.html)

[Development](./devel.html)

[Simulation Environments](./resources.html)

[Quality](./quality.html)

Ngspice Development

-   [Developers Info](./devel.html)

-   [Bug Reports](./bugrep.html)

-   [Git Access](./gitaccess.html)

-   [Docs for developers](./devdocs.html)

-   [Mailing List Archives](./mlarch.html)

-   [Releases Info](./relinfo.html)

-   Roadmap

-   [Writing Docs](./docwrite.html)

-   

    ------------------------------------------------------------------------

-   [Tests](./applic.html#test)

Ngspice development roadmap

There is no "official" development roadmap. What follows is a list of topics that we think should be addressed. There is no priority given in the list below, and we need people interested in contributing code. This is an open source project and we together will choose the options where we have most fun coding and testing.  

Guidelines

Ngspice it is an up-to-date representation of the spice3 circuit simulator, which is often referred as a "de facto" circuit simulation standard. Keeping spice3 compatibiliy should be a general guideline. Compatibility with other simulators is another guideline. It is important to use a common interface to share netlists and output vectors with other simulators.

Your contribution

There are various tools for contributing to ngspice. You may discuss your ideas on the [developers' discussion forum](https://sourceforge.net/p/ngspice/discussion/127605/). Code or example snippets can be published. For publishing and discussing complete patches, we have our [patch tracker](https://sourceforge.net/p/ngspice/patches/), where standard diffs or complete \*.c files are welcome. Finally the Sourceforge git interface allows issuing a [merge request](https://sourceforge.net/p/ngspice/ngspice/merge-requests/), after you have cloned the project and made the updates locally on the clone.

Frontend related topics:

-    Compatibility: Read PSPICE, HSPICE or LTSPICE netlists (partially done).
-    Compatibility: Enable reading HSPICE founndry PDKs (partially done).
-    Unify access to built in functions: The three internal function parsers (numparam,. B source, command interpreter) have partially different built in functions available. Unify them to make access transparent to the user (mostly done).
-    Plotting: Add second Y axis to standard plot.

Analyses related topics:

-   Add harmonic balance analysis capability. (ongoing)
-   Improve mixed signal simulation capability. (mostly done)
-   Improve transfer function and pole-zero code. Improve convergence, (almost) always return correct number of poles and zeros.

Devices related topics:

-   Verilog-A compact models: Add support for Verilog-A compact models for access to modern devices, using OSDI/OpenVAF (almost done).
-   Add basic noise simulation capability to analog code models.
-   Add large signal transient noise simulation.
-   Add OTA code model to support LTSPICE A OTA device.
-   Add IBIS support.
-   Add device parameters (@dev\[param\]) to be used in B source.
-   Add a saturable core inductor (e.g.  [this one](http://fmtt.com/Transformer%20SPICE%20Model%202-14-08.pdf)).

Documentation related topics:

-   Update documentation with latest additions. (ongoing)
-   Expand documentation with examples and recipes for the novice users.

Code quality related topics:

-   Build a non regression test suite (ongoing).

Performance related topics:

-   Investigate if the basic numeric loops in ngspice are efficient on modern CPUs. Shall we exploit the capabilities of modern GPUs? (almost done, see [CUSPICE)](./cuspice.html)
-   Investigate if an alternative matrix solver can [improve simulation speed](http://www.siam.org/news/news.php?id=1121) (KLU is available).  

Interfaces with other software:

-   Schematic entry: Enhance ngspice integration into KiCad. (ongoing)
-   Schematic entry: Enhance ngspice integration into XSCHEM. (ongoing)
-   Co-simulation with HDL (hardware description language) input:  Add Verilog or VHDL interfaces. [GHDL](http://ghdl.free.fr/) or the [vpi interface](https://en.wikipedia.org/wiki/Verilog_Procedural_Interface) are potential candidates.

Other ngspice options:

Audio WAVE: Add reading and writing sound files into ngspice for audio simulation permanently. [ngspice-41](https://sourceforge.net/p/ngspice/ngspice/ci/hv-wave/tree/) is available with wave support.

