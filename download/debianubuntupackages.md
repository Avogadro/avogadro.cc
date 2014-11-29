---
layout: default
title: DebianUbuntuPackages
---

# DebianUbuntuPackages

### Debian

Debian users can install Avogadro from the [*experimental*](http://wiki.debian.org/DebianExperimental) repository.

### Ubuntu

Ubuntu user's may use the [Debichem repository](https://launchpad.net/~debichem/+archive).

Ubuntu 8.04 (Hardy) users can do this by running these instructions (you will need administrator rights):

    sudo sh -c "echo deb http://ppa.launchpad.net/debichem/ubuntu hardy main > /etc/apt/sources.list.d/debichem.list"

Then:

    sudo apt-get update
    sudo apt-get install avogadro

**Note:** Ubuntu 7.10 (Gutsy) packages are available for Avogadro 0.8.0 from the Debichem repository but aren't being updated to newer versions of Avogadro.

