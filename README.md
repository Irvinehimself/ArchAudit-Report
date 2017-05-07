# ArchAudit-Report
**License:** GPLv3

**Dependencies:**
* arch-audit (community)
* whoneeds (pkgtools AUR  https://aur.archlinux.org/packages/pkgtools/)

<br><br>
**Contents:**
* What is ArchAudit-Report?
...* Features:
* Installation:
* Screenshots:

<br><br>
### What is ArchAudit-Report?
Okay, being honest, this utility is more informative than practical. However, it is very informative!

As you may know, ‘arch-audit’, is a tool which tells you which packages installed on your system have been issued security advisories, (see https://security.archlinux.org/). Unfortunately, the formatting of the arch-audit output is designed to facilitate piping to other auditing tools, (for example Lynis.) For a human, this raw output is neither informative, nor particularly readable.

Written in bash, ‘archaudit-report’ parses the raw output from ‘arch-audit’ and pipes it to 'whoneeds'. Analysing the output from the pipe, it then uses this data to prepare an easy to read, top down look at how the underlying advisories affect your applications.

### Features:
1. Colour coded highlights of the package name and associated risk.
2. A (clickable) link to the specific  package advisory at  https://security.archlinux.org/
3. A three column wide table, listing the applications that use each package.
4. A summary report detailing:
      * The number of advisories affecting your system
      * A breakdown of this count for different risk levels
      * The total number of top level applications affected by the advisories
      * A similar breakdown as above, detailing the number of applications affected at each risk level.
      * A ranked summary of the advisories, sorted by level of risk then number of affected applications
      * A ranked summary of affected applications sorted by risk

**Notes:**
This utility is meant to give an overview of which applications are affected by Arch Linux security advisories. It is not meant to be a measure of how secure a system is. To measure the overall level of system hardness, use Lynis or some other security auditing tool.

Generally, trying to switch between applications in the hope of avoiding packages with advisories is a fools errand. All you will achieve is a really bad migraine! Instead of wasting your time, what you should be paying attention to is: *“How quickly is an advisory fixed?”*  and *“In the wild, how many exploits have been attributed to a particular advisory?”*  Unlike in Windows, in Linux the answers to these questions is usually very reassuring.

*For an interesting take on Linux advisories and how it has gone wrong with WebKitGTK2, see this blog post by Gnome developer Michael Catanzaro: https://blogs.gnome.org/mcatanzaro/2016/02/01/on-webkit-security-updates/*

<br><br>
# Installation:
Once I get some feedback, I will put it in the AUR. Until then, installation is a matter of personal choice. This post on the Arch forums discusses various installation options for bash shells: https://bbs.archlinux.org/viewtopic.php?id=165042

Primarily, the most important consideration is to check that the file "archaudit-report" has permission to run as an executable. I believe 'chmod 755  archaudit-report’ does the trick, (alternatively you can use your file-manager GUI 😅)

If your security model permits it, for testing, you can just drop the file into a terminal. For a full installation, (necessary to run ‘archaudit-report’ directly from the command line,) the easiest method is to copy, (as root,) ‘archaudit-report’ into ‘/usr/local/bin/’. Since this directory is already in  $PATH, nothing further should be needed.

Note, it is **ABSOLUTELY NOT** necessary to run this shell with sudo!

Similarly, do not confuse ‘/usr/local/bin/’ with ‘/usr/bin’.

On a final note, when running ‘untrusted’😈 applications, a sandbox is a really good idea.  Firetools-0.9.46  has an excellent wizard which, (literally,)  allows you create a sandbox in seconds. Unfortunately, you will have to compile it yourself, since the AUR Firetools, (at version 0.9.44,) is out of date.

<br><br>
# Screenshots:

**Applications affected by an advisory:**
![Advisory tables](/screenshots/Advisories.png?raw=true "Advisory Tables")
<br><br>

**Summary overview:**
![Summary overview](/screenshots/Overview.png?raw=true "Summary Overview")
<br><br>

**Ranked list of advisories:**
![Advisory list](/screenshots/AdvisoryList.png?raw=true "Advisory List")
<br><br>

**Ranked list of affected applications:**
![Application list](/screenshots/ApplicationList.png?raw=true "Application List")
