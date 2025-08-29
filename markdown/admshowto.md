



-   [Home](./index.html)
-   [Screenshots](./screens.html)
-   [Download](./download.html)
-   [Documentation](./docs.html)
-   [Extras/Options](./extras.html)
-   [Contributions](./contrib.html)
-   Development
-   [Simulation Environments](./resources.html)
-   [Quality](./quality.html)

Ngspice Development

-   [Developers Info](./devel.html)

-   [Bug Reports](./bugrep.html)

-   [Git Access](gitaccess.html)

-   [Docs for developers](./devdocs.html)

-   [Mailing List Archives](./mlarch.html)

-   [Releases Info](./relinfo.html)

-   [Roadmap](./roadmap.html)

-   [Writing Docs](./docwrite.html)

-   

    ------------------------------------------------------------------------

-   [Tests](./applic.html#test)

ADMS for ngspice

-   [What ADMS is](./adms.html)
-   ADMS and ngspice HOWTO

GSS-TCAD

-   [GSS](./gss.html)

TCLspice

-   [What TCLspice is](./tclspice.html)
-   [TCLspice users manual](./tclusers.html)
-   [TCLspice by examples](./tclexamples.html)
-   [Designer's note](./tclnotes.html)

Introduction

In this document we will provide a guideline on how to auto-generate the ready-to compile C code for the ngspice API of a compact device model defined in the Verilog-AMS language. This feature is still experimental and not yet usable by a casual user.

Ngspice  includes the following Verilog-A compact models: 

-   ekv2.6
-   **hicum0**
-   **mextram**
-   psp102

For the MOS models (device Mxxxx) the following levels are implemented: ekv2.6 level=44, psp102 level=45, bipolar models (device qxxx): mextram 504 level=6, hicum0 level=7.

Goal:

In this guideline we will add the device model hicum0 to ngspice using the Verilog-AMS source code available from [TU Dresden](http://www.iee.et.tu-dresden.de/iee/eb/hic_new/hic_source.html) as hicumL0V1p11a. In fact this integration work has been done already for you. This guideline however assumes that hicum0 is not yet available. To run the examples, you will need the actual code from the ngspice git repository (see the [download page](./download.html)).

Limitations:

The adms ngspice interface supports a limited set of Verilog-AMS language constructs. Unfortunately the original adms web site is no longer on-line. Feel free to contribute to the adms ngspice interface so that more constructs can be supported. Especially the small signal noise analysis is not yet implemented.

01\. Adding admsXml to your build environment

To compile Verilog-AMS compact models into ngspice-ready C models the the program admsXml is required. Details of this software are described in several talks by Laurent Lemaitre at [MOS-AK](http://www.mos-ak.org/). To facilitate the installation, a source code package has been assembled for use with ngspice, available for [download here](adms2/adms-svn-ngspice-src.zip). It is based on source code from the subversion repository of adms on August 1st, 2010, Version 1186 and has been slightly modified (see ChangeLog).

Under OS LINUX (tested with SUSE 11.2, 64 bit) you may expand the zip file and run ./autogen\_lin.sh, followed by 'make' and 'make install'.

Under OS CYGWIN (tested with actual CYGWIN on MS Windows 7, 64 bit), please use ./autogen\_cyg.sh, followed by 'make' and 'make install'.

Under OS MINGW, a direct compilation would require the additional installation of perl module XML-LibXML which is not as straighforward as it should be. However you may start with a CYGWIN compile as decribed above. If you then go to your MSYS window, cd to the adms top directory and start ./mingw-compile.sh, you will obtain admsXml.exe, copied to MSYS /bin, and you are ready to go.

To facilitate installation under MS Windows, a admsXml.exe binary is available [here](adms2/adms-admsXml-Win32-bin.zip). Just copy it to MSYS /bin directory and start working on your verilog models.

A short test of a successful installation is:

$ admsXml -v \[usage..\] &lt;release  version="2.3.0" date="Aug 4 2010" time="10:24:18"/&gt;

Compilation of admsXml with MS Visual Studio is not possible, because the source code has variable declarations not only at the top of a block, but deliberately also in the following lines. This is o.k. by the C99 standard, but not supported by MS Visual Studio.

02\. Adding the hicum0 Verilog-A model to ngspice

Here we describe the necessary steps to add a Verilog-AMS model to ngspice using a device (hicum0 bipolar model) as example.

Ngspice does not offer support for loading models at run time. Every model must be included at compile time. Then, adding a new model into ngspice is a process that cannot be completely automated. Some files need to be edited by hand.

02.01 - Rent a space for your model

Verilog-AMS models in ngspice are collected under the 'src/spicelib/devices/adms/' directory. Models in that directory are scanned by 'autogen.sh' to generate the appropriate 'Makefile.am'. Create an 'hicum0' directory and an 'hicum0/admsva'. The latter is where we will put the Verilog-AMS files describing our model. Copy all the files of hicum0 into 'hicum0/admsva'. You have to rename the main file containing the verilog module with the directory name (e.g. modulename.va -&gt; hicum0.va). That's all we have to do at this level.

02.02 - What does ngspice need to know about new models ?

First you have to assign your new model a "device type". As you probably know, ngspice recognizes the type of a device by the first letter in device's name in the netlists ("r" for resistors, "q" for BJT, "m" for mosfets and so on). Then the first thing you have to find is the correct type for your new device (let's call this device\_type). Hicum is a bipolar device and then the right inital is "q".

Since there can be more than one model for each device type, another parameter you have to set is the device\_level, which must be unique for each device type. We choose "7" as the level for hicum0. We need to modify the file 'src/spicelib/parser/inpdomod.c' adding a "stanza" for hicum0 (look how hicum0 support is implemented). We need to change the routine that parses the device\_type, in this case '/src/spicelib/parser/inp2q.c'. Look at the modification made to implement hicum0. There is no standard template in this case and mostly depends on the device already supported. You have to know a little of spice internals to perform this step (look at what has already been done).

Further changes are to be made in the 'src/spicelib/devices/dev.c' file. Here we "link" the new model to ngspice. Again, this step is necessary because ngspice does not (yet) support dynamic loading of devices. The changes in this file are:

-   Add the model interface include (hicum0itf.h),
-   update the number of devices,
-   add an entry in `DEVices[]` array.

Finally, you may need to add device info into 'src/spicelib/devices/adms/admst/ngspiceVersion.xml'.

02.03 - What does autoconf need to know about new models ?

We need to add linking information for the new spice model, modifying the `configure.in` script adding entries in the VLADEVDIR and VLADEV variables and modifying autogen.sh as well. The name of the library is the name of the model directory.

02.04 - Rebuild ngspice configuration files

Now that we added the new model we need to regenerate the configuration files. We need to re-issue the autogen.sh command as follows:

$ ./autogen.sh --adms  

If admsXml is not installed properly, an error message is shown. If everything is o.k., you will get an output like:

Skipping CVS  
Skipping scripts dir  
Entering into directory: ekv  
--&gt;src/spicelib/devices/adms/ekv  
\[info...\] admsXml-2.3.0 (1186M) Aug 4 2010 10:24:44  
\[info...\] Makefile.am: file created  
\[info...\] elapsed time: 1 (second)  
\[info...\] admst iterations: 209089 (202225 freed)  
Entering into directory: hicum0  
--&gt;src/spicelib/devices/adms/hicum0  
\[info...\] admsXml-2.3.0 (1186M) Aug 4 2010 10:24:44  
\[info...\] Makefile.am: file created  
\[info...\] elapsed time: 1 (second)  
\[info...\] admst iterations: 325850 (317743 freed)  
Entering into directory: mextram  
--&gt;src/spicelib/devices/adms/mextram  
\[info...\] admsXml-2.3.0 (1186M) Aug 4 2010 10:24:44  
\[info...\] Makefile.am: file created  
\[info...\] elapsed time: 2 (second)  
\[info...\] admst iterations: 1891618 (1882424 freed)  
Entering into directory: psp102  
--&gt;src/spicelib/devices/adms/psp102  
\[info...\] admsXml-2.3.0 (1186M) Aug 4 2010 10:24:44  
\[info...\] Makefile.am: file created  
\[info...\] elapsed time: 2 (second)  
\[info...\] admst iterations: 1152671 (1138269 freed)  

Now we are ready to rebuild and install ngpice.

**WARNING**: at the compilation step some messages about '#warning adms version too recent' will be printed. Just ignore them for now.

03\. Test the Implementation of hicum0 into ngspice

Create file 'hicum0.sp'. Its contents is given below:

$ cat hicum0.sp Hicum0 test .option temp=25.0 reltol=1e-5 bstol=1e-15 .model mybjtmodel npn npn=1 level=7 qN1 c b 0 0 mybjtmodel rcc cc c 100.0 rbb bb b 1k vcc cc 0 1.0 vbb bb 0 0.0 ac=0.0 .dc vbb 0.0 1.0 0.02 .print dc v(c) i(vbb) i(vcc) .end  

run 'ngspice':

$ ngspice -b hicum0.sp Circuit: .title Netlist Doing analysis at TEMP = 298.150000 and TNOM = 300.150000 No. of Data Rows : 51 .title Netlist DC transfer characteristic Mon Jan 30 10:22:01 2006 -------------------------------------------------------------------------------- Index v-sweep v(c) vbb#branch vcc#branch -------------------------------------------------------------------------------- 0 0.000000e+00 1.000000e+00 0.000000e+00 -7.105421e-17 1 2.000000e-02 1.000000e+00 -5.593842e-19 -1.265654e-16 2 4.000000e-02 1.000000e+00 -2.076336e-18 -2.775558e-16 3 6.000000e-02 1.000000e+00 -5.366258e-18 -6.061817e-16 4 8.000000e-02 1.000000e+00 -1.254873e-17 -1.320055e-15 5 1.000000e-01 1.000000e+00 -2.812744e-17 -2.874367e-15 6 1.200000e-01 1.000000e+00 -7.629085e-17 -7.666090e-15 7 1.400000e-01 1.000000e+00 -1.669761e-16 -1.669553e-14 8 1.600000e-01 1.000000e+00 -3.645759e-16 -3.636425e-14 9 1.800000e-01 1.000000e+00 -7.948513e-16 -7.920553e-14 10 2.000000e-01 1.000000e+00 -1.732082e-15 -1.725142e-13 11 2.200000e-01 1.000000e+00 -3.773484e-15 -3.757461e-13 12 2.400000e-01 1.000000e+00 -8.219658e-15 -8.183998e-13 13 2.600000e-01 1.000000e+00 -1.790375e-14 -1.782522e-12 14 2.800000e-01 1.000000e+00 -3.899630e-14 -3.882434e-12 15 3.000000e-01 1.000000e+00 -8.493698e-14 -8.456170e-12 16 3.200000e-01 1.000000e+00 -1.849987e-13 -1.841804e-11 17 3.400000e-01 1.000000e+00 -4.029389e-13 -4.011557e-11 18 3.600000e-01 1.000000e+00 -8.776254e-13 -8.737407e-11 19 3.800000e-01 1.000000e+00 -1.911521e-12 -1.903059e-10 20 4.000000e-01 1.000000e+00 -4.163405e-12 -4.144973e-10 21 4.200000e-01 9.999999e-01 -9.068141e-12 -9.027994e-10 22 4.400000e-01 9.999998e-01 -1.975094e-11 -1.966349e-09 23 4.600000e-01 9.999996e-01 -4.301867e-11 -4.282821e-09 24 4.800000e-01 9.999991e-01 -9.369701e-11 -9.328218e-09 25 5.000000e-01 9.999980e-01 -2.040767e-10 -2.031732e-08 26 5.200000e-01 9.999956e-01 -4.444870e-10 -4.425191e-08 27 5.400000e-01 9.999904e-01 -9.680991e-10 -9.638130e-08 28 5.600000e-01 9.999790e-01 -2.108483e-09 -2.099148e-07 29 5.800000e-01 9.999543e-01 -4.591957e-09 -4.571626e-07 30 6.000000e-01 9.999004e-01 -9.999448e-09 -9.955176e-07 31 6.200000e-01 9.997833e-01 -2.176941e-08 -2.167303e-06 32 6.400000e-01 9.995284e-01 -4.736784e-08 -4.715812e-06 33 6.600000e-01 9.989751e-01 -1.029470e-07 -1.024912e-05 34 6.800000e-01 9.977781e-01 -2.231776e-07 -2.221894e-05 35 7.000000e-01 9.952090e-01 -4.812339e-07 -4.791028e-05 36 7.200000e-01 9.897838e-01 -1.026165e-06 -1.021618e-04 37 7.400000e-01 9.786930e-01 -2.140206e-06 -2.130697e-04 38 7.600000e-01 9.573154e-01 -4.287705e-06 -4.268455e-04 39 7.800000e-01 9.197474e-01 -8.062749e-06 -8.025264e-04 40 8.000000e-01 8.611162e-01 -1.395965e-05 -1.388838e-03 41 8.200000e-01 7.801099e-01 -2.212604e-05 -2.198901e-03 42 8.400000e-01 6.791392e-01 -3.235919e-05 -3.208608e-03 43 8.600000e-01 5.627227e-01 -4.429334e-05 -4.372773e-03 44 8.800000e-01 4.367031e-01 -5.756142e-05 -5.632969e-03 45 9.000000e-01 3.111929e-01 -7.186079e-05 -6.888071e-03 46 9.200000e-01 2.120521e-01 -8.696058e-05 -7.879479e-03 47 9.400000e-01 1.637984e-01 -1.026891e-04 -8.362016e-03 48 9.600000e-01 1.443326e-01 -1.189191e-04 -8.556674e-03 49 9.800000e-01 1.353683e-01 -1.355550e-04 -8.646317e-03 50 1.000000e+00 1.312181e-01 -1.525242e-04 -8.687819e-03 Total elapsed time: 0.625 seconds. Current dynamic memory usage = 1.515520 MB, Dynamic memory limit = 1241.702400 MB.

04\. How does adms work ?

In the previous chapters we described the general procedure for adding Verilog-A devices into ngspice. The process has been automated as much as ngspice api allowed, and most of adms operations are hidden from the user view. In this chapter we describe a little how adms works. adms creates the ready-to-compile C code from a set of admst code generators. admst is a subset of the XML language which has been created specifically for the purpose of C code generation. The syntax of admst is very close to the XSLT language (it includes some extensions.)

04.01 - Template files

The files in admst directory are the templates applied to generate the C code routines needed by ngspice api for each model. The files are:

-   `ngspiceVersion.xml`: a file that must be included in every call to admsXml.
-   `ngspiceMakefile.am.xml`: The template that generates the Makefiles.am in model directory.
-   `ngspiceMODULEacld.c.xml`: small signal ac analysis routine.
-   `ngspiceMODULEask.c.xml`: instance parameter report routine.
-   `ngspiceMODULE.c.xml`: model interface description.
-   `ngspiceMODULEdefs.h.xml`: definitions for model.
-   `ngspiceMODULEext.h.xml`: symbols exported by the model.
-   `ngspiceMODULEguesstopology.c.xml`: jacobian entries definitons.
-   `ngspiceMODULEinit.c.xml`: model init routine.
-   `ngspiceMODULEinit.h.xml`: model init include.
-   `ngspiceMODULEitf.h.xml`: model interface include.
-   `ngspiceMODULEload.c.xml`: routine for non linear analyses.
-   `ngspiceMODULEmask.c.xml`: model parameter report routine.
-   `ngspiceMODULEmpar.c.xml`: model parameter setting routine.
-   `ngspiceMODULEpar.c.xml`: instance parameter setting routine.
-   `ngspiceMODULEpzld.c.xml`: small signal pole-zero analysis routine.
-   `ngspiceMODULEsetup.c.xml`: model setup routine.
-   `ngspiceMODULEtemp.c.xml`: model updating routine.

04.02 - 'Makefile.am' generation

The 'Makefile.am' in each model directory is generated when 'autogen.sh' is called with '--adms' option. The command used to generate it is:

admsXml admsva/hicum0l.va -Iadmsva -e ../admst/ngspiceVersion.xml \\ -e ../admst/ngspiceMakefile.am.xml

This command generates the Makefile.am and needed includes. A typical output follows:

\[info\] admsXml-2.1.3 Feb 2 2006 19:01:39 \[warning\] \[admsva\hicum0.va:30\]: standard vams file created (not found in -I path) ... 'constants.h' \[warning\] \[admsva\hicum0.va:31\]: standard vams file created (not found in -I path) ... 'discipline.h' \[info\] Makefile.am: file created \[info\] elapsed time: 1.0624 \[info\] admst iterations: 185425 (185425 freed)

The created 'Makefile.am' looks like:

\## \## Interface: ngspice 1.0.0.0 \## created by: admsXml-2.1.3 - Sunday, 02/26/06 \## Process this file with automake to produce Makefile.in ADMSXMLINTERFACE:=../admst hicum0.c: admsXml -Iadmsva admsva/hicum0.va \\ -e $(ADMSXMLINTERFACE)/ngspiceVersion.xml \\ -e $(ADMSXMLINTERFACE)/ngspiceMODULEitf.h.xml \\ -e $(ADMSXMLINTERFACE)/ngspiceMODULEinit.c.xml \\ -e $(ADMSXMLINTERFACE)/ngspiceMODULEinit.h.xml \\ -e $(ADMSXMLINTERFACE)/ngspiceMODULEext.h.xml \\ -e $(ADMSXMLINTERFACE)/ngspiceMODULEdefs.h.xml \\ -e $(ADMSXMLINTERFACE)/ngspiceMODULEask.c.xml \\ -e $(ADMSXMLINTERFACE)/ngspiceMODULEmask.c.xml \\ -e $(ADMSXMLINTERFACE)/ngspiceMODULEpar.c.xml \\ -e $(ADMSXMLINTERFACE)/ngspiceMODULEmpar.c.xml \\ -e $(ADMSXMLINTERFACE)/ngspiceMODULEload.c.xml \\ -e $(ADMSXMLINTERFACE)/ngspiceMODULEacld.c.xml \\ -e $(ADMSXMLINTERFACE)/ngspiceMODULEpzld.c.xml \\ -e $(ADMSXMLINTERFACE)/ngspiceMODULEtemp.c.xml \\ -e $(ADMSXMLINTERFACE)/ngspiceMODULEsetup.c.xml \\ -e $(ADMSXMLINTERFACE)/ngspiceMODULEguesstopology.c.xml \\ -e $(ADMSXMLINTERFACE)/ngspiceMODULE.c.xml perl -p -i.bak -e 's/IOP\\"(\w+)"/IOP("\L\1"/' hicum0.c noinst\_LIBRARIES = libhicum0.a libhicum0\_a\_SOURCES = \\ hicum0.c \\ hicum0acld.c \\ hicum0ask.c \\ hicum0defs.h \\ hicum0ext.h \\ hicum0guesstopology.c \\ hicum0init.c \\ hicum0init.h \\ hicum0itf.h \\ hicum0load.c \\ hicum0mask.c \\ hicum0mpar.c \\ hicum0par.c \\ hicum0pzld.c \\ hicum0setup.c \\ hicum0temp.c BUILT\_SOURCES = \\ hicum0.c \\ hicum0acld.c \\ hicum0ask.c \\ hicum0defs.h \\ hicum0ext.h \\ hicum0guesstopology.c \\ hicum0init.c \\ hicum0init.h \\ hicum0itf.h \\ hicum0load.c \\ hicum0mask.c \\ hicum0mpar.c \\ hicum0par.c \\ hicum0pzld.c \\ hicum0setup.c \\ hicum0temp.c CLEANFILES = \\ hicum0.c \\ hicum0.c.bak \\ hicum0acld.c \\ hicum0ask.c \\ hicum0defs.h \\ hicum0ext.h \\ hicum0guesstopology.c \\ hicum0init.c \\ hicum0init.h \\ hicum0itf.h \\ hicum0load.c \\ hicum0mask.c \\ hicum0mpar.c \\ hicum0par.c \\ hicum0pzld.c \\ hicum0setup.c \\ hicum0temp.c \#TODO (not implemented) \\ hicum0conv.c \\ hicum0del.c \\ hicum0dest.c \\ hicum0getic.c \\ hicum0mdel.c \\ hicum0noise.c \\ hicum0trunc.c INCLUDES = -I$(top\_srcdir)/src/include MAINTAINERCLEANFILES = Makefile.in

The targets in the file are described in GNU/Autoconf manual, here we give only a short description:

-   BUILT\_SOURCES: this tells GNU/autoconf that the files in this target depends on other targets.
-   CLEANFILES: files that should be cleaned by the "clean target", the call 'make clean'.

04.03 - 'Makefile.in' and 'Makefile' generation

Controlled by './autogen.sh' and with information from 'configure.in', automake will generate the 'Makefile.in'. The call to autoconf will then create the file 'configure'. The line with its call './configure --enable-maintainer-mode' will generate all 'Makefile'.

04.04 - C code generation

The C code is automatically generated from the Verilog-A model with the admsXml command (part of the adms suite), when you issue the 'make' command. If you look inside a 'Makefile.am' in a model directory you will find the following lines (more or less):

admsXml -Iadmsva admsva/hicum0.va \\ -e ../admst/ngspiceVersion.xml \\ -e ../admst/ngspiceMODULEitf.h.xml \\ -e ../admst/ngspiceMODULEinit.c.xml \\ -e ../admst/ngspiceMODULEinit.h.xml \\ -e ../admst/ngspiceMODULEext.h.xml \\ -e ../admst/ngspiceMODULEdefs.h.xml \\ -e ../admst/ngspiceMODULEask.c.xml \\ -e ../admst/ngspiceMODULEmask.c.xml \\ -e ../admst/ngspiceMODULEpar.c.xml \\ -e ../admst/ngspiceMODULEmpar.c.xml \\ -e ../admst/ngspiceMODULEload.c.xml \\ -e ../admst/ngspiceMODULEacld.c.xml \\ -e ../admst/ngspiceMODULEpzld.c.xml \\ -e ../admst/ngspiceMODULEtemp.c.xml \\ -e ../admst/ngspiceMODULEsetup.c.xml \\ -e ../admst/ngspiceMODULEguesstopology.c.xml \\ -e ../admst/ngspiceMODULE.c.xml perl -p -i.bak -e 's/IOP\\"(\w+)"/IOP("\L\1"/' hicum0.c

This is the command that generates C code. As you will see in the Makefile.am this command is used to generate the target "hicum0.c", this is a trick to inform `make` that he needs to generate hicum0.c (and other sources) from hicum0.va. The inital output of make is

admsXml -Iadmsva admsva/hicum0.va \\ -e ../admst/ngspiceVersion.xml \\ -e ../admst/ngspiceMODULEitf.h.xml \\ -e ../admst/ngspiceMODULEinit.c.xml \\ -e ../admst/ngspiceMODULEinit.h.xml \\ -e ../admst/ngspiceMODULEext.h.xml \\ -e ../admst/ngspiceMODULEdefs.h.xml \\ -e ../admst/ngspiceMODULEask.c.xml \\ -e ../admst/ngspiceMODULEmask.c.xml \\ -e ../admst/ngspiceMODULEpar.c.xml \\ -e ../admst/ngspiceMODULEmpar.c.xml \\ -e ../admst/ngspiceMODULEload.c.xml \\ -e ../admst/ngspiceMODULEacld.c.xml \\ -e ../admst/ngspiceMODULEpzld.c.xml \\ -e ../admst/ngspiceMODULEtemp.c.xml \\ -e ../admst/ngspiceMODULEsetup.c.xml \\ -e ../admst/ngspiceMODULEguesstopology.c.xml \\ -e ../admst/ngspiceMODULE.c.xml \[info\] admsXml-2.1.3 Feb 5 2006 10:53:46 \[info\] hicum0itf.h: file created \[info\] hicum0init.c: file created \[info\] hicum0init.h: file created \[info\] hicum0ext.h: file created \[info\] hicum0defs.h: file created \[info\] hicum0ask.c: file created \[info\] hicum0mask.c: file created \[info\] hicum0par.c: file created \[info\] hicum0mpar.c: file created \[info\] noise contribution not implemented - ignored! \[info\] noise contribution not implemented - ignored! \[info\] noise contribution not implemented - ignored! \[info\] noise contribution not implemented - ignored! \[info\] noise contribution not implemented - ignored! \[info\] noise contribution not implemented - ignored! \[info\] hicum0load.c: file created \[info\] hicum0acld.c: file created \[info\] hicum0pzld.c: file created \[info\] hicum0temp.c: file created \[info\] hicum0setup.c: file created \[info\] hicum0guesstopology.c: file created \[info\] hicum0.c: file created \[info\] elapsed time: 6.28783 \[info\] admst iterations: 1106226 (1106226 freed) perl -p -i.bak -e 's/IOP\\"(\w+)"/IOP("\L\1"/' hicum0.c

Once the C code is generated the model directory should contain the files:

$ ls admsva hicum0ask.c hicum0guesstopology.c hicum0mask.c hicum0temp.c constants.h hicum0.c hicum0init.c hicum0mpar.c Makefile CVS hicum0.c.bak hicum0init.h hicum0par.c Makefile.am discipline.h hicum0defs.h hicum0itf.h hicum0pzld.c Makefile.in hicum0acld.c hicum0ext.h hicum0load.c hicum0setup.c

05\. How to update ngspice when the Verilog-AMS source code changes

If you modify the Verilog-AMS code you sohuld run a "make clean" and then re-make the ngspice:

$ make clean ... ... $ make ... ... $ make install

------------------------------------------------------------------------

Appendix 01: Comments on spice3-flavoured flags like npn, pnp, nmos, pmos and so on

In the adms-based implementation of hicum0 the value of the device type flag (either npn or pnp) in the model card is just ignored. The selection of the type of the device is actually done using model parameters. In the Verilog-AMS code of hicum0 there are two special model parameters called 'npn' and 'pnp' which decide what the type of the device will be (either a npn bipolar model or pnp bipolar model). The Verilog-AMS piece of code that triggers the decision is as follows:

if (\`PGIVEN(npn))  
HICUMtype = \`NPN;  
else if (\`PGIVEN(pnp))  
HICUMtype = \`PNP;  
else  
HICUMtype = \`NPN;  
end  

\`PGIVEN(npn) is a macro that returns 1 is model parameter 'npn' occurs in the .model card of the ngspice netlist. Otherwise it returns 0. For instance:

1.  the following model card will select a NPN type device:

    .model mybjtmodel npn  
    + npn=1  
    + level=7  

2.  the following model card will select a PNP type device:

    .model mybjtmodel npn  
    + pnp=1  
    + level=7  

In both cases flag 'npn' is just ignored. In section 'Update manually the ngspice parser files' it is recommended to use flag 'adms' instead. This limitation results from the LRM of VerilogAMS that does not support flags.

