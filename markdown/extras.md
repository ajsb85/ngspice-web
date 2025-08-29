# - [Documentation](./Docs.Html)

![NGSPICE](./images/nglogo.jpg) ![Mixed mode - mixed level circuit simulator - based on Berkeley's Spice3f5](./images/ngtext2.jpg) [](https://sourceforge.net/projects/ngspice)

- [Home](./index.html)
- [Screenshots](./screens.html)
- [Download](./download.html)
- [Documentation](./docs.html)
- [Tutorials](./tutorials.html)
- Extras/Options
- [Applications](./applic.html)
- [Development](./devel.html)
- [Simulation Environments](./resources.html)
- [Quality](./quality.html)

XSPICE in ngspice

- [What is XSPICE ?](./xspice.html)
- [XSPICE and ngspice HOWTO](./xspicehowto.html)

KiCad/Eeschema as GUI for ngspice

- [Tutorial for Eeschema with ngspice](./ngspice-eeschema.html)

Verilog-A compact device models with OSDI/OpenVAF

- [What is OSDI/OpenVAF ?](./osdi.html)

ngspice as shared library

- [Short Intro](./shared.html)
- [ngspice parallel](./parallel.html)

CUSPICE

- [CUSPICE Intro](./cuspice.html)

GSS-TCAD

- [GSS](./gss.html)

TCLspice

- [What is TCLspice ?](./tclspice.html)
- [TCLspice users manual](./tclusers.html)
- [TCLspice by examples](./tclexamples.html)
- [Designer's note](./tclnotes.html)

Ngspice Features, Extras and Options

Ngspice enhances the original spice3f5 in many ways. Here you will find a list and links to the various options. Typically details are not provided here, but are offered by the various links shown on the left or throughout the text. We also recommend to have a look at the [current ngspice manual](./docs/ngspice-manual.pdf).

Advanced Verilog-A compact device models

- The [OSDI/OpenVAF interface](./osdi.html) integrates Verilog-A compact device models into ngspice. No programming on the ngspice side is required, only your Verilog-A coded model! This interface enables modern models like PSP or FinFET model BSIM-CMG. A collection of such Verilog-A models is available at Dietmar Warning's [VA-Models](https://github.com/dwarning/VA-Models) page.

Mixed-signal co-simulation with digital Verilog circuit blocks

- Since version 42 ngspice offers the capability to integrate digital circuit blocks described with Verilog into its mixed-signal netlist for efficient co-simulation. The Verilog code is compiled with [Verilator](https://www.veripool.org/verilator/) into a shared library, which is then loaded by the new [code model](./xspice.html) d\_cosim. The I/O ports of the Verilog module are then directly accessible to the event based fast digital ngspice/XSPICE simulator, or may directly connect to analog parts of the ngspice netlist. A short [intro](./docs/others/Verilog-CoSim.pdf) is available as a pdf.

Mixed-signal co-simulation with digital C-coded circuit blocks

- Since version 42 ngspice offers the capability to integrate digital circuit blocks contained in C-coded independent processes into its mixed-signal netlist for efficient co-simulation. The C code is compiled with gcc. The external processes are started via the new [code model](./xspice.html) d\_process. The communication between ngspice/d\_process and the processes running is handled by pipes. The digital contents, interfaced to the event-based ngspice/XSPICE simulation, may also become part of an analog or mixed-signal ngspice netlist. A short [intro](./docs/others/c-process-CoSim.pdf) is available as a pdf. The d\_process code model originally has been developed by Uros Platise from Isotel, see his web page with a [motor controller example](http://www.isotel.eu/mixedsim/embedded/motorforce).

User defined device models

- The B-, E-, and G-sources (see [manual](./docs/ngspice-manual.pdf) chapt. 5) allow to generate voltages or currents which result from evaluating a mathematical expression, derived from node voltages, branch currents, parameters, and constants. Behavioral R, L, or C devices may depend on equations as well.
- The [XSPICE option](./xspice.html) integrates C language device models (code models) into ngspice. Behavioral modeling is strongly supported by various devices like amplifiers, filters, oscillators, integrators and others. Mixed signal analysis is sped up by event driven simulation of the digital sections. Various models already come along with ngspice to facilitating analog-digital co-simulation (see [manual](./docs/ngspice-manual.pdf) chapt. 8). The user may define his/her own analog, mixed, or digital devices and models (see chapt. 21-25, especially 24).

Programming ngspice

Various programming interface are available to add control flows to ngspice simulation or control ngspice from external programs or scripts.

- The ngspice scripting language (see manual chapter 13) allows to add control flows to a single simulation. You may run mathematical operations on simulation results, and start new simulations based on these data. Please have a look at the [control language tutorial](./ngspice-control-language-tutorial.html), at various scripts provided with the distribution, or at the examples from the manual. A [complete optimizer](#scripts) may be written in this language.
- Ngspice may be controlled via input, output fifos. Please see the manual at chapt. 12.12 for an example.
- The [shared ngspice option](./shared.html) is designed to compile ngspice as a shared library or dynamic link library, which may be loaded by any suitable application. This caller has full control over ngspice.
- The [tclspice option](./tclspice.html) is designed to add tcl scripting capability (including a graphics interface) to ngspice.
- The [ASCO optimizer](#ASCOo) is a nice example how to control ngspice from another program and how to run several ngspice instances in parallel on a multicore computer.

Ngspice as a shared library

Ngspice may be compiled as a shared library (\*.so or \*.dll). This will offer full control over the simulator from a calling process. See [this page](./shared.html) or the current manual at chapter 15 for more information.

Circuit optimization with ngspice

Several methods of using ngspice in circuit optimization have been devised by users.

- Optimization using a set of ngspice scripts. This is the [original web site](http://members.aon.at/fschmid7/page_2_1.html) by F. Schmidt. A slightly modified [set of scripts](https://ngspice.sourceforge.io/optimizers/ngspice-optimizer.7z) is available.
- Optimization using tcl as scripting language. An example is provided with the [tclspice option](./tclexamples.html). The manual at chapt. 16 has additional infos.
- Werner Hoch has developed a ngspice optimization procedure based on the ’differential evolution’ algorithm. On his [web page](http://www.h-renrew.de/h/python_spice/optimisation.html) he provides a Python script containing the control flow and algorithms.
- The [ASCO optimizer](http://asco.sourceforge.net/) by Joao Ramos, introduced the ’differential evolution’ algorithm for circuit optimization. An enhanced [version 0.4.7.1](https://ngspice.sourceforge.io/optimizers/asco-dist.7z), adding ngspice as a simulation engine, may be downloaded (including a MS Windows ngspice executable based on CVS). Chapt. 19.5 of the actual manual describes the ngspice specific integration issues and examples.

Statistical circuit analysis with ngspice

ngspice offers random numbers, as well as dedicated functions and scripts to vary device parameters for circuit simulation.

- Functions like AGAUSS are available for voltage and current sources (manual, chapt 18.2).
- Random voltage or current values may be generated directly (manual chapt. 4.1.8).
- Behavioral sources (B, E, G, R, L, C) include optionally generated random number values (manual chapt. 18.3).
- The ngspice scripting language uses the above mentioned functions and additional post processing functions (manual chapt. 22.4) for Monte Carlo analysis (manual chapt. 18.5). Example scripts are part of the ngspice distribution.
- Efficient noise voltage generators are part of the independent voltage and current sources (manual chapt. 4.1.7). Thermal noise, 1/f noise as well as random telegraph signal noise (RTS noise) are available. These sources are the basis for (time dependent) transient noise simulation with ngspice.

RF analysis with ngspice

High frequency simulation bridges the gap between high end scaled CMOS circuits and digital and analog applications. ngspice provides transistor models, e.g. BSIM4 for RF simulation as well as further tools. This field, however, ist still under development.

- Various transmission line models are available in ngspice and are decribed in chapt. 6 of the manual. They range from lossless, over lossy, distributed RC up to recursive convolution modelled single and coupled lines.
- You may 'measure' two port Scattering parameters of of your circuit and store them in a Touchstone file (see chapt. 13.8).
- ngspice incorporates a very efficient fast fourier analysis of output vectors (see chapt. 13.4.23).
- Periodic steady state analysis using a shooting method is under development. Test function are available (see chapt. 15.3.11).

TCAD and ngspice

Technology and device simulation, typically assembled in TCAD tools, may be integrated into ngspice. Thus individual devices may be simulated from scratch, being part of e.g. a transient ngspice simulation.

- An early adoption of this approach is the [cider option](https://www2.eecs.berkeley.edu/Pubs/TechRpts/1993/ERL-93-51.pdf), fully integrated into ngspice. Part of the documentation is available in the ngspice manual, chapt 26.

Please send your comments, suggestions, and corrections on this page to the [ngspice developers' list.](https://sourceforge.net/mailarchive/forum.php?forum_name=ngspice-devel)

 All text is available under the terms of the GNU Free Documentation License ![](./images/spice.jpg)
