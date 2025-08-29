



-   [Home](./index.html)
-   [Screenshots](./screens.html)
-   [Download](./download.html)
-   [Documentation](./docs.html)
-   [Extras/Options](./extras.html)
-   [Applications](./applic.html)
-   [Development](./devel.html)
-   [Simulation Environments](./resources.html)
-   [Quality](./quality.html)
-   [Contributions](./contrib.html)

XSPICE in ngspice

-   [What is XSPICE ?](./xspice.html)
-   [XSPICE and ngspice HOWTO](./xspicehowto.html)

KiCad/Eeschema as GUI for ngspice

-   [Tutorial for Eeschema with ngspice](./ngspice-eeschema.html)

ngspice as shared library

-   [Short Intro](./shared.html)
-   [ngspice parallel](./parallel.html)

OSDI/OpenVAF for ngspice

-   [What is OSDI/OpenVAF ?](./osdi.html)
-   [ADMS and ngspice HOWTO](./admshowto.html)

GSS-TCAD

-   [GSS](./gss.html)

TCLspice

-   [What is TCLspice ?](./tclspice.html)
-   [TCLspice users manual](./tclusers.html)
-   [TCLspice by examples](./tclexamples.html)
-   [Designer's note](./tclnotes.html)

Ngspice as a Shared Library

As a new option ngspice may be compiled as a shared library (\*.so in LINUX, \*.dll in MS Windows).

A controlling application may acquire complete control over ngspice after loading the shared lib either during compilation/linking or dynamically at runtime.

The shared module offers an interface which exports functions controlling the simulator and callback functions for feedback.

So you may send an input "file" with a netlist to ngspice, start the simulation in a separate thread, read back simulation data at each time point, stop the simulator depending on some condition, alter device or model parameters and then resume the simulation.

The calling process may offer a graphical user interface which you may develop and optimize without a need to alter the ngspice source code.

Details of the shared ngspice API are documented in chapter 19 of the actual [manual](https://ngspice.sourceforge.io/docs/ngspice-manual.pdf). A short description of the interface functions and the data structures used is given in the header file sharedspice.h, to be found in /src/include/ngspice. You may also have a look at the file /src/sharedspice.c, containing the function definitions.

Ngspice Shared Library Interfacing and Integration

Interfaces of ngspice.dll or ngspice.so are available for various languages. You may download sample programs for calling ngspice written in Turbo Delphi or Lazarus (Pascal variants) and C language in the download section below. KiCad uses a [C++ interface](https://git.launchpad.net/kicad/tree/eeschema/sim). (see file ngspice.cpp). A [free basic interface](http://www.freebasic.net/forum/viewtopic.php?t=24956) to ngspice has been published. A [Ruby interface](https://github.com/shimat/ngspicer) to shared ngspice is available, as well as an [interface with Octave](https://sourceforge.net/p/octave/ngspice/ci/default/tree/), and here [another interface with Octave](https://www.dsprelated.com/showarticle/707.php), calling the ngspice library. Fortran programs may make use of ngspice, as shown in this [Fortran interface](https://github.com/OpenSEMBA/ngspice_fortran_interface). [PySpice](https://github.com/PySpice-org/PySpice) interfaces shared ngspice with Python. There is [paprika](https://github.com/ua-kxie/paprika), offering Rust binding, and we have [gongs](https://github.com/Patrick-Varela/gongs), a Go package to interface shared ngspice.

Ngspice Shared Library Downloads

Three executables (coming with source code) serve as examples for controlling ngspice. These are not meant to be "productive" programs, but just give some commented example usages of the interface.

ng\_start64.exe is a MS Windows application loadinga 64 bit ngspice.dll dynamically. All functions and callbacks of the interface are assessed. The [source code](https://ngspice.sourceforge.io/ngspice-shared-lib/ng_start64_sources.7z) is compiled with [Lazarus](http://www.lazarus-ide.org/), an Open Source Delphi compatible cross-platform IDE for Rapid Application Development with Pascal. The binaries compiled for 64 Bit are [here](https://ngspice.sourceforge.io/ngspice-shared-lib/ng_start64_binaries.7z), including ngspice.dll, codemodels and some example input files.

Two C language console applications, compilable with LINUX, CYGWIN, MINGW or MS Visual Studio, are available [as source code](https://ngspice.sourceforge.io/ngspice-shared-lib/ngspice_cb.7z), demonstrating either statical linking or linking shared ngspice at runtime. A simple feedback loop is shown in tests 3 and 4, where a device parameter is changed upon having an output vector value crossing a limit.

