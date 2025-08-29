# Ngspice - Open Source Spice Simulator

![NGSPICE](../images/nglogo.jpg) ![Mixed mode - mixed level circuit simulator - based on Berkeley's Spice3f5](../images/ngtext2.jpg) [](https://sourceforge.net/projects/ngspice)

## About Ngspice

ngspice is the open source spice simulator for electric and electronic circuits.

Such a circuit may comprise of JFETs, bipolar and MOS transistors, passive elements like R, L, or C, diodes, transmission lines and other devices, all interconnected in a netlist. Digital circuits are simulated as well, event driven and fast, from single gates to complex circuits. And you may enter the combination of both analog and digital as a mixed-signal circuit.

ngspice offers a wealth of device models for active, passive, analog, and digital elements. Model parameters are provided by our [collections](./modelparams.html#collections), by the [semiconductor device manufacturers](./modelparams.html#vendors), or from [semiconductor foundries](./applic.html#sky). The user adds her circuits as a netlist, and the output is one or more graphs of currents, voltages and other electrical quantities or is saved in a data file.

ngspice does not provide schematic entry. Its input is command line or file based. There are however [third party](https://ngspice.sourceforge.io/resources.html) interfaces available.

## Compatibility

ngspice is SPICE compatible. You may apply PSPICE or LTSPICE device model parameters and netlists for simulating discrete circuits. ngspice will also read HSPICE device libraries from semiconductor foundry PDKs for simulating integrated circuits.

## Availability

ngspice builds on many operating systems. The source code and binaries for MS Windows are available for download on our [sourceforge download page](https://sourceforge.net/projects/ngspice/files/ng-spice-rework/). All popular [Linux distributions, Cygwin or FreeBSD](packages.html) offer ngspice as well, as does [Homebrew](https://formulae.brew.sh/formula/ngspice) for macOS. The [F.A.Q.](faq.html) and [documentation](./docs.html) pages provide a lot of information, a detailed [manual](https://ngspice.sourceforge.io/docs.html) is available. [Mailing lists](https://sourceforge.net/p/ngspice/mailman/), [discussion forums](https://sourceforge.net/p/ngspice/discussion/) and a [bug tracker](https://sourceforge.net/p/ngspice/bugs/) are offered.

Introductory videos on the ngspice status and updates have been held at several [FOSDEM](https://fosdem.org) conferences and are found here: [FOSDEM'20](https://fosdem.org/2020/schedule/event/ngspice/), [FOSDEM'21](https://fosdem.org/2021/schedule/event/ngspice/), [FOSDEM'22](https://fosdem.org/2022/schedule/event/ngspice/), and [FOSDEM'24](https://video.fosdem.org/2024/h1308/fosdem-2024-2834-ngspice-circuit-simulator-stand-alone-and-embedded-into-kicad.mp4).

If you are new to Spice and ngspice, don't hesitate to give it a try, if you are a professional user, you will benefit from its robustness and flexibility.

[](http://sourceforge.net) All text is available under the terms of the GNU Free Documentation License ![](../images/spice.jpg)
