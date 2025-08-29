![NGSPICE](./images/nglogo.jpg) ![Mixed mode - mixed level circuit simulator - based on Berkeley's Spice3f5](./images/ngtext2.jpg) [](https://sourceforge.net/projects/ngspice)

-   [Home](./index.html)
-   [News](./news.html)
-   [Screenshots](https://sourceforge.net/projects/ngspice/)
-   [Download](./download.html)
-   Documentation
-   [Tutorials](./tutorials.html)
-   [Extras/Options](./extras.html)
-   [Applications](./applic.html)
-   [Development](./devel.html)
-   [Simulation Environments](./resources.html)
-   [Quality](./quality.html)

Ngspice Docs

-   Documentation
-   [XSPICE and ngspice](./xspice.html)
-   [ngspice shared library](./shared.html)
-   [CUSPICE](./cuspice.html)
-   [OSDI/OpenVAF for ngspice](./osdi.html)
-   [TCLspice users manual](./tclusers.html)
-   [Links to other manuals](./literature.html)
-   [Tutorials](tutorials.html)
-   [Books](./books.html)

Ngspice Documentation

A ngspice manual is available as a pdf file. Here you may download the release version of the

-   [Ngspice user's manual (version 43).](./docs/ngspice-43-manual.pdf)

The manual is under continuous development and maintained at [Ngspice user's manual web site](http://ngspice.git.sourceforge.net/git/gitweb.cgi?p=ngspice/ngspice-manuals;a=tree). Here you may download the actual version as a pdf file, including all modifications made available in the git sources since the latest ngspice release, as the

-   [Ngspice user's manual (updated).](./docs/ngspice-manual.pdf)

Please remember that this manual is a "work in progress": New ngspice features will be added as they become available in git, there are still some minor bugs, and thus the manual may be updated from time to time without notice. You are welcome to contribute to this documentation!

A xhtml version of this most recent manual is available here:

-   [Ngspice user's xhtml manual (updated).](https://ngspice.sourceforge.io/docs/ngspice-html-manual/manual.xhtml)

You also may use information on spice3f and similar simulators available on the Internet. One of the best online manuals for spice3f4 is maintained by Charles Williams (including MacSpice enhancements):

-   [SPICE 3 (MacSpice) User's Manual.](https://www.macspice.com/ug/sec1.html)

Manuals for previous ngspice releases are still available:

-   [Ngspice user's manual (version 39).](./docs/ngspice-39-manual.pdf)
-   [Ngspice user's manual (version 40).](./docs/ngspice-40-manual.pdf)
-   [Ngspice user's manual (version 41).](./docs/ngspice-41-manual.pdf)
-   [Ngspice user's manual (version 42).](./docs/ngspice-42-manual.pdf)

Ngspice incorporates many models or options provided by external partners. They have often provided detailed information or manuals, which you may find [here](./literature.html).

Please send your comments, suggestions, and corrections on the ngspice manual to the [ngspice developers' list.](https://sourceforge.net/mailarchive/forum.php?forum_name=ngspice-devel)

Ngspice Internals (Control Flow etc.)

Meanwhile ngspice has become a complex piece of software. A typical simulation run may contain the following steps: Read the netlist, pre-process the netlist (e.g. compatibility, sub-circuits, parameters etc), create the circuit structure, create and fill in the matrix, run the simulation, process the resulting data.

Below you will find a list of available documents. They are formatted as Excel or Word files.

-   [Ngspice top level control flow](./docs/cf/ngspice_top-level_control-flow.xlsx)
-   [Ngspice command op (operating point)](./docs/cf/op_operating_point.xlsx)
-   [Ngspice device model parsing](./docs/cf/model_parsing.xlsx)
-   [Ngspice function parsers](./docs/cf/function-parsers.docx)

These files are just a first step to document the internals of ngspice (control flow etc.). More will be made available as time allows.

[](http://sourceforge.net) All text is available under the terms of the GNU Free Documentation License ![](./images/spice.jpg)
