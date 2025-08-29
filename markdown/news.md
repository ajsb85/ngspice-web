# - [Documentation](./Docs.Html)

![NGSPICE](../images/nglogo.jpg) ![Mixed mode - mixed level circuit simulator - based on Berkeley's Spice3f5](../images/ngtext2.jpg) [](https://sourceforge.net/projects/ngspice)

- [Home](./index.html)
- News
- [Screenshots](https://sourceforge.net/projects/ngspice/)
- [Download](./download.html)
- [Documentation](./docs.html)
- [Tutorials](./tutorials.html)
- [Extras/Options](./extras.html)
- [Applications](./applic.html)
- [Development](./devel.html)
- [Simulation Environments](./resources.html)
- [Quality](./quality.html)

Ngspice News

- [News](#)

- [What is ngspice ?](presentation.html)

- [Features, Extras & Options](extras.html)

- [F.A.Q.](faq.html)

- [Tutorials](tutorials.html)

- ------------------------------------------------------------------------

- [Sourceforge Developer Pages](https://sourceforge.net/projects/ngspice/)

NEWS

ngspice release 44, December 29th, 2024

A new ngspice release is available. ngspice-44 is offering several enhancements and bug fixes.

- Code model d\_cosim supports Icarus Verilog for mixed signal simulation.
- The VBIC bipolar model has been further updated.
- EKV3 is available as a shared library.
- More error messages updated, trying to find the location of the error.
- New functions exported in the shared ngspice API for reset or avoiding to read .spiceinit.

For a list of additional new features please have a look at the NEWS feature in the ngspice tarball. In ngspice-44 in addition several bugs reported by users have been removed.

ngspice release 43, July 14th, 2024

A new ngspice release is available. ngspice-43 is offering several enhancements and bug fixes.

- Configure options KLU, OSDI, readline, OpenMP, and XSPICE have been defined as standard.
- The VBIC bipolar model has bee significantly updated.
- JFET and diode models have been updated as well.
- Improved error message, trying to find the location of the error.

For a list of additional new features please have a look at the NEWS feature in the ngspice tarball. In ngspice-43 in addition several bugs reported by users have been removed.

ngspice release 42, December 27th, 2023

A new ngspice release is available. ngspice-42 is offering major enhancements and bug fixes.

- KLU matrix solver has been added to the venerable Sparse 1.3
- Verilog-A device models (copiled by OpenVAF) now support small signal noise simulation.
- Digital C coded circuit blocks may be read by the code model d\_process.
- Verilog (digital) circuits, compiled with Verilator, may be read into ngspice by new code model d\_cosim.

For a list of additional new features please have a look at the NEWS feature in the ngspice tarball. In ngspice-42 in addition more issues leading to simulator crashes upon faulty inputs have been removed.

ngspice release 41, August 16th, 2023

A new ngspice release is available. ngspice-41 is offering a lot of enhancements and bug fixes.

- Analog node changes in VCD file output.
- Read Touchstone file for S parameter simulation.
- Completely renewed XSPICE d\_osc code model.
- Updates to commands setscale, compose, eprvcd, iplot, and listing.
- Option FREQ for E and G sources.
- New dot command .libsave.

For a list of additional new features please have a look at the NEWS feature in the ngspice tarball. ngspice-41 is also a bug-fix release. More issues leading to simulator crashes upon faulty inputs have been removed.

ngspice release 40, April 1st, 2023

A new ngspice release is available. ngspice-40 is offering some enhancements and bug fixes.

- Extended SOA for VBIC bipolar model.
- Supports atto scale factor.
- Inertial delay to all basic digital code models, including U devices.
- For a list of additional new features please have a look at the NEWS feature in the ngspice tarball.
- ngspice-40 is predominantly a bug-fix release. Several issues leading to simulator crashes upon faulty inputs have been removed.

ngspice release 39, January 31st, 2023

A new ngspice release is available. ngspice-39 is offering two major code enhancements and new features.

- ngspice now offers simulation with Verilog-A models, using its new OSDI interface and the OpenVAF model compiler. This enhancement enables access to all modern compact models for short channel MOS, FinFets, double gate transistors, SiGe bipolars, and III-V HEMTs.
- ngspice now supports nearly all features of digital PSPICE compatible U devices (instances). Therefore we now may simulate a wealth of digital devices. These are translated into internal XSPICE event models, with very fast simulation.
- For a list of additional new features please have a look at the NEWS feature in the ngspice tarball.
- Patches: Many developer and user provided patches and bug fixes have been applied.

ngspice release 38, October 29th, 2022

A new ngspice release is available. ngspice-38 is offering several new features and code enhancements.

- New features: .probe command updated (current and power measurements). Support of digital devices with U-instance models (PSPICE compatible). Automatic generation of A/D and D/A bridging interfaces, when mixed signal simulation (combining analog and event-based digital) is used. Update to pow() function (LTSPICE compatible). For a list of all new features please have a look at the NEWS feature in the ngspice tarball.
- Patches: Many developer and user provided patches and bug fixes have been applied.

ngspice release 37, May 19th, 2022

A new ngspice release is available. ngspice-37 is offering several new features and code enhancements.

- New features: .probe command to measure currents, differential potentials or device power dissipation. S-parameter simulation with command .sp, command 'esave' to save only relevant digital nodes, substantail speed-up of plotting under MS Windows, flags 'alle' and 'digitop' to the plot command, reduce XSPICE memory consumption dramatically For a list of all new features please have a look at the NEWS feature in the ngspice tarball.
- Patches: Many developer and user provided patches and bug fixes have been applied. Other bugs and some memory leaks have been removed as well.

ngspice release 36, January 1st, 2022

A new ngspice release is available. ngspice-36 is offering several new features and code enhancements.

- New features: .probe command to measure currents or differential potentials. x/y contour plots for 2d Cider simulation, new function integ (integration), command 'wrnodev' to print matrix RHS as .ic = V(node\_xx), Transient operating point, more SOA (safe operating area) parameters on more devices. For a list of all new features please have a look at the NEWS feature in the ngspice tarball.
- Patches: Many developer and user provided patches and bug fixes have been applied. Other bugs and some memory leaks have been removed as well.

ngspice release 35, August 8th, 2021

A new ngspice release is available. ngspice-35 is offering several new features and code enhancements.

- New features: Plotting with SVG file format. Geometry scaling for diode level 3, diode self heating model, option Cshunt for capacitors node-to-ground. Analog delay code model. PSP model update for NMOS, PMOS. Read 4k7 in addition to 4.7k. For a list of all new features please have a look at the NEWS feature in the ngspice tarball.
- Patches: Many developer and user provided patches and bug fixes have been applied. Other bugs and some memory leaks have been removed as well.

ngspice release 34, January 31st, 2021

A new ngspice release is available. ngspice-34 is offering several new features and code enhancements.

- New features: High speed bipolar model HICUM2.4 has been added. Compatibility with Open Source Google/Skywater PDK has been improved. KiCad compliance has been improved, compatibility to PSPICE device models as well. For a list of all new features please have a look at the NEWS feature in the ngspice tarball.
- Patches: Many developer and user provided patches and bug fixes have been applied. Other bugs and some memory leaks have been removed as well.

ngspice release 33, October 18th, 2020

A new ngspice release is available. ngspice-33 is offering several new features and code enhancements.

- New features: Further improved VDMOS power transistor model. Improved JFET model (temperature model) and bipolar model (Kull quasi-saturation model). New commands, new code models, compatibility switches for KiCad and Spectre have been added. KiCad compliance has been improved. For a list of all new features please have a look at the NEWS feature in the ngspice tarball.
- Patches: Many developer and user provided patches and bug fixes have been applied. Other bugs and some memory leaks have been removed as well.

ngspice release 32, May 5th, 2020

A new ngspice release is available. ngspice-32 is offering several new features and code enhancements.

- New features: Improved VDMOS power transistor model including self-heating. ngspice now understands UNICODE: file and directory names as well as texts for labeling images may use any valid UNICODE character. Internally ngspice uses utf-8 string encoding and UTF-16 for Windows I/O. The graphics output on native Windows, Postscript and X11 has been updated considerably, concerning color and linewidth selection and fonts for labeling. New commands have been added. Error messages have been improved, several crash scenarios caused by input errors have been removed. For a list of all new features please have a look at the NEWS feature in the ngspice tarball.
- Patches: More than 30 developer and user provided patches and bug fixes have been applied. Other bugs and some memory leaks have been removed as well.

ngspice release 31, September 22nd, 2019

A new ngspice release is available. ngspice-31 is another bug-fix release, but also offers several new features.

- Patches: More than 30 developer and user provided patches have been applied. Bug fixes: 6 bugs that users have reported on the ngspice bug tracker have been fixed. Other bugs and some memory leaks have been removed as well.
- New features: Improved VBIC model including self-heating; variable 'nostepsizelimit' to speed up certain simulations; Windows GUI has become more responsive; Windows history buffer is re-written; new command 'setcs'; vectors lin-tstart, lin-tstop, and lin-tstep enable the 'linearize' command to cut out a section of a result vector.

ngspice release 30, January 1st, 2019

A new ngspice release is available. ngspice-30 is foremost a bug-fix release, but also offers several new features.

- Bug fixes: 15 bugs that users have reported on the ngspice bug tracker have been fixed. Other bugs and some memory leaks have been removed as well.
- New features: The VDMOS model has been overhauled and updated. A new variable 'controlswait' allows shifting the command sequence in shared ngspice to after the simulation.
- Documentation: The manual making procedure has been setup anew. A html manual may be generated in addition to the pdf version.

ngspice release 29, October 27th, 2018

A new ngspice release is available. ngspice-29 offers several new features:

- Bug fixes: Small bugs fixed, lots of memory leaks removed.
- New features: Enhanced compatibility modes with PSPICE (.include files or the complete netlist), LTSPICE compatibility started, not yet complete. New 'sidiode' simple diode model, new command 'setseed', new internal variables 'no\_auto\_gnd' and 'inputdir'. Environmental variable SOURCE\_DATE\_EPOCH is supported.
- Documentation: Updated pdf manual and other documentation.

ngspice release 28, June 1st, 2018

A new ngspice release is published. ngspice-28 offers several new features:

- License: All licenses involved are DFSG compatible.
- Bug fixes: Small bugs fixed, memory leaks removed, code reorganized to improve its readability and safety.
- New features: new VDMOS power MOS model, ngspice reads device libs with PSPICE syntax, old apps like ngnutmeg are made only upon user reqest, new commands 'mc\_source' and 'alterparam', instance parameters may be added to the .model line, new variable 'sim\_status', ngspice shared library supports XSPICE digital event data over its interface, pkg-config added .
- Documentation: Updated pdf manual and other documentation.

ngspice release 27, September 17th, 2017

After more than three years of quiet but continuous development a new release is due. Many new features have been added to ngspice-27, improving its applicability and compatibility.

- Bug fixes: Several small bugs removed, improved code compliance.
- New features: XSPICE 2D and 3D table models, digital LUT models; updates to HiSIM and BSIM4 models; new commands 'edisplay' and 'eprvcd'; improved command 'wrdata'; relative cm paths for shared ngspice; OpenMP support for BSIM4.5 and bsim3v3.24 models; new function stddev; new variables 'interactive' 'sqrnoise', and 'batchmode'; improved support for VS2015/2017 compilation, including the code models; new option 'savecurrents'.
- Documentation: Updated pdf manual and other documentation.

CUSPICE Launched, April 28th, 2014

CUSPICE is the revolutionary ngspice on CUDA platforms. The ngspice simulator has been modified to exploit the parallelism offered by CUDA platforms. The code has been uploaded in the source repository. CUSPICE now supports only a small (growing) set of ngspice devices: BSIM4v7, Capacitor, Self and Mutual Inductor, Current Source, Resistor and Voltage Source.

CUSPICE requires an NVIDIA video card with Fermi (or newer) architecture and a working CUDA enviroment installation.

CUSPICE speeds up model evaluation, circuit and right hand side creation steps up to 3x. Interested testers of the code should read the [user guide](cuspice/CUSPICE_User_Guide.pdf) and have a look at the [CUSPICE](./cuspice.html) web page. Feedbacks from testers of this code are appreciated!

ngspice release 26, January 12th, 2014

Several new features have been added to ngspice-26, improving its applicability and compatibility.

- Bug fixes: Many small bugs removed, handling of libraries updated, improved code compliance.
- New features: fft command optionally using fftw3; new functions nint, asinh, acosh, atanh, pwr; 'temper' in behavioural devices; check for soa (safe operating area); shared ngspice as a shared object or dynamic link library; hash table to parsing the netlist; basic .if/.else block; Area Calculation Method (ACM) for BSIM3.3.0; \`tc1', \`tc2' instance parameters.
- Documentation: Updated pdf manual and other documentation.

ngspice release 25, January 3rd, 2013

As always: new features have been added to ngspice-25, improving its applicability and stability.

- Bug fixes: Memory leaks removed, especially for several XSPICE devices, improved code compliance.
- New features: CMC model qa check for actual BSIM and hisim devices; additional parameters accessible in bsim3; new or updated commands: 'snsave', 'snload'; new code model 'memristor'; hisim models updated; 'measure' speed enhanced; port for Mac OS X.
- Documentation: Updated pdf manual and other documentation.

ngspice release 24, January 31st, 2012

More features have been added to ngspice in this update, improving ngspice applicability and compatibility.

- Compatibility: Extended syntax for behavioral E and G sources.
- Bug fixes: Enhanced stability for several device models, code compliance.
- New features: New or updated commands: wrdata, remcirc, altermod, inventory, devhelp, reset; new functions ceil, floor, cph; new code model 'filesource'; 64 Bit compilation capability with MINGW, MS Visual Studio, LINUX.
- Documentation: Updated pdf manual and other documentation.

ngspice release 23, June 5th, 2011

More features have been added to ngspice in this update, improving ngspice applicability.

- Compatibility: More code cleanup considerably reduces compiler warnings.
- New devices: HiSIM2 and HiSIM\_HV models from Hiroshima University have been added.
- New features: Ngspice builds in a separate directory (e.g. in ng-spice-rework/release); transient noise simulation, a random voltage generator option trrandom and random telegraph noise added to independent voltage and current sources; command wrs2p to write a s-parameter file using Touchstone vers. 1 format.
- Documentation: Updated pdf manual and other documentation.

ngspice release 22, Sept 26th, 2010

More features have been added to ngspice in this update, improving ngspice compatibility, speed, and stability.

- Compatibility: An extensive code cleanup considerably reduces compiler warnings.
- Speed: OpenMP multicore support for BSIM3, BSIM4, and BSIMSOI4 is now available, speeding up a transistor loaded simulation by a factor of two.
- New features: Reinstate {$var} expansion in interactive interpreter; .TITLE line added; update to 'spectrum' script; par('expression') in .four, .plot, .print, .meas, .save commands; command 'option' for use in spinit, .spiceinit, and in scripts; adms procedure updated; new random number generator, new random functions sunif() and sgauss(), and scripts for Monte Carlo simulations, new plot vectors allv, alli, ally.
- Documentation: Updated pdf manual and other documentation.

ngspice release 21, June 21st, 2010

This update is another cornerstone in improving ngspice compatibility, stability and reliability.

- Compatibility: Added compatibility mode for dealing with other simulators.
- Devices: BSIMSOI: update to version 4.3.1. Transmission lines were updated with txl and cpl from kspice. B sources now include PWL function handling, with variables "HERTZ", "time" and "temper" and Ternary function added. E and G sources, as well as R, C, L devices may contain expressions as value. PWL sources have got a repeat parameter (r=value) and a delay parameter (td=value).
- Interface: Added "-p" option for running in "pipe mode". Improved measures: added "meas" command in control section. Added "wrdata" command for tabulated data out.
- Documentation: Updated documentation available in pdf as a separate package.

ngspice release 20, November 16th, 2009

Ngspice release 20 is the second release of the simulator in 2009.

- Fixes: model names starting with a number (1n4001) are now correctly parsed. The .global command has been reinstated (it was previously disabled) and error messages now display the corresponding line numberin the input deck.
- New Features: .measure command for transient, ac and dc analyses (still not complete, e.g. DERIV is missing).
- Devices: Updated BISM4 model to revision 4.6.5. Added PWL (PieceWise Linear) functionality for B (arbitrary generator) sources.

ngspice release 19, April 23rd, 2009

Ngspice release 19 came early after release 18. It reveals an important work in compile scripts, many bug fixes in memory management, interface, and work in device models.

- Compile scripts: tclspice and ADMS compiling fixes. Architecture compiling fixes for SunOS, MS Visual Studio, MINGW, Cygwin.
- Memory management: fixed memory leaks, modifies memory management for MS Windos, integration of espice bugfixes and enhancements, bug fixes in plots and cli interface.
- Rework of BSim models, integration of EPFL-EKV model V2.63, ADMS models mextram, hicum0, hicum2.

ngspice release 18, December 1st, 2008

After a long periode of silence, NGspice team is proud to announce you that ng-spice-rework-18 will be released the 1st of december. This is an incredible gift, you can offer your collegues, your friends or your familly. A lot of work have been done since August, 30th 2005: Bug fixes and new features. Ngspice gets every release closer from a state of the art simulator. Road is long, but release 18 is a step more, and overall it is a promising step. The main interest of ngspice it that it makes converge the many divergent spice implementations, by collecting papers, and looking at the functionalities of other spice branches. Some features have been added at netlist level, as parametrical netlists and .lib statement. Ngspice is now one of most versatile spice implementation as it can deal with a very large set of netlists functionalities.

- A special thanks to Phil Bakers, for contributing numparam, the parametrical netlist. and .lib statement
- Holger Vogt for windows integration and fft command on spice vectors
- Gong Ding for the interface with GSS-TCAD semiconductor simulator.
- Lionel Sainte Cluque from bringing back tclspice in ngspice.
- Thanks to Paolo Nenzi, Dietmar Warning, Steven Borley for their huge contribution.

I would say that the importance of release 18 is not only the features it provides, but the basis it makes for futur developpement of ngspice. Ngspice is in the short list of the high quality open source circuit simulation programs. For this reason it has been integrated with little or great success in many EDA workflows. Nevertheless, I think that better integration can be achieved, and open source EDA suites are, for the moment, and I hope this will change, of a much lower quality that proprietary ones. It lacks features, and it lacks integration between tools. NGspice make a step toward others open source EDA softwares by clarifying its license and providing tclspice. Tclspice, released under GNU LGPL, is a library loadable in a tcl interpreter that gives acces to spice simulation through tcl commands. I hope that soon, some nice tcl interfaces can bundle schematic editors, spice pre/post processors, BOM databases, and so on.

A reflexion has been undertaken on the evolutions that can be made. Many big features are planned. I hope these project will take form soon. As an open source project, you are welcome to contribute. Please, visit the [Developement](./devel.html) and [Roadmap pages](./roadmap.html) .

Recent Releases

Release Date

ngspice-44

29-December-2024

ngspice-43

14-July-2024

ngspice-42

27-Dec-2023

ngspice-41

16-Aug-2023

 All text is available under the terms of the GNU Free Documentation License ![](../images/spice.jpg)
