



[Home](./index.html)

[Screenshots](./screens.html)

[Download](./download.html)

[Documentation](./docs.html)

[Extras/Options](./extras.html)

[Contributions](./contrib.html)

Development

[Simulation Environments](./resources.html)

[Quality](./quality.html)

TCLspice

-   [What is TCLspice ?](./tclspice.html)
-   [TCLspice users manual](./tclusers.html)
-   [TCLspice by examples](./tclexamples.html)
-   [Designer's note](./tclnotes.html)

Ngspice Development

-   [Developers Info](./devel.html)

-   [Bug Reports](./bugrep.html)

-   [CVS Access](./cvsaccess.html)

-   [Docs for developers](./devdocs.html)

-   [Mailing List Archives](./mlarch.html)

-   [Releases Info](./relinfo.html)

-   [Roadmap](./roadmap.html)

-   [Writing Docs](./docwrite.html)

-   

    ------------------------------------------------------------------------

-   [Tests](./applic.html#test)

OSDI/OpenVAF for ngspice

-   [What is OSDI/OpenVAF ?](./osdi.html)

GSS-TCAD

-   GSS

TCLspice

TCLspice builds a [TCL/TK shell](http://www.tcl.tk/) on top of ngspice.

Current status

TCLspice is included and fully integrated into the ngspice source tree. All ngspice enhancements are accessible in tclspice as well. tclspice may be selected at compile-time, using the flag ./configure --with-tcl instead of --with-x, or --with-wingui. Ngspice then is made as a shared library (dll) ready for integration into tcl scripts. A graphics package using [blt](http://blt.sourceforge.net/) has been included.

Download

-   TCLspice is distributed with the core ngspice sources. Downloading the latest [ngspice distribution](https://sourceforge.net/project/showfiles.php?group_id=38962) or the ngspice development version from the [git server](http://ngspice.git.sourceforge.net/git/gitweb-index.cgi) is the best way to get it.
-   A 32 bit binary for MS Windows (including tcl/tk and blt dlls) is ready for download as a [7z compressed directory](https://ngspice.sourceforge.io/experimental/tclspice-25.7z) (still very experimental though).

Documentation

-   Refer to the links on the left.
-   The [Ngspice user's manual](./docs/ngspice-manual.pdf) at chapter 15 offers installation instructions (LINUX and MS Windows) as well as a desription of the examples.
-   The old TCLspice web page offers info on [tclspice commands.](http://tclspice.sourceforge.net/docs/tclspice_com.html)

Release Information

-   **Since ngspice 18:** tclspice has been integrated into the ngspice sources. It compiles smoothly under LINUX provided suitable tcl/tk headers and libs are available. Compilation under MS Windows is tedious, but possible, and is described in the ngspice manual.
-   **&lt;= 0.2.17:** Prior to release 0.2.17, refer to old [TCLspice page.](http://tclspice.sourceforge.net/)

To Do (Road map)

-   **Testing:**

-   -   **Installation:**

    -   -   The description in the actual [Ngspice user's manual](./docs/ngspice-manual.pdf) at chapter 19 needs some enhancements.

    -   **Use:**

    -   -   I think there are a few bugs. :) Let's make sure. Please send your bug report to one of the ngspice lists.

-   **Documentation:** This still needs to be corrected. Any remarks welcome. This documents can be enriched of your many contributions.

-   -   Correct what is wrong,
    -   Send me the link of your reference pages to populate the bibliography of the user manual,
    -   Document the code of your most brilliant scripts to include them in the "learn by example" section.

-   **Development:**

-   -   TCL HMI :
        -   Looking for a good TCL developer to develop a good TCL front-end: intuitive, proficient, easy to use, and so on. This is intended to be an independent project, but TCLspice and NGspice relies on it.
        -   The front-end will be independent from the simulator but both tclspice and ngspice will relies on it.
        -   A simulator engine like ngspice is very flexible. As a counterpart it is not frendly. There is a need for a front-end software that enables new users to  understand  and  proficiently use  it and, in the same time, is appealing to the  professional who is  skilled and doesn't  want to spend time wandering through menus and icons and prefers to write batch recipes. A good front-end is necessary for the end user.
    -   Windows port:
        -   Port to the most popular operating system.

-   **Cooperation:**

-   -   While ngspice and tclspice are quite known to the free eda community, there have not been much "networking" activity. As a result very few ngspice package exists and each distribution has its own compiled with the personal preferences of the package maintainer. We should contact package maintainer and plan with them the integration of ngspice in an organized way.
    -   Contact the people from the many OS distributions to plan integration of TCLspice in their packages.
    -   Contact the people TCLspice initiators were working with (list above) to restart development.

History:

Prior to year 2008 TCLspice was an independent project forked from ngspice. It is still hosted on sourceforge but it is not active anymore. The former maintainer of TCLspice, Stefan Jones, accepted to give me, Lionel Sainte Cluque, his chair as the project was no longer active. Paolo Nenzi, ngspice maintainer accepted to merge TCL functionality to ngspice source code as soon as it is stable.

Prior to 2008

*A crude copy and paste from TCLspice website:*

TclSpice is being actively developed and maintained by [MultiGiG ltd](http://www.multigig.com/) (as a by-product of a Clock-verification tool) and we try to act in concert with the following independent Open-Source EDA efforts to achieve (eventually) a complete freely available but industrial quality tool-set which work together seamlessly.

-   [Magic](http://bach.ece.jhu.edu/%7Etim/programs/magic/index.html) VLSI editor \[ tcl version \] (Tim Edwards).

-   [Xcircuit](http://xcircuit.ece.jhu.edu/index.html) schematic capture package \[ tcl version \] (Tim Edwards).

-   [Automatic Schematic Generation](http://www.ecs.gannon.edu/%7Efrezza/) (Multigig, Stephan Frezza).

-   [FastHenry](http://rleweb.mit.edu/vlsi/codes.htm) Inductance extractor (Jacob White).

-   [FastCap](http://rleweb.mit.edu/vlsi/codes.htm) Capacitance field solver (Jacob White).

-   OpenAccess VLSI database ([www.openeda.org](http://www.openeda.org/)).

-   [Octtools,](https://sourceforge.net/projects/octtools/) TimberWolf, place / router (Berkely (formerly)) (sourceforge.net).

-   [SpicePP](https://sourceforge.net/projects/tclspice/) preprocessor for berkeley spice3f5. It adds support for some structures commercial spice provide.

Some words from Stefan Jones:

The project was started around 2002 when I started working for Multigig. The then owner of Multigig, John Wood, was working on Tcl extensions for the magic vlsi program.

It was also considered a good thing to try to do the same for ngspice, bringing the same scripting benefits and a newer, easier to use GUI.

Also the old xspice simulator source code was found. It was also decided it would be a good idea to merge this also into ngspice.

Around 2003 the code was starting to diverse from ngspice with the two above features. I stopped producing diffs to ngspice as the ngspice people wanted the code to be kept separate. But I did make a cvs branch on the ngspice repository for the code so at least the two versions (ngspice and tclspice) could be merged easily.

Adrian Dawe was responsible for the TCL GUI code, also an employee at Multigig (which you said could not get to work I believe). He also setup the original tclspice website. I did the C-code bits.

Also around this time Stuart Brorson started working on spice. He finally fixed the remaining issues in the xspice to tclspice code merge and got it working properly.

I think soon after Dietmar Warning also became interested in tclspice and submitted a few patches.

But soon after that people seemed to switch to working on ngspice as it was the more active project (with Paolo Nenzi being more active)

Around 2004 Multigig switch to commercial spice tools. Thus work slowed/stopped on tclspice as it was no longer used much. Recently no-one uses tclspice anymore at Multigig so no work has been done other than to fix the occasion user submitted bug report.

Since 2008

In 2007 the function spicetoblt was released, enabling data to be passed easily from spice to TCL. This was the first indicator of TCLspice revival. In the early 2008th, TCL specific code have been copied and pasted into an ngspice CVS tarball, and the first set of TCLspice patches have been released. Then ngspice make process have been reviewed to handle libtool, required for generating libraries in a platform independent way.

