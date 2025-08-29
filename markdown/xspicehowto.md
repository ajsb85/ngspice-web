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
- XSPICE and ngspice HOWTO
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

XSPICE in Ngspice howto

Ngspice and XSPICE installation

Please first of all check that you have installed Ngspice including the XSPICE option properly. The installation procedure has been described in the [Ngspice manual](./docs/ngspice-manual.pdf) at chapter 28.1 (for LINUX) or 28.2 (for MS Windows). Then run one or all of the examples to be found in the actual distribution or in git at [ngspice/examples/xspice](https://sourceforge.net/p/ngspice/ngspice/ci/master/tree/examples/xspice). To ensure that no hidden error is slipping through, you might add the line "set strict\_errorhandling" to either file spinit or .spiceinit.

Amplifier code model

Coming soon.

Memristor code model

A memristor subcircuit model, available from git at [ngspice/examples/memristor/memristor.sp](https://sourceforge.net/p/ngspice/ngspice/ci/master/tree/examples/memristor/memristor.sp) has been translated into an XSPICE code model. The source files are available from git at [ngspice/src/xspice/icm/xtradev/memristor](https://sourceforge.net/p/ngspice/ngspice/ci/master/tree/src/xspice/icm/xtradev/memristor/), an example circuit may be downloaded as [ngspice/examples/memristor/memristor\_x.sp](https://sourceforge.net/p/ngspice/ngspice/ci/master/tree/examples/memristor/memristor_x.sp). Some details of its usage are available from the [Ngspice manual](./docs/ngspice-manual.pdf) at chapter 8.2.29.

In the follwing you will find my ideas (h\_vogt) on the implementation of this model. Please consult the manual at chapter 8.1 and the model files cfunc.mod and ifspec.ifs from the actual ngspice git repository for further details.

- The model is added to the already existing code model library xtradev. So create a new directory /src/xspice/icm/xtradev/memristor/. Add the directory name 'memristor' to file /src/xspice/icm/xtradev/modpath.lst. Copy the two files cfunc.mod and ifspec.ifs from /icm/xtradev/capacitor/ to /icm/xtradev/memristor/, so to have a starting point.
- Edit /memristor/ifspec.ifs (see also manual chapter 24.6): Change the Spice\_Model\_Name to memristor. This will become the model name in the .model line. Replace the C\_Function\_Name cm\_capacitor by cm\_memristor. Select a suitable description. Select a port name (e.g. memris), to be used in cfunc.mod. We want to describe a resistor, so we have two terminals, which are input and output at the same time, therefore Direction: is inout. Our resistor has voltage as input and current as output, so we select Default\_Type: gd (differential voltage controlled current source), and no other than \[gd\] allowed. The parameter table lists the 6 model parameters rmin, rmax, rinit, alpha, beat, and vt, with their defaults, all being real values.
- Edit /memristor/cfunc.mod (see also manual chapter 27.7): Replace cm\_capacitor by cm\_memristor. This is the central function containing the model code. We have to rewrite it completely, when started with cm\_capacitor(). After defining some variables and getting some of the parameters by using the PARAM macro, we have to allocate memory for the state variable rval and initialize it to rinit. For transient simulation we then calculate the output according to the given model equations. The resistance relies in a specific fashion on the time integral of the input voltage (see argument to the cm\_analog\_integrate() function). A special consideration has to be given to the PARTIAL macro. Partial derivatives are required by the simulator to allow it to solve the non-linear equations that describe circuit behavior for analog nodes. We have I = V/Rval, so we have to find dI/dV = 1/Rval + V\*(d(1/Rval)/dV). As a first approximation we just use dI/dV = 1/Rval, but this shurely can be improved. DC and AC simulation are not defined for a memristor, because calculation of a dc bias point, without taking the time into acount, will not be possible. The model for now just returns rinit. Small signal noise modelling is not possible for the same reason, but has not been integrated into XSPICE anyway. You may try using transient noise instead (manual chapter 11.3.11).
- Compilation and installation of the new memristor code model is now a simple make, sudo make install ! Using the model is described in the manual, chapter at chapter 8.2.29.

On the right you see the output plot of memristor current versus voltage, as obtained from memristor\_x.sp. The exciting voltage is a sine with frequency increasing from tran1 over tran2 to tran3 by 20% per step.

The typical memristive behaviour is obvious: The v-i plane exhibits a pinched hysteresis loop, when driven by a bipolar periodic voltage. The loop shrinks towards a straight line with increasing excitation frequency.

Adding another memristor model is as simple as applying the procedure as described above. The main task is generating the C model code and (not so easily) obtaining the partial derivative dI/dV. Models with more than one state variable may be integrated as well.

Digital code model

Coming soon!

Mixed mode circuit: Phase-locked loop with analog devices and digital code models

A phase-locked loop circuit is available at git in directory [/ngspice/examples/xspice/pll/](https://sourceforge.net/p/ngspice/ngspice/ci/master/tree/examples/xspice/pll). The pll consists of several circuit blocks: a voltage controlled oscillator (vco), a digital frequency divider, the digital reference, the digital phase and frequency comparator, and the loop filter.

The analog vco is a 7 stage ring oscillator made of gain cells. As an (faster simulating) alternative you may use a controlled digital oscillator, readily available as a code model, whose frequency versus voltage characteristics has been made similar to the ring oscillator. The loop filter uses switched current sources as charge pump and a second order passive RC network. As an alternative there is available a CMOS transistor pair for charging and a 3rd order passive filter. The digital blocks are described by XSPICE code models, dac and adc bridges connect the digital and analog worlds.

The parameters of the loop filter are far from being optimized. You may use [Dean Banerjee's book](http://www.national.com/assets/en/boards/deansbook4.pdf) for a detailed instruction how to get best pll performance.

Mixed mode circuit: delta-sigma converter with analog devices and digital code models

A delta-sigma 9 bit converter circuit is available at git in directory [/ngspice/examples/xspice/delta-sigma/](https://sourceforge.net/p/ngspice/ngspice/ci/master/tree/examples/xspice/delta-sigma). The converter consists of several circuit blocks: a first order continuous time modulator (mod1), and a sinc filter and decimator.

The first order modulator consists of an integrator (xspice gain code model) and a latched comparator (B source and xspice D-latch) with feed back to the integrator input. This continuous time circuit also serves as an anti-aliasing filter. The sinc-filter/decimator is a binary 10 bit counter made of xspice J-K flip flops and some logic and latches. After N counts, determined by a divider code model, the counter contents is latched, the counter resetted.

This example is a very simple delta-sigma converter, not a 'productive' circuit, but demonstrates the cooperation of xspice code models (digital and analog) and analog devices in ngspice.

Debugging xspice code models in ngspice

The code model libraries are shared libraries (or dlls) loaded at runtime. Thus it is a little tricky to debug them during development.

There is some discussion about that in the net (see the [Multisim discussion forum](http://forums.ni.com/t5/Circuit-Design-Suite-Multisim/debugging-xspice-code-models/td-p/1049895)), where it is suggested to add a file for collecting debug output.

For developers using MS Visual Studio I have provided a Visual Studio project [xspice-gen-2019.7z](./experimental/xspice-gen-2019.7z) for download. It allows you to generate a code model in a library to be loaded into ngspice and to use the powerful debugger offered by MS Visual Studio in a step by step mode. Install the project into a directory of your choice and have a look at xspice-debug-howto.txt for further instructions.

Relevant Links

- [XSPICE and Ngspice introduction](./xspice.html): XSPICE code model support for Ngspice.
- [Ngspice manual](./docs/ngspice-manual.pdf): The actual ngspice manual, XSPICE is covered in chapts. 12 and 25 - 29.
- [Spice OPUS](http://fides.fe.uni-lj.si/spice/xspice.html): XSPICE page for the Spice OPUS simulator.
- [ICAP/4](http://www.intusoft.com/articles/xspiceover.htm): XSPICE for the ICAP/4 simulator.

[](http://sourceforge.net) All text is available under the terms of the GNU Free Documentation License ![](./images/spice.jpg)
