# - [Documentation](./Docs.Html)

![NGSPICE](../images/nglogo.jpg) ![Mixed mode - mixed level circuit simulator - based on Berkeley's Spice3f5](../images/ngtext2.jpg) [](https://sourceforge.net/projects/ngspice)

- [Home](./index.html)
- [News](./news.html)
- [Screenshots](https://sourceforge.net/projects/ngspice/)
- [Download](./download.html)
- [Documentation](./docs.html)
- [Tutorials](./tutorials.html)
- [Extras/Options](./extras.html)
- [Applications](./applic.html)
- [Development](./devel.html)
- [Simulation Environments](./resources.html)
- Quality

Ngspice Tests and Quality Assurance

- [Test circuits for KiCad Eeschema/ngspice](applic.html#KiCad)
- [Valgrind test with various netlists (Linux)](applic.html#para)
- [Large CMOS circuits (ISCAS85)](applic.html#lcir)
- [Test circuits (ISCAS85)](applic.html#test)
- [Make Check](applic.html#mchk)

\_\_\_\_\_ Tests and Quality Assurance \_\_\_\_\_

In this section you will find some test circuits as netlists or Eeschema input files. Again you are welcome to contribute!

Paranoia

[Paranoia tests](./tests/paranoia.7z) were suggested by Dietmar Warning. A large number of ngspice netlists has been assembled, a script ./paranoia\_tests.sh will run these examples under Valgrind and summarize the results. Valgrind will detect memory leaks (a few are still there, new ones may be introduced during code development). Unfortunately Valgrind is not available for MS Windows or macOS. Thus Linux is required to run the script. Running the tests, being paranoid, is a good attitude if large code changes are to be released.

Based on the paranoia test named above Brian Taylor has developed a parallel version of the test [Paranoia Parallel](./tests/paranoia_parallel.7z), making use of today's multi-core machines. On an 8-core machine it runs approx. 6 times faster than the serial version. See the README for details.

Test circuits for simulation in KiCad

KiCad/Eeschema uses the ngspice shared library to allow simulating electronic circuits directly from the circuit diagram. [kicad-test-circuits.7z](./tests/kicad-test-circuits.7z) contains several circuits, simple and more sophisticated ones to test the eeschema-ngspice couple. Plots showing expected results are included.

Large circuits (ISCAS85)

To challenge any circuit simulator, there has been published a test bench in 1985 at ISCAS (see [large test circuits](./tests/iscas85Circuits.7z) for the ngspice compatible version). At that time in fact an absolute challenge, even today any simulator (like ngspice) may be benchmarked by running these circuits (with up to 3512 gates and (optional) back-annotated passives).

ngspice (regression) test circuits

The ngspice distribution also provides a lot of [test circuits](https://sourceforge.net/p/ngspice/ngspice/ci/master/tree/tests) . Many of the available devices are bench-marked here.

make check

If you build ngspice on macOS, Linux or Cywin(Windows), you may run the `make check` command. A regression test is started, using the [regression circuits](https://sourceforge.net/p/ngspice/ngspice/ci/master/tree/tests/regression) that are distributed with ngspice. After various short syntax checks and functional tests we use the QA (quality assurance) simulation approach to verify the correctness of the BSIM3, BSIM4, HiSIM, and HICUM model implementations. As this check may require a large amount of CPU time, there is a configure option `--enable-shortcheck` available, which focuses the check upon BSIM3 and BSIM4.

 All text is available under the terms of the GNU Free Documentation License ![](../images/spice.jpg)
