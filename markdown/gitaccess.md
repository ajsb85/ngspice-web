![NGSPICE](./images/nglogo.jpg) ![Mixed mode - mixed level circuit simulator - based on Berkeley's Spice3f5](./images/ngtext2.jpg) [](https://sourceforge.net/projects/ngspice)

-   [Home](./index.html)
-   [Screenshots](./screens.html)
-   [Download](./download.html)
-   [Documentation](./docs.html)
-   [Extras/Options](./extras.html)
-   [Applications](./applic.html)
-   Development
-   [Simulation Environments](./resources.html)
-   [Quality](./quality.html)
-   [Contributions](./contrib.html)

Ngspice Development

-   [Developers Info](./devel.html)

-   [Bug Reports](./bugrep.html)

-   Git Access

-   [Docs for developers](./devdocs.html)

-   [Mailing List Archives](./mlarch.html)

-   [Releases Info](./relinfo.html)

-   [Roadmap](./roadmap.html)

-   [Writing Docs](./docwrite.html)

-   

    ------------------------------------------------------------------------

-   [Tests](./applic.html#test)

OSDI/OpenVAF for ngspice

-   [What ADMS is ?](./osdi.html)

GSS-TCAD

-   [GSS](./gss.html)

TCLspice

-   [What TCLspice is ?](./tclspice.html)
-   [TCLspice users manual](./tclusers.html)
-   [TCLspice by examples](./tclexamples.html)
-   [Designer's note](./tclnotes.html)

Ngspice Git access

Ngspice source code is stored in a public (anonymous) accessible Git Source Code Management (SCM) tool maintained by [Sourceforge](https://sourceforge.net/p/ngspice/_list/git).

Setting up the environment for Git on your computer:

On Linux you may install Git using the distribution's repository manager (rpm, apt, etc.). On macOS Git is available via Homebrew or Apple Xcode. For MS Windows there you will find this [Git download page](https://git-scm.com/download/win).

After Git installation you may use Git with the commands given below in the usual terminal window. On MS Windows you may open a Git Bash window by right-clicking in the Explorer window onto any directory of your choice and choosing 'Git Bash here'.

To learn more about Git, which is both powerful and difficult to master, please consult [**http://git-scm.com/**](http://git-scm.com/), especially: [**http://git-scm.com/documentation**](http://git-scm.com/documentation) which has pointers to documentation and tutorials.

Retrieving ngspice code:

Create or select a directory of your choice, e.g. 'Software'. Cd into this directory. To retrieve ngspice code you have to issue the command:

git clone git://git.code.sf.net/p/ngspice/ngspice ngspice\_test

The code will be downloaded and made available in the directory Software/ngspice\_test. The command above is used to retrieve the current master branch tree, and installs a complete local repository onto your system.

If a firewall is blocking git:// access, there is an alternative to clone via https://:

git clone https://git.code.sf.net/p/ngspice/ngspice ngspice\_test

To fetch and incorporate new commits from Sourceforge into your local git repository, please cd to directory ngspice\_test and run

git pull

git pull will deny to overwrite modified files in your working directory. To drop your local changes first, you can run

git reset --hard

Be careful because this command may delete your local changes!

To switch to another branch, you may issue

git fetch

and then

git checkout pre-master

Pre-master is the current development branch. Other ngspice Git branches are available as well, see this [list of ngspice Git branches](https://sourceforge.net/p/ngspice/ngspice/ref/master/branches/).

Accessing ngspice Git repositories via the Sourceforge web interface

Though Git repositories are most commonly accessed using a Git client, Sourceforge.net also provide a web-based interface to view Git repositories. Browsing the Git tree gives you a great view into the current status of this project's code. You may also view the complete histories of any file in the repository.

-   [Ngspice Git repository](https://sourceforge.net/p/ngspice/ngspice/ci/master/tree/)

ngspice or ngspice-manuals may be selected. If you choose ngspice, then the master branch becomes visible. On the left you will find buttons to select any of the other development branches. On the top right you may download as a snapshot the complete tarball of the selected branch.

[](http://sourceforge.net) All text is available under the terms of the GNU Free Documentation License ![](./images/spice.jpg)
