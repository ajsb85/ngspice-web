# Ngspice Frequently Asked Questions

**Document Revision**: 1.7
**Document Maintainer**: Holger Vogt
**Last Update**: 17-03-2018

## Table of Contents

- [Introduction and General Information](#introduction-and-general-information)
  - [What is ngspice?](#what-is-ngspice)
  - [Why resurrecting Berkeley's Spice?](#why-resurrecting-berkeleys-spice)
  - [What is the project's goal?](#what-is-the-projects-goal)
  - [What you are going to do?](#what-you-are-going-to-do)
  - [Legal issues](#legal-issues)
  - [What mailing lists exist for ngspice?](#what-mailing-lists-exist-for-ngspice)
  - [Are the mailing lists archived anywhere?](#are-the-mailing-lists-archived-anywhere)
  - [What newsgroups exist for ngspice?](#what-newsgroups-exist-for-ngspice)
  - [Where can I get a copy of ngspice?](#where-can-i-get-a-copy-of-ngspice)
  - [Where should I look on the World Wide Web for ngspice stuff?](#where-should-i-look-on-the-world-wide-web-for-ngspice-stuff)
  - [Where should I look on the World Wide Web for Spice documentation?](#where-should-i-look-on-the-world-wide-web-for-spice-documentation)
- [Development](#development)
  - [What is the current version?](#what-is-the-current-version)
  - [What are the latest features in the current release?](#what-are-the-latest-features-in-the-current-release)
  - [What does it look like?](#what-does-it-look-like)
  - [Who are the authors of ngspice?](#who-are-the-authors-of-ngspice)
  - [How can I report a bug/request for a feature?](#how-can-i-report-a-bugrequest-for-a-feature)
  - [How can I join the development?](#how-can-i-join-the-development)
- [Solutions to Common Miscellaneous Problems](#solutions-to-common-miscellaneous-problems)
  - [What systems are supported?](#what-systems-are-supported)
  - [I get errors when I try to compile the source code, why?](#i-get-errors-when-i-try-to-compile-the-source-code-why)
  - [This document didn't answer my question. Where else can I look for an answer?](#this-document-didnt-answer-my-question-where-else-can-i-look-for-an-answer)
- [Administrative Information and Acknowledgements](#administrative-information-and-acknowledgements)
  - [Feedback](#feedback)
  - [Formats in which this FAQ is available](#formats-in-which-this-faq-is-available)
  - [Authorship and acknowledgements](#authorship-and-acknowledgements)
  - [Disclaimer and Copyright](#disclaimer-and-copyright)

## Introduction and General Information

### What is ngspice?

Ngspice is a mixed-level/mixed-signal circuit simulator based on three open source software packages: Spice3f5, Cider1b1 and Xspice:

- Spice3 is the most famous and used circuit simulator. It was developed University of California at Berkeley (UCB), by "a cast of thousand" (as they say).
- Cider is a mixed-level simulator that already includes Spice3f5 and adds a device simulator to it: DSIM. Cider couples the circuit level simulator to the device simulator to provide greater simulation accuracy (at the expense of greater simulation time). Critical devices can be described with technology parameters (numerical models) and non critical ones with the original spice's compact models.
- Xspice is an extension to Spice3 that provides code modeling support and simulation of digital components through an embedded event driven algorithm.
- The NG prefix has lot of meanings: Next Generation, New Good, etc. Choose or invent the one you prefer. The heart of the project is the ngspice program.

### Why resurrecting Berkeley's Spice?

Berkeley's Spice can be considered the father of most circuit simulators available today. It is an old but still good piece of software, it may not be the fastest or the most reliable but it's free, it's available in source code and most of the electrical simulators inherited it's syntax. On the more technical side, spice3 uses good numerical algorithms (most commercial implementations have only strengthened them), implements most of the models for MOSFET submicron designs and has a powerful set of analyses. On the more "social" side, spice3 it's well introduced in the academic environment.

### What is the project's goal?

The project goal evolved during project development, at first the final goal was to develop a reliable, fast and friendly circuit simulator for mixed signal/mixed level simulation. During development it become apparent that to reach the goal a complete rewrite of spice was needed. Since it was almost absurd to rewrite Spice and since a new simulator was already under development: ACS (Al's Circuit Simulator), now GNUCap (GNU Circuit Analysis package), the goal of nspice became less utopical: merge Spice3f5, Xspice and Cider into a mixed-signal/mixed-level simulator that can be used as a reliable engine.

### What you are going to do?

We are going to develop a mixed-signal/mixed-level circuit simulation program integrating three different spice based simulators: Spice, Xspice and Cider.

Xspice is a mixed-signal circuit simulator developed by GTRI (Georgia Tech Research Institute) at Georgia Institute of Technology. Xspice was originally developed as an extension over Spice3c1. Xspice introduces code modeling and a digital simulator into ngspice. The "home site" of Xspice at GTRI is no longer available.

Cider is a mixed-level circuit and device simulator based on Spice3f5 that couples a device simulator (DSIM) to Spice.

The merging process has been done some 10 years ago, accompanied with bug fixing and improvement of the three simulators. The improvements are concentrated into 7 directions:

- Compact models: the improvements in compact models will address mainly the implementation of additional effects not available in the original code. Device specific improvements are documented on ngspice's documentation and in the DEVICE file in project's tarball.

  Improvements that affects all devices already implemented are: "dtemp" option to set instance's temperature relative to the circuit one and "m" parallel multiplier to simulate an arbitrary number of instances of the same kind connected in parallel.

- Simulator's analyses: this is a low priority area. Planned improvements include the implementation of parametric analyses, to analyse the behaviour of the circuit as a parameter changes. Parameter sweep, Monte Carlo and Worst Case fall in this category.

- Numerical analysis code: the improvements within the numerical code must be done with extreme care. Planned improvements are the use of a KLU library as possible Sparse library replacement and the upload of matrix solver and device evaluation to the GPU.

- Spice language: The language used to input the circuit to the simulator has been extended and now allows the user to input parametric values for components (the numparam library). Planned improvements includes a better support for circuit hierarchy, and netlist manipulation via command line (adding and removing instances).

- Frontend: The design of a new spice frontend is not of interest because free and commercial frontends are available.

- ngspice as shared library: ngspice may be compiled as a shared library with a C interface offering access to all simulation data and allowing full control of the simulator from a calling program. By integrating tclspice, ngspice may also be compiled as a TCL/TK library.

- Documentation: Commercial simulators come with very good manuals containing tutorials, description of models equations, example of use, suggestions, etc. Spice came with little documentation. The Spice3f manual, available on the Internet has been used as the basis for the new manual. It will be constantly improved during ngspice development and will be timely available with each new release.

### Legal issues

Ngspice merges three different simulators: spice3f5 and CIDER are covered by the modified BSD license (see <http://embedded.eecs.berkeley.edu/pubs/downloads/spice/index.htm>, <https://embedded.eecs.berkeley.edu/pubs/downloads/cider/index.htm>, and <ftp://ftp.cs.berkeley.edu/pub/4bsd/README.Impt.License.Change>). Xspice is in the public domain. The ngspice license is the modified BSD license. The ngspice manual is released under Creative Commons Attribution Share-Alike (CC-BY-SA) v4.0.

### What mailing lists exist for ngspice?

There are two active mailing lists dedicated to the ngspice project.

Users mailing list: <ngspice-users@lists.sourceforge.net> This list is for ngspice users, examples, problems, bug reports and general discussion on ngspice can be sent here.

Developers mailing list: <ngspice-devel@lists.sourceforge.net> The list dedicated to ngspice development. Developers shold subscribe here, to follow the program development. May be used to send patches, and technical discussion on ngspice.

Send an empty message with Subject "help" to the following addresses to get instructions.

Send an empty message to the following address to Subscribe.

Documentation about the user interface of these mailing lists can be found at:

1.7. Are the mailing lists archived anywhere ?

Yes, the lists are archived. There are two places where to look for archives. The project started on the IEEE Central and South Italy web server and then moved to sourceforge. Sourceforge provides an archiving service that cam be accessed via the summary page:

1.8. What newsgroups exist for ngspice ?

There is no ngspice specific newsgroup. Anyway ngspice threads appear on newsgroups dedicated to circuit simulation and electronic design. An (incomplete) list is:

- sci.electronics.cad
- comp.lsi.cad

1.9. Where can I get a copy of ngspice ?

You can download ngspice from:

1.10. Where should I look on the World Wide Web for ngspice stuff?

Look at the official Ngspice Web Page:

[http://ngspice.sourceforge.net](https://ngspice.sourceforge.io/)

1.11. Where should I look on the World Wide Web for Spice documentation ?

There are a lot of Internet sites that have information on spice, the best way is to point to your preferred search engine. Some interesting sites are:

The Spice Home Page:

The Spice Download Page:

Cider Page:

Spice benchmarks:

## DEVELOPMENT

2.1. What is the current version ?

The latest version released is:

- ngspice-36 (released on 01/01/2022)

2.2. What are the latest features in the current release ?

Please have a look at the ngspice main page

[ngspice main page](https://ngspice.sourceforge.io/)

2.3. What does it looks like ?

Ngspice, as the original Spice3 (and Xspice and Cider) is a command line simulator, with X11 or Windows graphics plotting.

2.4. Who are the authors of ngspice ?

The development is open to anyone who wish to contribute. If the original Spice3 was made with the contribution of "a cast of thousand", ngspice can only increase that number. An incomplete list of contributor makes the "acknowledgements" page of ngspice documentation.

2.5. How can I report a bug/request for a feature ?

The ngspice summary page (hosted on Sourceforge) has bug-reporting, feature-request and bugs trackers. You can use them or subscribe to mailing lists and post there. The former is preferred since it allows to follow up the status of improvements.

2.6. How can I join the development ?

To join the development just code the feature you want to add and send your patch in the mailing list. Before you start coding check the latest development release of ngspice from our CVS. It might be that your feature has already been implemented.

There is no bureaucracy here.

## SOLUTIONS TO COMMON MISCELLANEOUS PROBLEMS

3.1. What systems are supported ?

Ngspice is written in C, and may be compiled under FreeBSD, LINUX, Solaris, MacOS, under Windows using MS Visual Studio, mingw, or cygwin environment.

3.2. I get errors when I try to compile the source code, why ?

This is a one-million-euros question :).

Write a mail to the user's list describing the problem and providing information on the type of hardware, the flavour of operating system.

3.3. This document didn't answer my question. Where else can I look for an answer ?

Read old messages from the mailing list archive, search the web site or read the docs. Upgrade to the latest version of ngspice, many problems are fixed in the new versions. If you still can't find an answer, post your question to the mailing lists.

## ADMINISTRATIVE INFORMATION AND ACKNOWLEDGEMENTS

4.1. Feedback

Send your comments about this F.A.Q. and about ngspice to the users list

ngspice-users@lists.sourceforge.net.

4.2. Formats in which this FAQ is available

This document is available only in ASCII format in the ngspice source package.

4.3. Authorship and acknowledgements

Parts of the questions and answers are originate from Paolo Nenzi.

4.4. Disclaimer and Copyright

This document is provided as is. The information in it is not warranted to be correct: you use it at your own risk.
