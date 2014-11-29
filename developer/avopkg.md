---
layout: default
title: Avopkg
---

# Avopkg

Avopkg is a minimalistic package manager designed for easy distribution of Avogadro plugins. It's written in POSIX shell and requires only standard \*nix tools like `basename`, `cat`, `grep`, `awk`, so it should run on any POSIX-compliant OS, including Linux, \*BSD, Mac OS X, or POSIX subsystem like Cygwin or Windows SFU.

Avopkg is preprocessed in time of compilation and contains installation path of Avogadro, OpenBabel, and some information about target system.

You can get brief information about Avopkg usage by running `avopkg` without arguments. Also, manpage for avopkg is available.

Installation of Avopkg packages
-------------------------------

To install Avogadro plugin, packaged with Avopkg (typically has ".avo" extension), run

    avopkg [-f] filename

Avopkg will check if plugin is native or Python.

-   If it's Python plugin, Avopkg will check whether Avogadro was compiled with Python support. If not, installation fails.
-   If it's native library, Avopkg will check OS and CPU architecture, failing on mismatch. However, you can force installation using `-f` key (e.g., it's possible to run Linux plugin on FreeBSD).

You can add file association for ".avo" files to install package by clicking it in your favourite file manager. Probably it will require creation of new MIME type.

Building Avopkg packages
------------------------

In order to build package for your Avogadro plugin, you'll need to prepare manifest file. The next instructions assume that current directory in shell is a directory, containing all necessary plugin files (compiled libraries/python scripts, documentation snd so on).

### Wizard mode

Run

    avopkg -wizard

You'll be asked some questions about your extension, and answers will be written to manifest file (your\_package\_name.mf). If this file already exists, you'll be asked if you want it to be overwritten.

Wizard is smart enough to propose you some "default" answers in [ ] - you can choose them by hitting Enter with empty input. Finally, wizard will propose you to build package and then to make test installation. However, in some cases you'll need to modify manifest manually (e.g., to fix list of packaged files)

### How to create/edit manifest manually

Manifest contains the next fields:

-   **Name** - Long name of plugin
-   **Author** - Full name of author
-   **Package** - short unix name of plugin
-   **Files** - space separated list of files (not including manifest)
-   **Category** - one of available plugin categories
-   **Python** - present if plugin is written in Python

Currently, only 'Package' and 'Files' are used by package manager.

Field names are separated from their values with colon(:). Example:

    Name: OpenThermo Extension for Avogadro
    Author: Konstantin Tokarev
    Package: OpenthermoGui
    Files: libopenthermo.so COPYING
    Category: extensions

**Python** field is special - it has not to have any value or colon. But if you accidentally specify something like `Python: yes`, it's fine too, but `Python: no` will not work as you expect.

Additional fields (you might need to specify them if you do cross-compilation):

-   **System** - OS name
-   **SizeofVoidP** - 4 for 32-bit, 8 for 64-bit, etc.

Default values for them are taken from Avopkg configuration on "pack" stage, but if you specify (one of) these fields explicitly, it will not be overridden.

### Pack mode

Run

    avopkg -pack manifest

Practically, manifest can have any name, not necessarily your\_package\_name.mf. But using another name will break integration with build system (see later). You'll get ready to use package in current directory.

### Build system integration

Avopkg is integrated with CMake and QMake build systems for Avogadro packages. In both cases, you'll have three additional make targets: `manifest`, `package`, `install`. `make manifest` is equivalent to avopkg -wizard package\_name.

Avopkg in other applications
----------------------------

Being tuned for Avogadro needs, Avopkg can serve as generic plugin manager for other applications. Actually, it's generic minimalistic package management system without handling of package interdependencies. For example, it could be used to install plugin JARs/classes for Java applications.

Such things as default extensions for manifests and packages, or compression command could be easily changed. The only thing that will require some work is changing of installation paths. If you want to make Avopkg more generic and usable for your application, feel free to contribute.

<Category:User> <Category:Developer>

