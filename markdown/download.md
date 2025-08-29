![NGSPICE](./images/nglogo.jpg) ![Mixed mode - mixed level circuit simulator - based on Berkeley's Spice3f5](./images/ngtext2.jpg) [](https://sourceforge.net/projects/ngspice)

-   [Home](./index.html)
-   [News](./news.html)
-   [Screenshots](https://sourceforge.net/projects/ngspice/)
-   [Download](https://sourceforge.net/project/showfiles.php?group_id=38962)
-   [Documentation](./docs.html)
-   [Tutorials](./tutorials.html)
-   [Extras/Options](./extras.html)
-   [Applications](./applic.html)
-   [Development](./devel.html)
-   [Simulation Environments](./resources.html)
-   [Quality](./quality.html)

Ngspice Download

-   [Download](https://sourceforge.net/project/showfiles.php?group_id=38962)
-   [Git Access](gitaccess.html)
-   [Prereleases](prereleases.html)
-   [Old Releases](oldreleases.html)
-   [Packages](packages.html)

Ngspice download (stable release)

All ngspice stable releases, including the most recent one, can be downloaded from [Sourceforge.net File Release System](https://sourceforge.net/projects/ngspice/files/ng-spice-rework/). Ngspice is released as a gzipped tar archive containing all source files of the simulator. They compile under various operating systems, e.g. LINUX, MS Windows, MAC, BSD, Solaris, and maybe others. Binary packages are distributed for MS Windows and MAC OS X.

-   [**ngspice-44**](https://sourceforge.net/projects/ngspice/files/ng-spice-rework/44/): this is the folder with the latest stable release. It does not contain last minute code and experimental features. This is the release intended for end-users. All sources are assembled into a tarball for download. Binary packages for MS Windows and MAC OS X are to be found here as well.

Ngspice installation (quick intro)

For MS Windows (64 bit, Windows 10 or up) we are using an efficient 7z compressed folder. You may extract it with a software like [7-Zip](https://7-zip.de/index.html), to be installed before downloading ngspice. Then download [ngspice-44\_64.7z](https://sourceforge.net/projects/ngspice/files/ng-spice-rework/44/ngspice-44_64.7z) from the web site given above. Expand the contents of the 7z zipped file to an arbitrary location on your computer (you should have read and write access to this location, if not run in admin mode), e.g. to D:\\ You also may download the [**GUI**](https://ngspice.sourceforge.io/experimental/ngspice_start.7z) that is shown [below](./download.html#bin1). Expand its content into the Spice64\bin folder. And that's it!

A macOS release is currently not available from the ngspice web pages. You may refer to [Homebrew](https://formulae.brew.sh/formula/ngspice) for an up-to-date executable.

For Linux we do not offer pre-compiled packages. You may either resort to your Linux distributor und use their installation manager for a pre-compiled package. Some are listed [here](packages.html). However these may not yet contain the current release version. So you might want to compile ngspice by yourself. Then download and extract the sources from the [ngspice-44 tarball](https://sourceforge.net/projects/ngspice/files/ng-spice-rework/44/ngspice-44.tar.gz). Please see file INSTALL or the [ngspice manual](https://sourceforge.net/projects/ngspice/files/ng-spice-rework/44/ngspice-44-manual.pdf) (chapt. 28) for instructions on compilation and installation of ngspice. Installation on RedHat or similar OSs is described [here](https://sourceforge.net/projects/ngspice/files/ng-spice-rework/44/NGSPICE%20on%20Red%20Hat%20Like%20Distributions.pdf).

If you are interested in the [ngspice nightly](./download.html#nightly) for MS Windows or other development or ngspice experimental versions, please read on! Legacy Windows OSs are supported as well.

Ngspice source code download via browser or snapshot (code under development)

-   [**ngspice tree view of master branch**](https://sourceforge.net/p/ngspice/ngspice/ci/master/tree/): This is the master branch of the code actually under development. It contains the most recent features and has already got lots of testing. Use this link to access the individual source code files via your browser. Select 'Download Snapshot' from this page to download the complete and actual master branch source code. Check one of the 'Branches' buttons (or 'More Branches' to display all branches) to switch to another branch and then again use 'Download Snapshot'. Another development branch example is given in the next bullet point.



-   [**ngspice tree view of branch pre-master-45**](https://sourceforge.net/p/ngspice/ngspice/ci/pre-master-45/tree/): This is the current development branch with very recent source code additions. After testing they may make it into the master branch and the next stable release. Use this link to access the source code files via your browser or download the complete snapshot by 'Download snapshot'.

Ngspice source code download using git (code under development)

Using 'git' offers you a way to get access to all branches and to manage them. The following command will download the complete sources from the ngspice git repository via anonymous access. You will find the ngspice top level directory as \[actual directory\]/ngspice, containing a complete local git repository.

git clone git://git.code.sf.net/p/ngspice/ngspice

Please see file INSTALL for instructions on compilation and installation of ngspice.

For more details on git usage please see our [git access page](./gitaccess.html).

For github or gitlab users, there are up-to-date clones (not managed by the ngspice team, kudos to the organizers) available: [**ngspice at github**](https://github.com/danchitnis/ngspice-sf-mirror/tree/pre-master-44) or [**ngspice at gitlab**](https://gitlab.com/ngspice/ngspice/-/tree/pre-master-44).

Ngspice GUI for MS Windows

A simple GUI for starting ngspice and plotting (binaries for MS Windows, 64 bit) is available [**here**](https://ngspice.sourceforge.io/experimental/ngspice_start.7z), along with its [**source code**](https://ngspice.sourceforge.io/experimental/ng_gui_sources.7z) that compiles with [**Lazarus**](https://www.lazarus-ide.org/) IDE.



Ngspice-44+ for MS Windows (pre-master-45 branch, 64 bit)

[**ngspice-44plus 64 bit devel**](https://ngspice.sourceforge.io/experimental/ngspice-44plus-pre-master-45.7z) is our ngspice nightly for MS Windows (though not updated every night). It contains 64 bit ngspice binaries with GUI, console and the shared ngspice dll. Sources are drawn from the pre-master-45 branch at git. The last update has been made on December 29th, 2024. It contains the KLU solver and the [OpenVAF/OSDI](https://openvaf.semimod.de/docs/getting-started/introduction/) interface for Verilog-A device models.

Ngspice executables for Windows console and macOS (pre-master branch, 64 bit)

**ngspice-42plus 64 bit devel** is the ngspice nightly, automatically created every night, for Windows and macOS (Intel and ARM), to be found at [Github](https://github.com/gatk555/ngspice/actions).

Ngspice-41 update for Fusion360 and EAGLE (MS Windows, 64 bit)

[**ngspice-41 64 bit upgrade**](https://ngspice.sourceforge.io/eagle-upgrade/ngspice-Fusion360-Update.7z) is an offer to the Fusion360 and EAGLE community to upgrade their ngspice-26 installation to a current ngspice. The ngspice.exe was made from master branch on September 21st 2023, tagged ngspice-41, for MS Windows. An installation how-to is found in file ngspice-howto.txt.

Ngspice for MS Windows, reading, simulating and writing wav audio files

[**ngspice-43 64 bit wave audio**](https://ngspice.sourceforge.io/experimental/Spice_wav_43.7z) is ngspice for MS Windows based on branch hv-wave-43. It reads wav audio files, use the contents as voltage source input for simulation, and writes out the results again as a wav file. The 7z archive contains 64 bit ngspice, or 64 bit ngspice.dll, with all required extra dlls and a section with some examples. Some testing is still required, and some know how in wav files and audio sampling may help. See file README.wavsim for some more details and acknowledgments and file README.examples for a list of the experimental files. Many thanks to Robin Gareus and Hannu Vuolasaho. Robin Gareus has provided an introduction and manual on his [web pages](http://gareus.org/oss/spicesound/start).

The additional libraries are [samplerate.dll](https://github.com/libsndfile/libsamplerate/releases), and [sndfile.dll](https://github.com/libsndfile/libsndfile/releases/).

Ngspice for legacy Windows OSs

Here you will find ngspice-33 made with MINGW as 64 bit binary for MS Windows 7. Right click on a link and store the 7z file to your harddisk. [**ngspice-33 for W7**](https://ngspice.sourceforge.io/experimental/ngspice-33-w7.7z) contains the ngspice.exe executable plus three dlls linked to the exe.

[**ngspice-27 for xp**](https://ngspice.sourceforge.io/experimental/ngspice-27_xp.7z) contains 32 bit ngspice-27 for Windows XP. Right click on the link and store the 7z file to your harddisk. Enclosed are ngspice.exe with GUI and the shared ngspice dll plus some other dlls needed.

Ngspice experimental (not updated for release version 41!)

Here you will find some ngspice binaries (for MS Windows) which are provided for those interested in experimental code. Right click on a link and store the 7z file to your harddisk.

[**cuspice**](https://ngspice.sourceforge.io/experimental/ngspice-27-CUSPICE-64.7z) (ngspice-27 64 bit using CUDA, incl. CUDA redistributables, 24 MBit download size) contains a 64 bit ngspice binary with GUI, using the KLU matrix solver and CUDA (uses nvidia graphics card for acceleration). Sources are drawn from the CUSPICE+5 branch at git.

The ngspice [**tclspice package**](https://ngspice.sourceforge.io/experimental/tclspice-25.7z) includes all libraries and files necessary to run some tcl scripts with the ngspice tclspice dll. The package has been created with a modified [**BLT library**](https://ngspice.sourceforge.io/experimental/blt2.5.3.7z), which serves for plotting. If you install the tcl/tk libraries version 8.6 from [ActiveState](https://www.activestate.com/products/tcl/), add the [**VS 2008 project file**](https://ngspice.sourceforge.io/experimental/visualc-tcl.7z) to the ngspice main directory, and set the appropriate links in the project file to the tcl/tk library and headers, you may compile ngspice tclspice for MS Windows yourself.

A more recent tclspice version, very experimental, is here as [**BLT library for VS2017**](https://ngspice.sourceforge.io/experimental/blt2.5.3-compact.7z), and [**VS 2017 project file**](https://ngspice.sourceforge.io/experimental/visualc-tclspice-26plus.7z), based on the master branch as of June 2017. Again: very experimental, not yet tested!

Ngspice download (old, obsolete stuff)

Old releases (before rework-10), are available through this web site only (see the menu on the left), they are archived for historical purposes and are no longer maintained.

 All text is available under the terms of the GNU Free Documentation License ![](./images/spice.jpg)
