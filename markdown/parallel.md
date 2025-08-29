



-   [Home](./index.html)
-   [Screenshots](./screens.html)
-   [Download](./download.html)
-   [Documentation](./docs.html)
-   Extras/Options
-   [Applications](./applic.html)
-   [Development](./devel.html)
-   [Simulation Environments](./resources.html)
-   [Quality](./quality.html)
-   [Contributions](./contrib.html)

XSPICE in ngspice

-   [What is XSPICE ?](./xspice.html)
-   [XSPICE and ngspice HOWTO](./xspicehowto.html)

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

Ngspice Parallel

The [shared ngspice option](./shared.html) introduces the capability to run several ngspice invocations in parallel in individual threads, with their simulation progress synchronized, including the exchange of current or voltage data between the different threads. A master program loads several ngspice library instances, and starts an individual ngspice thread in each instance. You have to divide your circuit into partitions and define their interconnections. Each ngspice thread loads one circuit partition and runs its simulation. The simulation progress is synchronized via a callback function, voltage or current data are exchanged according to the interface definition in another callback function.

Details of the shared ngspice API are documented in chapter 15 of the current [manual](https://ngspice.sourceforge.io/docs/ngspice-manual.pdf). A short description of the interface functions and the data structures used is given in the header file sharedspice.h, to be found in /src/include/ngspice. You may also have a look at the file /src/sharedspice.c, containing the function definitions.

A console master program, compilable with (LINUX, CYGWIN, MINGW t.b.d.) MS Visual Studio, is available as source code and MS Windows executables [here](https://ngspice.sourceforge.io/ngspice-shared-lib/ngspice_sync_win.7z), demonstrating an inverter chain, partitioned into three parts, being simulated in parallel in three ngspice shared libraries loaded dynamically. This is a very crude example of partitioning and synchronization, just touching the potential offered by the ngspice parallel approach.

The demonstrator thus is a call for adventurous ngspice developers to invest some effort into exploring the ngspice shared api and create improved control and synchronization flows for parallel simulation.

