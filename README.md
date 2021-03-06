# ArchAudit-Report
**License:** GPLv3

**Dependencies:**
* arch-audit (community)
* whoneeds (pkgtools AUR  https://aur.archlinux.org/packages/pkgtools/)

<br><br>
### Contents:
* What is ArchAudit-Report?
* Features:
* Notes:
* Installation:
* Screenshots:
* Addendum  on sha checksums:
* Release history:

<br><br>
### What is ArchAudit-Report?
While this utility is mainly informative, it presents that information in a way which allows the user to target vulnerable "top-level" applications for additional security. For example, sand-boxing with [Firejail](https://github.com/netblue30/firejail).

More precisely, [arch-audit](https://github.com/ilpianista/arch-audit), is a tool which tells you which packages installed on your system have been issued [security advisories](https://security.archlinux.org/). Unfortunately, the formatting of the arch-audit output is designed to facilitate piping to other auditing tools, (for example Lynis.) For a human, this raw output is neither informative, nor particularly readable.

Written in bash, ‘archaudit-report’ parses the raw output from ‘arch-audit’ and pipes it to 'whoneeds'. Analysing the output from the pipe, it then uses this data to prepare an easy to read, top down look at how the underlying advisories affect your applications.

<br><br>
### Features:
1. Colour coded highlights of the package name and associated risk.
2. A (clickable) link to the specific  package advisory at  https://security.archlinux.org/
3. Notification of any updates that fix a vulnerability.
4. A three column wide table, listing the applications that use each package.
5. A summary report detailing:
      * The number of advisories affecting your system
      * A breakdown of this count for different risk levels
      * The total number of top level applications affected by the advisories
      * A similar breakdown as above, detailing the number of applications affected at each risk level.
      * A ranked summary of the advisories, sorted by level of risk then number of affected applications
      * A ranked summary of affected applications sorted by risk

<br><br>
### Notes:
This utility is meant to give an overview of which applications are affected by Arch Linux security advisories. It is not meant to be a measure of how secure a system is. To measure the overall level of system hardness, use Lynis or some other security auditing tool.

Generally, trying to switch between applications in the hope of avoiding packages with advisories is a fools errand. All you will achieve is a really bad migraine! Instead of wasting your time, what you should be paying attention to is: *“How quickly is an advisory fixed?”*  and *“In the wild, how many exploits have been attributed to a particular advisory?”*  Unlike in Windows, in Linux the answers to these questions is usually very reassuring.

*For an interesting take on Linux advisories and how it has gone wrong with WebKitGTK2, see [this](https://blogs.gnome.org/mcatanzaro/2016/02/01/on-webkit-security-updates/) blog post by Gnome developer Michael Catanzaro.*

<br><br>
### Installation:

**Update:** ArchAudit-Report is now available from the [AUR](https://aur.archlinux.org/packages/archaudit-report/)

If you don't wish to use my PCKGBUILD, then [this](https://bbs.archlinux.org/viewtopic.php?id=165042) post on the Arch forums discusses various installation options for bash shells.

Primarily, the most important consideration is to check that the file "archaudit-report" has permission to run as an executable. I believe 'chmod 755  archaudit-report’ does the trick, (alternatively you can use your file-manager GUI 😅)

Secondly, git repos are generally works in progress and may be unstable. Usually, it is best practice to downoad the latest stable release. (See Release History, below, for direct links and sha256 checksums).

If your security model permits it, for testing, you can just drop the file into a terminal. For a full installation, (necessary to run ‘archaudit-report’ directly from the command line,) the easiest method is to copy, (as root,) ‘archaudit-report’ into ‘/usr/local/bin/’. Since this directory is already in  $PATH, nothing further should be needed.

Note, it is **ABSOLUTELY NOT** necessary to run this shell with sudo!

Similarly, do not confuse ‘/usr/local/bin/’ with ‘/usr/bin’.

On a final note, when running ‘untrusted’😈 applications, a sandbox is a really good idea.  Firetools-0.9.46  has an excellent wizard which, (literally,)  allows you create a sandbox in seconds. Unfortunately,(at the time of writing,) you will have to compile it yourself, since the AUR Firetools, (at version 0.9.44,) was out of date.

<br><br>
### Screenshots:

**Applications affected by an advisory:**
![Advisory tables](/screenshots/Advisories.png?raw=true "Create git repo Advisory Tables")
<br><br>

**Summary overview:**
![Summary overview](/screenshots/Overview.png?raw=true "Summary Overview")
<br><br>

**Ranked list of advisories:**
![Advisory list](/screenshots/AdvisoryList.png?raw=true "Advisory List")
<br><br>

**Ranked list of affected applications:**
![Application list](/screenshots/ApplicationList.png?raw=true "Application List")
<br><br>

### Addendum  on sha checksums for GitHub packages:
Okay,not really relvant to ArchAudit-Report, but, while writing the PKGBUILD for the AUR, I really struggled figuring out how to get the "sha256sum" for the release tarball. From my Google searches, I am not alone with this problem. I found many request for developers to provide sha-checksums, but no details on how to do it.

For reference, here is how you provide a checksum:
1. Prepare the release as normal.
2. Download and verify the tarball
3. In terminal, enter 'sha256sum < PathToTarball' (or sha1sum, or whatever.)
4. Copy/Paste result to README.md, (or wherever.)

<br><br>
### Release History:
1. **ArchAudit-Report [v1.05](https://github.com/Irvinehimself/ArchAudit-Report/archive/1.05.tar.gz):**
    * Minor bug fix to "Updated to  new arch-audit format"
    * Tarball sha256 = **90c80802e0a21d4f948348433e43895863e513f568719ee8cdb81059e425322d**
1. **ArchAudit-Report [v1.04](https://github.com/Irvinehimself/ArchAudit-Report/archive/v1.04.tar.gz):**
    * Minor bug fix to "About: version"
    * Tarball sha256 = **710e86f6421268c84c6c40101d21317addbbeead7aa237a599f688f8a3e09a43**
1. **ArchAudit-Report [v1.03](https://github.com/Irvinehimself/ArchAudit-Report/archive/v1.03.tar.gz):**
    * Minor bug fix to how the pckgrisk advisory is parsed
    * Tarball sha256 = **2551816854ae2215bbdac03d0ac07a34fdd2de409acc2528977999a93c42f154**
1. **ArchAudit-Report [v1.02](https://github.com/Irvinehimself/ArchAudit-Report/archive/v1.02.tar.gz):**
    * Some minor cosmetic improvements. But, most importantly, it adds "About: Version" to the infobox.
    * Tarball sha256 = **99dbd9ecbed70ab806f0c228e3f3c4968fdd9941cc0faac4209c9959c16ade21**
1. **ArchAudit-Report [v1.01](https://github.com/Irvinehimself/ArchAudit-Report/archive/v1.01.tar.gz):**
    * Minor bug fix to UpdateFlag
    * Tarball sha256 = **3d78f9f92ee296e5cda42bbde096f9c394bc18a91fbd9446dc726d4b0c80574b**
1. **ArchAudit-Report [v1.0](https://github.com/Irvinehimself/ArchAudit-Report/archive/v1.0.tar.gz):**
    * First public release
    * Tarball sha256 = **fd4559b866f73dd3ae6fb3f7e2a6bd36b3f14150fbd16e8af24c896fb5c4402c**

