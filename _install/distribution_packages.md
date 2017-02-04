---
layout: single
category: Install
title: Distribution Packages
---

Debian
------

Debian users can install Avogadro from the [*testing*](http://packages.debian.org/testing/avogadro), [*unstable*](http://packages.debian.org/sid/avogadro), or [*experimental*](http://wiki.debian.org/DebianExperimental) repositories.

Ubuntu
------

Starting with Ubuntu 8.10, Avogadro is included in the regular Ubuntu archives so check there first. However, the latest Avogadro release may not be available so the Debichem project has also provided the repositories below.

### 9.04 (Jaunty)

Ubuntu 9.04 (Jaunty) users may use the [Debichem repository](https://launchpad.net/~debichem/+archive) to get the latest version of Avogadro by running these instructions (you will need administrator rights):

    sudo sh -c "echo deb http://ppa.launchpad.net/debichem/ubuntu jaunty main > /etc/apt/sources.list.d/debichem.list"

### 8.10 (Intrepid)

Ubuntu 8.10 (Intrepid) users may use the [Debichem repository](https://launchpad.net/~debichem/+archive) to get the latest version of Avogadro by running these instructions (you will need administrator rights):

    sudo sh -c "echo deb http://ppa.launchpad.net/debichem/ubuntu intrepid main > /etc/apt/sources.list.d/debichem.list"

### 8.04 (Hardy)

Ubuntu 8.04 (Hardy) users may use the [Debichem repository](https://launchpad.net/~debichem/+archive) by running these instructions (you will need administrator rights):

    sudo sh -c "echo deb http://ppa.launchpad.net/debichem/ubuntu hardy main > /etc/apt/sources.list.d/debichem.list"

Then:

    sudo apt-get update
    sudo apt-get install avogadro

Note: The packages in the Debichem repository are signed for your security. If you get authentication errors when installing Avogadro please read the instructions on the [Debichem PPA page](https://launchpad.net/~debichem/+archive/ppa) and [Launchpad PPA documentation](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories).

Gentoo
------

Gentoo users can emerge Avogadro with:

    emerge avogadro

Fedora
------

Avogadro packages are available for Fedora 8, 9, 10 and Fedora devel. Visit the [Fedora Package Database](https://admin.fedoraproject.org/pkgdb/packages/name/avogadro) for more information.

FreeBSD
-------

There is a [port](http://www.FreeBSD.org/cgi/ports.cgi?query=avogadro&stype=all) available for FreeBSD.

OpenSUSE
--------

### 11.1

-   **Stable**

Stable packages can be found here:

[`http://download.opensuse.org/repositories/Education/openSUSE_11.1`](http://download.opensuse.org/repositories/Education/openSUSE_11.1)

-   **Unstable**

You can also find useful unstable builds, based on SVN snapshot, although there aren't any guarantees about their stability and even runnability.

[`http://download.opensuse.org/repositories/home:/MadCAD/openSUSE_11.1`](http://download.opensuse.org/repositories/home:/MadCAD/openSUSE_11.1)

### 11.0

-   **Stable**

Stable packages can be found here:

[`http://download.opensuse.org/repositories/Education/openSUSE_11.0`](http://download.opensuse.org/repositories/Education/openSUSE_11.0)

-   **Unstable**

You can also find useful unstable builds, based on SVN snapshot, although there aren't any guarantees about their stability and even runnability.

[`http://download.opensuse.org/repositories/home:/MadCAD/openSUSE_11.0`](http://download.opensuse.org/repositories/home:/MadCAD/openSUSE_11.0)

### 10.3

-   **Stable**

OpenSUSE 10.3 users will find the latest Avogadro packages in the **Packman Repository**.

Add one of [these mirrors](http://en.opensuse.org/Additional_YaST_Package_Repositories#Packman) to your list. Manual download available here: <http://packman.links2linux.de/package/avogadro>

-   **Unstable**

You can also find useful unstable builds, based on SVN snapshot, although there aren't any guarantees about their stability and even runnability.

[`http://download.opensuse.org/repositories/home:/MadCAD/openSUSE_10.3`](http://download.opensuse.org/repositories/home:/MadCAD/openSUSE_10.3)

ArchLinux
---------

There is a [PKGBUILD](http://aur.archlinux.org/packages.php?ID=13512|contributed) available in the ArchLinux User-community Repository (AUR).

Mandriva
--------

All these packages are made by the [MandrivaClub.NL](http://www.mandrivaclub.nl) project, and thus are completely unofficial. All packages are available as 32 and 64 bit. Commands listed should be done with root rights. After adding the sources, refresh your package list with

`urpmi.update -a`

Now you can install the package *avogadro*.

### 2008.1

These packages require Qt 4.4 from (in this example) [Mandriva Italia backports](http://mib.pianetalinux.org/).

-   **32 bit**

`urpmi.addmedia --update MIB_i686_progs `[`http://mib.pianetalinux.org/2008.1/i686/progs`](http://mib.pianetalinux.org/2008.1/i686/progs)` with media_info/synthesis.hdlist.cz`
`urpmi.addmedia --update MandrivaClub.NL `[`ftp://ftp.surfnet.nl/pub/os/Linux/distr/mandrakeclubnl/2008.1/i586/release`](ftp://ftp.surfnet.nl/pub/os/Linux/distr/mandrakeclubnl/2008.1/i586/release)` with hdlist.cz`

-   **64 bit**

`urpmi.addmedia --update MIB_x86_64_progs `[`http://mib.pianetalinux.org/2008.1/x86_64/progs`](http://mib.pianetalinux.org/2008.1/x86_64/progs)` with media_info/synthesis.hdlist.cz`
`urpmi.addmedia --update MandrivaClub.NL `[`ftp://ftp.surfnet.nl/pub/os/Linux/distr/mandrakeclubnl/2008.1/x86_64/release`](ftp://ftp.surfnet.nl/pub/os/Linux/distr/mandrakeclubnl/2008.1/x86_64/release)` with hdlist.cz`

### 2009.0

-   **32 bit**

`urpmi.addmedia --update MandrivaClub.NL `[`ftp://ftp.surfnet.nl/pub/os/Linux/distr/mandrakeclubnl/2009.0/i586/release`](ftp://ftp.surfnet.nl/pub/os/Linux/distr/mandrakeclubnl/2009.0/i586/release)` with media_info/hdlist.cz`

-   **64 bit**

`urpmi.addmedia --update MandrivaClub.NL `[`ftp://ftp.surfnet.nl/pub/os/Linux/distr/mandrakeclubnl/2009.0/x86_64/release`](ftp://ftp.surfnet.nl/pub/os/Linux/distr/mandrakeclubnl/2009.0/x86_64/release)` with media_info/hdlist.cz`

### 2009.1

-   **32 bit**

`urpmi.addmedia --update MandrivaClub.NL `[`ftp://ftp.surfnet.nl/pub/os/Linux/distr/mandrakeclubnl/2009.1/i586/release`](ftp://ftp.surfnet.nl/pub/os/Linux/distr/mandrakeclubnl/2009.1/i586/release)` with media_info/hdlist.cz`

-   **64 bit**

`urpmi.addmedia --update MandrivaClub.NL `[`ftp://ftp.surfnet.nl/pub/os/Linux/distr/mandrakeclubnl/2009.1/x86_64/release`](ftp://ftp.surfnet.nl/pub/os/Linux/distr/mandrakeclubnl/2009.1/x86_64/release)` with media_info/hdlist.cz`

### 2010.0

-   **32 bit**

`urpmi.addmedia --update MandrivaClub.NL `[`ftp://ftp.surfnet.nl/pub/os/Linux/distr/mandrakeclubnl/2010.0/i586/release/`](ftp://ftp.surfnet.nl/pub/os/Linux/distr/mandrakeclubnl/2010.0/i586/release/)` with media_info/hdlist.cz`

-   **64 bit**

`urpmi.addmedia --update MandrivaClub.NL `[`ftp://ftp.surfnet.nl/pub/os/Linux/distr/mandrakeclubnl/2010.0/x86_64/release/`](ftp://ftp.surfnet.nl/pub/os/Linux/distr/mandrakeclubnl/2010.0/x86_64/release/)` with media_info/hdlist.cz`

