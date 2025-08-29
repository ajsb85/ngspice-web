# - [Documentation](./Docs.Html)

![NGSPICE](./images/nglogo.jpg) ![Mixed mode - mixed level circuit simulator - based on Berkeley's Spice3f5](./images/ngtext2.jpg) [](https://sourceforge.net/projects/ngspice)

- [Home](./index.html)
- [News](./news.html)
- [Screenshots](./screens.html)
- [Download](./download.html)
- [Documentation](./docs.html)
- [Extras/Options](./extras.html)
- [Applications](./applic.html)
- Development
- [Simulation Environments](./resources.html)
- [Quality](./quality.html)

Ngspice Development

- [Developers Info](./devel.html)

- [Bug Reports](./bugrep.html)

- [GIT Access](./gitaccess.html)

- [Docs for developers](./devdocs.html)

- [Mailing List Archives](./mlarch.html)

- [Releases Info](./relinfo.html)

- [Roadmap](./roadmap.html)

- [Writing Docs](./docwrite.html)

- ------------------------------------------------------------------------

- [Tests](./applic.html#test)

XSPICE in ngspice

- What is XSPICE ?
- [XSPICE and ngspice HOWTO](./xspicehowto.html)
- [XSPICE Usage](./xspiceusage.html)

KiCad/Eeschema as GUI for ngspice

- [Tutorial for Eeschema with ngspice](./ngspice-eeschema.html)

OSDI/OpenVAF for ngspice

- [What is OSDI/OpenVAF ?](./osdi.html)

GSS-TCAD

- [GSS](./gss.html)

TCLspice

- [What is TCLspice ?](./tclspice.html)
- [TCLspice users manual](./tclusers.html)
- [TCLspice by examples](./tclexamples.html)
- [Designer's note](./tclnotes.html)

XSPICE in Ngspice for behavioral analog and event driven modeling

XSPICE is an extension to the ngspice circuit simulator that provides the ability to use code modeling techniques to add new models. The XSPICE code model library distributed with ngspice contains over 40 functional blocks including summers, multipliers, integrators, memristor, magnetics models, limiters, S-domain transfer functions, digital gates, digital storage elements, and a generalized digital state-machine.

What is the XSPICE mixed-signal simulation capability ?

Digital functions are simulated in XSPICE through an embedded event-driven algorithm added to the Ngspice core. This algorithm is coordinated with the analog simulation algorithm to provide fast and accurate simulation of mixed-signal circuits and systems. The event-driven algorithm supports a "User-Defined Node" capability allowing additional event-driven data types to be defined and used. XSPICE comes with a 12-state digital data type as well as a user-defined node library that includes 'real' and 'integer' types useful in simulating sampled-data systems such as Digital Signal Processing algorithms.

XSPICE distribution in Ngspice

XSPICE is fully integrated into Ngspice. The code models are grouped into several code model libraries. These are shared libraries \*.cm (equivalent to \*.so or \*.dll), made during compilation with gcc.

Adding new models to the existing library or adding new libraries are straightforward. An example is given on the [XSPICE and ngspice HOWTO](./xspicehowto.html) page. Details are described in the [actual Ngspice manual](./docs/ngspice-manual.pdf).

XSPICE Licensing

XSPICE sources and documentation are in the public domain.

About the authors

XSPICE was developed by Fred Cox, Bill Kuhn, and their colleagues at the Georgia Tech Research Institute, a unit of the Georgia Institute of Technology.

Original XSPICE source code from Georgia Tech

Due to the fact that the Georgia Tech XSPICE web page is no longer on-line, the original C sources are made available [here](xspice/xspice-1-0.tar).

Relevant Links

- [XSPICE and Ngspice HOWTO](./xspicehowto.html): XSPICE code model generation starter and example.
- [Ngspice manual](./docs/ngspice-manual.pdf): The actual ngspice manual, XSPICE is covered in chapts. 12 and 25 - 29.
- [XSPICE docs](./devdocs.html): The original XSPICE documentation from Georgia Tech.
- [Spice OPUS](http://fides.fe.uni-lj.si/spice/xspice.html): XSPICE page for the Spice OPUS simulator.
- [ICAP/4](http://www.intusoft.com/articles/xspiceover.htm): XSPICE for the ICAP/4 simulator.

[](http://sourceforge.net) All text is available under the terms of the GNU Free Documentation License ![](./images/spice.jpg)
