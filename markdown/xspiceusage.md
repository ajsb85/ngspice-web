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

- [What is XSPICE ?](./xspice.html)
- [XSPICE and ngspice HOWTO](./xspicehowto.html)
- XSPICE Usage

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

XSPICE short intro

The XSPICE extension to the ngspice circuit simulator provides code modeling techniques to add new analog and digital models. Analog functions may be added to the netlist like any other hard coded analog model. Digital functions, if added to the netlist, are simulated in XSPICE through an embedded event-driven algorithm added to the Ngspice core. This algorithm is coordinated with the analog simulation algorithm to provide fast and accurate simulation of mixed-signal circuits and systems.

XSPICE usage by third parties

XSPICE has been used by developers outside of the ngspice branches. This page serves to provide links to these activities. If you are aware of other XSPICE usage, please let me know.

The first link describes a complete design flow using only open source tools, including ngspice for mixed signal simulation.

The next link describes an accurate simulator of the 8-bit AVR microcontrollers which has been integrated into ngspice

In his [PhD work](https://depositonce.tu-berlin.de/items/9a951c49-99d4-45d3-98fe-c80ef629d12c) Stephan Thiel has developed more than 200 code models for supporting signal processing simulation with XSPICE or ngspice. The code model sources, a setup for compilation using Visual Studio and executable dlls are available [**here**](https://ngspice.sourceforge.io/experimental/xspice-vs2019-signal-processing-dist.7z) (ca. 6.7 MB). Unfortunately there is not much documentation, so please have a look at the code model titles and their source code.

Relevant general links

- [XSPICE and Ngspice HOWTO](./xspicehowto.html): XSPICE code model generation starter and example.
- [Ngspice manual](./docs/ngspice-manual.pdf): The actual ngspice manual, XSPICE is covered in chapts. 12 and 25 - 29.
- [XSPICE docs](./devdocs.html): The original XSPICE documentation from Georgia Tech.
- [Spice OPUS](https://fides.fe.uni-lj.si/spice/xspice.html): XSPICE page for the Spice OPUS simulator.
- [ICAP/4](http://www.intusoft.com/articles/xspiceover.htm): XSPICE for the ICAP/4 simulator.

[](http://sourceforge.net) All text is available under the terms of the GNU Free Documentation License ![](./images/spice.jpg)
