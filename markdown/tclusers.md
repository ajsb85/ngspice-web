



[Home](./index.html)

[Screenshots](./screens.html)

[Download](./download.html)

[Documentation](./docs.html)

[Extras/Options](./extras.html)

[Contributions](./contrib.html)

Development

[Simulation Environments](./resources.html)

[Quality](./quality.html)

Ngspice Development

-   [Developers Info](./devel.html)

-   [Bug Reports](./bugrep.html)

-   [Git Access](./gitaccess.html)

-   [Docs for developers](./devdocs.html)

-   [Mailing List Archives](./mlarch.html)

-   [Releases Info](./relinfo.html)

-   [Roadmap](./roadmap.html)

-   [Writing Docs](./docwrite.html)

-   

    ------------------------------------------------------------------------

-   [Tests](./applic.html#test)

OSDI/OpenVAF for ngspice

-   [What is OSDI/OpenVAF ?](./osdi.html)

GSS-TCAD

-   GSS

TCLspice

-   [What TCLspice is ?](./tclspice.html)
-   [TCLspice users manual](./tclusers.html)
-   [TCLspice by examples](./tclexamples.html)
-   [Designer's note](./tclnotes.html)

TCLspice Users Manual

Version 0.1

TCLspice is a circuit simulator library based on ngspice, a circuit simulator emerged from the ashes of spice3f5.

In tclspice two elements are important: TCL and spice. TCL refers to the scripting and extension language TCL/TK and Spice refers to the well known simulator. TCLspice is a synergy between the two and gives users the  power to extend spice with tcl and vice versa. The many packages available for TCL make this the ideal language to build new powerful circuit simulation software, and HMI/GUI.

This document does not cover what spice is, neither how to use it, nor tcl syntax. If you don't already know, this document is of no interest for you, and you should jump to the bibliography section, where you can find references.

This document will inform you on the actual implementation of tclspice: What is done, what is not. It will give you necessary information to use the package spice in a tcl script or console, and give you ideas of the benefits you can have from it. After reading you can grant more information in [TCLSpice learn by example](./tclexamples.html) page.

Installation

Dependencies

As any complex software ngspice can have a lot of compiling options. Refer to the installation notes of ngspice to find those which suit your needs.

TCLSpice relies on several other packages. As Nobody tracked the dependencies before, there is no information on dependencies compatibility. I give the revision number I use. Don't hesitate to tell me your success and failures with other versions. In order to get tclspice compiled, you need to have on your computer those software:

-   tcl (using version 8.4)
-   tk (using version 8.4)
-   BLT (using v2.4)
-   tclreadline (using v1.2)(may be required at configuration time by error but it is not required at comppilation time)

Compilation

Once you have it and you know what flavour to give to your spice engine, download and unpack ngspice sources.

./autogen.sh ./configure  --enable-capzerobypass --enable-intnoise  --enable-numparam --enable-dot-global --enable-xspice --with-tcl make

Above is given the minimal set of configure switch. Below is what I personnally suggest:

--enable-capzerobypass --enable-intnoise --enable-xspice --with-tcl --enable-debug --enable-numparam --enable-dot-global --enable-maintainer-mode --enable-experimental

Testing

Go to a tclspice test-bench directory and run the test:

cd test/tcl-testbench1 ./testbench1

Your own judgement will let you know if it is ok or not.

Installing (needs root privilege)

make install

If it does not run, look at the console output, if it gives you clues to solve your problem, do it. If it does not, ask for help.

Installation Directory

As you may know tclspice consists in a library which is an executable shared object. You will see in the next section that you can either call it by providing a TCL interpreter the library absolute path, or simply by providing the library package name.

Running tclspice by its absolute path does not require it to be placed in a special place. Runing it by its package name requires a package description file to be placed in a predefined directory. This is automatically done by the configure script. The configure script find an acceptable place for the library, and another acceptable place for the configuration files, by reading tclConfig.sh file. If you don't provide any target directory, runing make install will enable you to open you tcl interpreter and load spice package automatically.

If you want the library to be installed in another directory, you can proceed two ways:

-   Copy the libspice.so.\* files by hand. (Typically in src/.libs/ If it is not there, use find command to locate it).

-   Provide the install script with your custom installation path, using spicelibdir environement variable. In the example below, notice that there is NO -- before spicelibdir:

    ./configure spicelibdir=/whereever/you/want --with-tcl

    run make, run make installe with the required privileges.

When running make install, the installation process will try to install a package descriptor in an acceptable directory. The consequence is that you can still run spice package from a tcl interpreter by its package name. The drawback is that you can have the installation process failing if you try to install it without root privileges.

As you can see this is still under developpement. If you get errors, please, inform me.

Running without installing

Still to be developed.

Running TCLspice

TCLspice consists of a package to include in your tcl console or script:

package require spice

Then you can execute any native spice command by preceding it with *spice::* For example if you want to source the testCapa.cir netlist, type the following:

spice::source testCapa.cir

TCLspice gets its identity in the command spice::vectoblt This command copies data computed by the simulation engine into a tcl variable. vectoblt is composed of three words: vec, to and blt. Vec means spice vector data. To is the English preposition, and blt is a useful tcl package providing a vector data structure. Example:

blt::vector create Iex spice::vectoblt Vex#branch Iex

Here an empty blt vector is created. It is then filled with the vector representation of the current flowing out of source Vex. Vex#branch is native spices syntax. Iex is the name of the BLT vector.

The reverse operation is handled by native spice commands, such as alter, let and set.

Plotting

Plotting data is not a matter of spice, but of tcl. Once the data is stored in a blt vector, it can be plotted. Example:

blt::graph .cimvd -title "Cim = f(Vd)" pack .cimvd .cimvd element create line1 -xdata Vcmd -ydata Cim

With blt::graph a plotting structure is allocated in memory. With pack it is placed into the output window, and becomes visible. The last command, and not the least, plots the function Cim = f(Vcmd), where Cim and Vcmd are two BLT vectors.

Bibliography

-   Spice Information:
    -   
    -   
    -   
-   Spice Usage:
    -   [newton.ex.ac.uk/teaching/CDHW/Electronics2/userguide/index.html](http://newton.ex.ac.uk/teaching/CDHW/Electronics2/userguide/index.html)
-   Tcl and TCL/TK:
    -   
    -   
    -    (French)
    -   [http://www.bin-co.com/tcltutorial/contents.php](http://www.bin-co.com/tcl/tutorial/contents.php)
-   BLT (There is almost no documentation on BLT:
    -   Introduction: [http://heim.ifi.uio.no/~hpl/Pmw.Blt/doc/tutorial.html](http://heim.ifi.uio.no/%7Ehpl/Pmw.Blt/doc/tutorial.html)
    -   Official docs, download slides.pdf on 
    -   On vectors usage: 
    -   Extensive help is available in the sources tarball.
    -   The manpages are available online (It is a directory listing. Choose your topic) 

