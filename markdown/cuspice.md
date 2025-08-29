



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

KiCad/Eeschema as GUI for ngspice

-   [Tutorial for Eeschema with ngspice](./ngspice-eeschema.html)

ngspice as shared library

-   [Short Intro](./shared.html)
-   [ngspice parallel](./parallel.html)

OSDI/OpenVAF for ngspice

-   [What is OSDI/OpenVAF ?](./osdi.html)

GSS-TCAD

-   [GSS](./gss.html)

TCLspice

-   [What is TCLspice ?](./tclspice.html)
-   [TCLspice users manual](./tclusers.html)
-   [TCLspice by examples](./tclexamples.html)
-   [Designer's note](./tclnotes.html)

Parallel processing with ngspice

The quest for simulating ever larger circuits poses a severe burden on the processing elements, requesting more and more computing power. Multi-core processors and GPU computing are the typical answers.

Ngspice supports multi-threading with OpenMP on multi-core CPUs. Device evaluation is run in parallel for specific devices (see the [current ngspice manual](./docs/ngspice-manual.pdf), chapter 12.10). The matrix solver of ngspice however is not parallelized. Thus a simulation speed-up of roughly a factor of two is possible.

The next step to speeding-up simulation is transferring the computational load to a GPU. Today's GPUs are real number crunchers and are important building blocks for high performance computing in super-computers, but also on the bench-top. This is done in CUSPICE, a development headed by Francesco Lannutti.

CUSPICE

CUSPICE exploits the massively parallel computing power of today's GPUs. Matrix building and calculations are done on the GPU, as well as the evaluation of the device code. Some features of this innovative approach are listed below:

-   Simulation speed enhancement for transistor loaded examples is significant (more than 3 times on transient simulation).
-   CUSPICE exploits the ngspice interfaces, it may be run similar to standard ngspice.
-   Currently only a limited subset of ngspice devices benefits from the CUSPICE acceleration approach, namely BSIM4v7, Capacitor, Self and Mutual Inductor, Current Source, Resistor and Voltage Source. All other devices run as well, but only in standard ngspice mode. XSPICE and CIDER are not (yet) supported.
-   The benefits of CUSPICE are experienced in large circuits only (a few thousand transistors minimum). This is due to the overhead required for coupling CPU and GPU.

Resources

-   The source code for CUSPICE, based on ngspice-27, is available from the ngspice git pages at the [CUSPICE+5 branch](https://sourceforge.net/p/ngspice/ngspice/ci/CUSPICE%2B5/tree/).
-   You will need a recent NVIDIA graphics card, including actual drivers. I (Holger) have used a (simple) GTX 750 and already see a significant acceleration. A Maxwell, Pascal or Volta card will be a good choice, especially if it is from the TESLA accelerator family (real "number crunchers" with excellent double precision compute capability).
-   If you compile yourself, you need the actual CUDA implementation, available from [NVIDIA](https://developer.nvidia.com/cuda-downloads).
-   Compile instructions for LINUX are given in the [CUSPICE user guide](https://ngspice.sourceforge.io/cuspice/CUSPICE_User_Guide.pdf). MS Windows users may apply the Visual Studio project file delivered with the sources. This has been tested with VS 2017 and CUDA 10.1.
-   For MS Windows a 64 bit compiled executable including the CUDA distributable dlls may be downloaded from the [experimental section](https://ngspice.sourceforge.io/download.html#exp1) of the ngspice download page. Of course you will need a suitable NVIDIA graphics card with actual drivers.

Literature

-   [CUSPICE user guide](https://ngspice.sourceforge.io/cuspice/CUSPICE_User_Guide.pdf) This short manual is somewhat outdated, but gives a quick reference to CUSPICE.
-   [CUSPICE: The revolutionary NGSPICE on CUDA Platforms](http://www.mos-ak.org/venice_2014/publications/T_2_Lannutti_MOS-AK_2014.pdf) Presentation by Francesco Lannutti at 12th MOS-AK ESSDERC/ESSCIRC Workshop September 26, 2014 Venice.
-   [What Does It Take to Accelerate SPICE on the GPU?](http://on-demand.gputechconf.com/gtc/2013/presentations/S3364-SPICE-Acceleration-on-GPUs.pdf) Presentation by M. Naumov, F. Lannutti e.a. at GPU Technology Conference 2013
-   [KLU sparse direct linear solver implementation into NGSPICE](http://ieeexplore.ieee.org/document/6226278/), Francesco Lannutti; Paolo Nenzi; Mauro Olivieri Proceedings of the 19th International Conference Mixed Design of Integrated Circuits and Systems - MIXDES 2012

Feedback

We have only a limited amount of feedback on CUSPICE so far. So we maintainers are interested in your reports!

