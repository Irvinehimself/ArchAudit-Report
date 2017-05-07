# ArchAudit-Report v1.00
**License:** GPLv3

**Dependencies:**
* arch-audit (community)
* whoneeds (pkgtools AUR  https://aur.archlinux.org/packages/pkgtools/)

### What is it?
Okay, being honest,  this utility is more informative than practical. However, **it is very informative!**

As you may know, ‘arch-audit’, is a tool which tells you which packages installed on your system have been issued security advisories, (see https://security.archlinux.org/). Unfortunately, the formatting of the arch-audit output is designed to facilitate piping to other auditing tools, for example Lynis. For a human, this raw output is neither informative, nor particularly readable.

Written in bash, ‘archaudit-report’ parses the raw output from ‘arch-audit’ into a formatted, easy to read top down look at how the underlying advisories affect your applications.

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
	
**Note1:**
This utility is meant to give an overview of which applications are affected by Arch Linux security advisories. It is not meant to be a measure of how secure a system is. To measure the overall level of system hardness, use Lynis or some other security auditing tool.

**Note2:**
It is important to realise that trying to switch  between packages in the hope of eliminating vulnerabilities is a fools errand. All it will achieve is a really bad migraine! 

What you should really be paying attention to is: **“How quickly are they fixed?”**  and **“In the wild, how many exploits have been attributed to a particular advisory?”**  Unlike in Windows, in Linux the answers to these questions are usually very reassuring.

*For an interesting take on Linux advisories and how it has gone wrong with WebKitGTK2, see this blog post by Gnome developer Michael Catanzaro: https://blogs.gnome.org/mcatanzaro/2016/02/01/on-webkit-security-updates/*

<br><br>
# Installation:
Once I get some feedback, I will put it in the AUR. Until then, installation is a matter of personal choice. This post on the Arch forums discusses various installation options for bash shells: https://bbs.archlinux.org/viewtopic.php?id=165042

You should note that the choice of installation directory may be limited by your security model. For example, without fiddling, neither Grsecurity, nor Firejail with Apparmor enabled allow you to run executables from your home directory.
 
With the above caveat in mind, (apart from just dropping the file into a terminal,) the easiest installation method is to copy, (as root,) ‘archaudit-report’ into ‘/usr/local/bin/’. Since this is already in  $PATH, nothing further should be needed and simply entering ‘archaudit-report’ into a terminal will generate the report.

**Note:** It is **ABSOLUTELY NOT** necessary to run this shell with sudo!

**Note:** Do not confuse ‘/usr/local/bin/’ with ‘/usr/bin’.

If there is a problem, check that non root users have  permission to run it as an executable, I believe  ‘sudo chmod 755  archaudit-report’ does the trick.

On a final note, when running ‘untrusted’😈 applications, a sandbox is a really good idea.  Firetools-0.9.46  has an excellent wizard which, (literally,)  allows you create a sandbox in seconds. Unfortunately, you will have to compile it yourself, since the AUR Firetools, (at version 0.9.44,) is out of date.

<br><br>
# Screenshots

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
