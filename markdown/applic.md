# - [Documentation](./Docs.Html)

![NGSPICE](./images/nglogo.jpg) ![Mixed mode - mixed level circuit simulator - based on Berkeley's Spice3f5](./images/ngtext2.jpg) [](https://sourceforge.net/projects/ngspice)

- [Home](./index.html)
- [News](./news.html)
- [Screenshots](https://sourceforge.net/projects/ngspice/)
- [Download](./download.html)
- [Documentation](./docs.html)
- [Tutorials](./tutorials.html)
- [Extras/Options](./extras.html)
- Applications
- [Development](./devel.html)
- [Simulation Environments](./resources.html)
- [Quality](./quality.html)

Ngspice Applications

- [Google/SkyWater Open Source PDK](applic.html#sky)
- [Delta-Sigma Converter](applic.html#dsc)
- [Memristor](applic.html#memr)
- [Example Circuits](applic.html#exam)
- [Device model parameters for simulation](applic.html#mparam)

\_\_\_\_\_ Applications \_\_\_\_\_

This section contains links to ngspice applications or short paragraphs describing the usage of ngspice. Its content will grow over time. You are welcome to contribute!

Google/SkyWater 130 nm CMOS PDK

ngspice supports the Open Source [Google/Skywater PDK](https://github.com/google/skywater-pdk) (process design kit) for the 130 nm CMOS process from [Skywater](https://www.skywatertechnology.com/). To install the PDK, a good choice is to follow the [installation procedure](http://opencircuitdesign.com/open_pdks/install.html) offered by Tim Edwards (Chapter "Prerequisites", steps 1 to 12). Design support is also available by Stefan Schippers' [XSCHEM](http://repo.hu/projects/xschem/index.html). See his [video](https://www.youtube.com/watch?v=jXmmxO8WG8s) for further installation instructions.

To successfully simulate with ngspice and the SkyWater PDK, at least ngspice-34 is required, however much better results (speed-up of at least a factor of 3, large circuits with 200k transistors have been tested) are available with the KLU solver in ngspice, available in our file download branch for [ngspice-43](https://sourceforge.net/projects/ngspice/files/ng-spice-rework/43/) . To enable KLU, compile ngspice with the configure flag `--enable-klu` . The MS Windows build from the distribution has KLU already enabled. KLU is now optionally selectable ('option klu' in .spiceinit), then replacing the venerable Sparse 1.3 matrix solver by the KLU method. It is still under test, but so far has yielded good results. Your user feedback is welcome!

You will have to create an initialization file .spiceinit (or alternatively called spice.rc) in your HOME directory. It should contain the following lines:
              * .spiceinit for use with Skywater PDK and ngspice KLU
              set ngbehavior=hsa     ; set compatibility for reading PDK libs
              set skywaterpdk        ; skip some checks for faster lib loading
              set ng_nomodcheck      ; don't check the model parameters
              set num_threads=8      ; CPU processor cores available
              option noinit          ; don't print operating point data
              option klu             ; select KLU as matrix solver
              optran 0 0 0 100p 2n 0 ; don't use dc operating point, but transient op

`set num_threads=8` should be set to the number of physical cores of the computer in use (here for example 8 cores), `set ngbehavior=hsa` will ensure HSPICE compatibility with some important and essential tweaks for the PDK, `set ng_nomodcheck` will suppress some unwanted warnings, `option noinit` will suppress the printing of the operating point results.

The calculation of the dc operating point, delivering the node voltage for starting the transient simulation, often has caused trouble (long duration, sometimes no convergence etc.). A new feature in ngspice is the **optran** method, calculating the operating point by a distinct transient simulation. The command `optran 0 0 0 100p 2n 0`, to be given in .spiceinit, does take care of this method. `0 0 0` denotes: no initial iteration, no gmin stepping, no source stepping, `100p 2n 0` then denotes: use an extra transient simulation with step size 100 ps and about 20 steps until 2 ns to set up all dc voltages, without explicitedly setting a voltage ramp. Only after a successful operating point calculation by optran the normal transient sim is started.

For MS Windows users, a pre-compiled executable of [ngspice-43](https://sourceforge.net/projects/ngspice/files/ng-spice-rework/43/ngspice-43_64.7z/download) (including KLU option) is available. Linux or macOS users might apply the compile scripts ./compile\_linux.sh or ./compile\_macos\_gcc.sh from the ngspice top directory of the [ngspice-43 tarball](https://sourceforge.net/projects/ngspice/files/ng-spice-rework/43/ngspice-43.tar.gz/download) to compile an OS specific executable.

After having installed the PDK, you may run the [ISCAS85 SkyWater example](./tests/skywater-examples.7z). Please edit the ngspice input files for a simple inverter and the ISCAS85 C7552\_ann and add the correct path to your PDK installation. Simulating the C7552\_ann will take a few minutes because it contains 15000 MOS transistors (BSIM4v5 model) and 82000 passives (R and C). Overall speedup of the c7552 simulation is a factor of two, the plain transient simulation time is reduced by a factor of three, when using KLU. And it is now possible to run simulations with 200k transistors. Setup time may be reduced (for experimental purposes) by directly including the model file with .inc, instead of using .lib (see the netlist file).

Please see also [SKY130 installation](https://classes.up-microlab.org/index.php?title=SKY130_Models) for a detailed description.

IHP Open Source PDK

In an ongoing development [IHP](https://www.ihp-microelectronics.com/) is working towards an Open Source PDK for its 130 nm SG13G2 BiCMOS process. Data are available as [IHP Open Source PDK](https://github.com/IHP-GmbH/IHP-Open-PDK). The process offers bipolar devices with exceptional performance with fT/fmax = 350/450 GHz. ngspice has been selected as the preferred analog simulator. Again here is the [ISCAS85 c7552\_ann circuit](./tests/IHP-c7552_ann.7z) for running a simulation comparison using the IHP PDK. You will need to compile the PSP103.6 nqs model with [OpenVAF](https://ngspice.sourceforge.io/osdi.html) and load it into ngspice (see chapter 9 of the [ngspice manual](https://sourceforge.net/projects/ngspice/files/ng-spice-rework/43/ngspice-43-manual.pdf/download)). Bipolar transistors are modelled with the native ngspice VBIC model.

Google/GlobalFoundries GF180MCU Open Source PDK

Another Open Source PDK has been published in 2022 as the [Google/GlobalFoundries PDK](https://github.com/google/gf180mcu-pdk/) for the 180 nm GF180MCU CMOS process from [GF](https://gf.com/). ngspice is supported with parameters for native and high voltrage devices as an analog simulator.

KiCad/ngspice example circuits

[KiCad](https://KiCad.org) is a powerful frontend to ngspice. It allows schematic entry of your circuit and control of the simulator. More than 35 [examples](https://forum.kicad.info/t/simulation-examples-for-eeschema-ngspice/34443) are presented at the KiCad info forum, ranging from audio power amplifiers over power supplies (linear and SMPS) and some miscellanious applications (CMOS, tubes, other).

Phase locked loop

[Phase-locked loop](./xspicehowto.html#pll)

Delta-Sigma D/A Converter

[Delta-sigma converter](./xspicehowto.html#dsc)

Memristor

[Memristor](./xspicehowto.html#memr)

Example circuits

The ngspice distribution provides a lot of [example circuits](https://sourceforge.net/p/ngspice/ngspice/ci/master/tree/examples). These consist of netlists and models and cover various aspects of ngspice analog, digital and mixed signal simulation. They are also a very good study source if you are interested in the ngspice control language.

Device model parameters for simulation

For simulation you need as input the netlist, device model parameters, simulation commands, and out commands. The ngspice distribution does not provide such model parameters, but you may find many of them either in the web or on this web site. The [Model Parameter Page](./modelparams.html) does offer some further info and links.

 All text is available under the terms of the GNU Free Documentation License ![](./images/spice.jpg)
