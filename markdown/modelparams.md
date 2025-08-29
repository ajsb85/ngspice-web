# - [Documentation](./Docs.Html)

![NGSPICE](../images/nglogo.jpg) ![Mixed mode - mixed level circuit simulator - based on Berkeley's Spice3f5](../images/ngtext2.jpg) [](https://sourceforge.net/projects/ngspice)

- [Home](./index.html)
- [News](./news.html)
- [Screenshots](https://sourceforge.net/projects/ngspice/)
- [Download](./download.html)
- [Documentation](./docs.html)
- [Extras/Options](./extras.html)
- [Applications](./applic.html)
- [Development](./devel.html)
- [Simulation Environments](./resources.html)
- [Quality](./quality.html)

Models and model parameters for ngspice

- [News](index.html)

- [What is ngspice ?](presentation.html)

- [Features, Extras & Options](extras.html)

- [F.A.Q.](faq.html)

- [Tutorials](tutorials.html)

- ------------------------------------------------------------------------

- [Sourceforge Developer Pages](https://sourceforge.net/projects/ngspice/)

Models for ngspice

For simulation you need as input to ngspice your circuit (aka the netlist), device models (or model parameters), simulation commands, and output commands. The ngspice distribution does offer some default model parameters only for the basic, intrinsic devices. Device makers, vendors and modeling specialists however provide models, and you may find many of them in the two collections offered below, or in the web (see links below, or search for a specific device or use a general search term like 'get SPICE models'). Generally PSPICE, HSPICE, and (many) LTSPICE models are compatible to ngspice. Sometimes models by commercial vendors are encrypted. These cannot be used by open source ngspice. Some hints on how to make models and model parameters available to ngspice are given [below](#howto).

Model and model parameter collections:

A [basic model parameter set](./model-parameters/basic_models.7z) is available as a starter or for a quick analysis. This set is by far not complete, but offers examples for various device classes (BJT, MOS, JFet, OpAmp, diodes, and a few others).

A broad selection of models and model parameters for devices dated before 2000 has been collected by A. Roldan from University of Granada. While no longer available from the original web pages, it will be offered below.

- [models\_ugr.7z](./model-parameters/models_ugr.7z) (maintained up to ca. 2010)

Another very comprehensive selection of models and model parameters for devices, covering active and passive devices from many device vendors has been derived from the simulator package [Micro-Cap 12](http://www.spectrum-soft.com/download/download.shtm), a formerly (up to 2019) professionally maintained commercial spice simulator, now free and publicly available.

- [MicroCap-LIBRARY.7z](./model-parameters/MicroCap-LIBRARY.7z) (maintained up to 2019)

There is a set of special models, home-made, for specific devices available. You may find a bipolar and a CMOS version of the 555, a bipolar 741, a bipolar ICL8038, behavioral LM3914, LR8 and LTC1044.

- [special\_models.zip](./model-parameters/special_models.zip)

ngspice supports digital event based simulation, which is more than 50 times faster than analog simulation. If you are using KiCad as schematic entry, there is a small (but growing) set of models for 74HCxxx devices available, which may directly be attached to the appropriate 74xxx symbol.

- [74HCxxxM.zip](./model-parameters/74HCxxxM.zip)

ngspice supports a large set of models for digital 74xx devices, mapping them onto XSPICE for true digital (or mixed signal with automatically set interfaces) simulation. In ngspice the models may be used by simply calling the subcircuit of the required device. In KiCad these models will need an appropriate pin assignment according to its symbol, (or a subcircuit when used by a multi-part symbol).

- [74xx-models.7z](./model-parameters/74xx-models.7z) (models for 74xx digital devices, a ngspice subset derived from the MicroCap library)

Various sources from the web:

- (partially outdated)

- - - - - (as of 2012).

Device vendor web pages:

- - - - (select the appropriate 'Document Type': PSPICE .lib, HSPICE or spice3 should be o.k.)

- - - - - - - - - - - - - For TI models, check for the product on the TI web pages. PSPICE models (use their \*.lib file in ngspice) may often be found in the 'Design & Development' section of the product page.

PDKs for IC design

For IC design very sophisticated model parameter sets are required for the complex intrinsic ngspice models (BSIM3, BSIM4, HiCUM, etc.). These data are typically made available by the semiconductor foundries (aka chip manufacturers) in a setup called PDK (process design kit). ngspice is largely compatible to the HSPICE versions of the PDKs. These are typically made available by the foundry to the customer against an NDA (non-disclosure agreement). But now the Open Source community has become actively involved in PDK generation. Google/Skywater have made a PDK for a 130nm process Open Source. Please see [here](./applic.html#sky) for more information. IHP is working on a PDK for its 130 nm BiCMOS proces [SG13G2](https://github.com/IHP-GmbH/IHP-Open-PDK).

Other sources of models for advanced MOS (IC related, but not necessarily linked to any foundry) are found here:

- - [asap7](https://github.com/The-OpenROAD-Project/asap7)

- [Models for 0.8u, 0.35u, 0.18u, 45nm, 7nm CMOS](https://analogicdesign.com/students/netlists-models/model-files/)

How to add models and model parameters to the ngspice netlist

Basically ngspice may use three types of model data: the PDKs (we will not talk about them here, see our [Application page](./applic.html#sky)), sets of model parameters for the intrinsic ngspice device models, and complete subcircuit models for OpAmps and other devices and circuits.

A set of model parameters is used by ngspice device models like bipolar or MOS transistors, JFETs or transmission lines. Such a model parameter set is arranged in a single line and looks like
    .model mname type ( pname1=pval1 pname2=pval2 ... )

where mname is the model name, type is the ngspice model type, and pnamxx are the model parameters with their values pvalxx. The parameters are prescribed by the model type, the values are used to achieve best correlation between model and measured device reality. Please note that sometimes the .model is split into several lines, where consecutive lines start with a '+' in the first column. This is regarded as a single line. A typical example is:
    *SRC=BC546;BC546;BJTs NPN;Gen. Purpose;65V 100mA
    .MODEL BC546 NPN (IS=50.7F NF=1 BF=318 VAF=145 IKF=.3
    + ISE=15.9P NE=2 BR=4 NR=1 VAR=24 IKR=.45 RE=1.54 RB=6.17
    + RC=.617 XTB=1.5 CJE=20.8P CJC=8.33P TF=611P TR=138N)
    *   National 65 Volt  .5 Amp  260 MHz  SiNPN  Transistor  01-26-1991
    *PINOUT TO-92 3 2 1

Lines starting with an asterisk '\*' are comment lines, used to explain some details and to define the (visible) boundaries between this and the next (previous) model parameter set, if many of them are put together in a model library file.

The other model type is a subcircuit model, putting several interconnected intrinsic devices into a subcircuit, which is enclosed in .subckt ... .ends and looks like
    .subckt sname node1 node2 node3
        ...
    .ends

where sname is the model's name, and nodexx are the nodes connecting the subcircuit to the outside world. An example (a power MOS transistor FDS86252) is this:
    .SUBCKT FDS86252 2 1 3
    ******************************************************************
    **      Fairchild Discrete Modeling Group                       **
    ******************************************************************
    **      Website         www.fairchildsemi.com\models            **
    ******************************************************************
    **      (C) Copyright 2009 Fairchild Semiconductor Corporation  **
    **                      All rights reserved                     **
    **                                                              **
    **                      FDS86252 Spice model                    **
    **                    Revision RevA, 28 Apr 2011                **
    ******************************************************************
    *Nom Temp 25 deg C
    Dbody 7 5 DbodyMOD
    Dbreak 5 11 DbreakMOD
    Lgate 1 9 5.108e-9
    Ldrain 2 5 0.1e-9
    Lsource 3 7 2.295e-9
    RLgate 1 9 51.08
    RLdrain 2 5 1
    RLsource 3 7 22.95
    Rgate 9 6 0.47
    * Shielded  Gate
    D1 100 5 D_SG_cap
    D2 100 101 D_SG_cap
    R1 101 7 0.876
    C1 6 101 87e-12
    .MODEL D_SG_cap D (IS=1e-9 n=1 RS=4e-3 CJO=0.994e-9 M=0.711 t_abs=25)
    It 7 17 1
    Ebreak 11 7 17 7 158.5
    Rbreak 17 7 RbreakMOD 1
    .MODEL RbreakMOD RES (TC1=0.75e-3 TC2=-0.9e-6)
    .MODEL DbodyMOD D (IS=2.5e-12 n=1.05 RS=7e-3 TRS1=7.5e-3 TRS2=1e-6
    + CJO=0.252e-9 M=0.565 TT=1e-9 XTI=9.5)
    .MODEL DbreakMOD D (TRS1=0 TRS2=1e-6 )
    Rsource 7a 7 0.715e-3
    Rdrain 5 16 RdrainMOD 36e-3
    .MODEL RdrainMOD RES (TC1=7.25e-3 TC2=21e-6)
    M_BSIM3 16 6 7a 7a Bsim3 W=1.1544 L=1.1e-6 NRS=0 NRD=0
    .MODEL Bsim3 NMOS (LEVEL=7 VERSION=3.1 MOBMOD=3 CAPMOD=2 paramchk=1 NQSMOD=0
    *Process Parameters
    + TOX=1000e-10 ;Oxide thickness
    + XJ=0.54e-6 ;Channel depth
    + NCH=0.83e17 ;Channel concentration
    *Channel Current
    + U0=670 VSAT=500000 DROUT=1.8
    + DELTA=0.03 PSCBE2=0 RSH=0.715e-3
    *Threshold voltage
    + VTH0=3.85
    *Sub-threshold characteristics
    + VOFF=-0.13 NFACTOR=1.85
    *Junction diodes and Capacitance
    + LINT=0.19e-6 DLC=0.19e-6
    + CGSO=300e-12 CGSL=0 CGDO=1e-12 CGDL=150e-12
    + CJ=0 CF=0 CKAPPA=1
    * Temperature parameters
    + KT1=-2.85 KT2=0 UA1=17.5e-9
    + NJ=10)
    .ENDS

How to find a suitable model?

Expand the two model collections [models\_ugr.7z](./model-parameters/models_ugr.7z) and [MicroCap-LIBRARY.7z](./model-parameters/MicroCap-LIBRARY.7z) into a directory of your choice (e.g. models) to obtain folders models/MicroCap-LIBRARY-for-ngspice and models/modelos\_subckt. With a suitable text editor (e.g. notepad++ on Windows, Kate on Linux, or any other) create and open a file mymodels.lib and put it into the model folder. Search in the two collection folders and sub-folders (with the editor's text search function) for BC546 and FDS86252. There may be more than one entry for a device, so choose one. Mark and copy the model parameter set from begin to end (best including the comment lines also), at least from .model to end of last consecutive line and the model from .subckt to .ends and paste both into mymodels.lib.

Include mymodels.lib into your netlist, e.g. by (check for the correct path)
    .include model/mymodels.lib

You may now access the model data from within your netlist by calling the devices with
    Q2 c1 b1 e1 BC546
    XPowerMOS d1 g1 s1 FDS86252

If you are looking for a model from TI, e.g. the OpAmp OPA1641, you will find a PSPICE compatible, zipped model file assembly sbom627b.zip on the TI web pages. If you unzip it, the ngspice compatible device model is contained in the file OPA1641.lib. To check its eligibility, open the file in a text editor. After the introduction (comment lines), you will find the characteristic line
    .subckt OPA1641 IN+ IN- VCC VEE OUT

as the begin of the main subcircuit. So copy this file OPA1641.lib to your model folder and invoke it by:
    .include model/OPA1641.lib
    Xopamp inp inm vc ve opout OPA1641

And because this OpAmp model is a PSPICE model, don't forget to set
    set ngbehavior=ltpsa

in file .spiceinit.

[](https://sourceforge.net) All text is available under the terms of the GNU Free Documentation License ![](../images/spice.jpg)
